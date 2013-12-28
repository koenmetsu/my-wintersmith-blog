<h2>First: an introduction</h2>
Code Contracts is a language-agnostic tool that provides you the power of <a title="Design by Contract" href="http://en.wikipedia.org/wiki/Design_by_contract" target="_blank">Design By Contract</a> development. In short, it enables you to make statements about what your code expects and delivers. It's a great way of telling whether or not your code does what <span style="text-decoration:underline;">you</span> expect it to do.

Actions speak louder than words, so let's bring in an example:<strong> the BankAccount class</strong>.

    public class BankAccount
    {
        public decimal Balance { get; set; }
        public double InterestRate { get; set; }
    
        public void Withdraw(decimal amount)
        {
            Balance -= amount;
        }
    
        public void Deposit(decimal amount)
        {
            Balance += amount;
        }
    
        public void AddInterests()
        {
            var interests = Balance * (decimal)InterestRate;
            Balance += interests;
        }
    }

A real simple class that should speak for itself. It maybe could use some comments, DDD or better logic, but it'll do for this post.
<h2>Adding preconditions</h2>
Preconditions are a way to define what state your application must be in at the start of execution of a called method. They're all about telling what you expect from someone calling your methods.

Let's take the <strong>Withdraw</strong> method: someone withdraws money from their account. We might have the following expectations:
<em><ul>
	<li>If you withdraw money, you should at least have money on your account.</li>
	<li>You have to withdraw some money, which means more than nothing ( else it wouldn't be really withdrawing, would it? ).</li>
	<li>You aren't allowed to withdraw more money than you have.</li>
</ul></em>
All of these expectations can easily be converted to preconditions in Code Contracts, by using the <strong>Contract.Requires</strong> method.

    public void Withdraw(decimal amount)
    {
        Contract.Requires(amount &gt; 0);
        Contract.Requires(Balance &gt; 0);
        Contract.Requires(Balance &gt;= amount);
        Balance -= amount;
    }

The nice stuff is that you're not only defining the state your application must be in, <span style="text-decoration:underline;">you're also </span><span style="text-decoration:underline;">defining behavior here</span>.
<h2>Adding postconditions</h2>
Postconditions define what state your application should be when it leaves the called method. This is the part that's all about <strong>delivering promises</strong> about your code, as well as checking if the method did what you expected it to do.

For the <strong>Withdraw</strong> method:
<em><ul>
	<li>We state that after we withdraw money, the balance  of the bank account won't be negative.</li>
	<li>We also state that after the withdrawal, the balance will be the starting balance ( when we entered the method ) minus the amount we withdrawn.</li>
</ul></em>
Once again, the postconditions are easily converted to contracts. The <strong>Contract.OldValue()</strong> represents the value of a certain field or parameter as they were in the beginning of the method.

    public void Withdraw(decimal amount)
    {
        Contract.Requires(amount &gt; 0);
        Contract.Requires(Balance &gt; 0);
        Contract.Requires(Balance &gt;= amount);
        Contract.Ensures(Balance == Contract.OldValue(Balance) - amount);
        Contract.Ensures(Balance &gt;= 0);
    
        Balance -= amount;
    }

The second statement here seems pretty obvious because of the actual code following the contracts, but a lot of times this code will obviously be quite more complicated.
<h2>Isolating object invariants</h2>
Object invariants are conditions on an object which should be true at all times that object is visible to a client. They express the conditions under which the object is in a "good" state.

As good programmers we try to prevent writing the same code twice, and if we look at the preceded code we notice the balance must always be greater than zero.

<em>For the balance to be in a good state, it must never be zero.</em>

We can isolate this contract by creating a method that contains <strong>Contract.Invariant()</strong> statements, and decorate this method with the <strong>ContractInvariant</strong> attribute.

    [ContractInvariantMethod]
    private void EnsureBalanceIsPositive()
    {
        Contract.Invariant(Balance &gt; 0);
    }

All the invariants will be checked at the end of every public method. So now we added these, we no longer need the preconditions regarding the balance being greater than zero.
<h2>Conclusion</h2>
Although this example uses really simple code, by using Code Contracts we made it exactly clear what this BankAccount can and cannot do.

Your code can become immensely more complicated, new developers can join your project but <strong>by defining the </strong><strong>behavior</strong> of this class by contracts, they will <strong>immediately recognize</strong> what the class does.

Ideally we would define the contracts on an interface or base class, so deriving classes would all share a base behavior, but that's out of scope for this post. =)

For more info on Code Contracts, visit the homepage <a href="http://research.microsoft.com/en-us/projects/contracts/">here</a>.



