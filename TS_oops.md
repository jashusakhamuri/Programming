
```
interface bank {
    bank_name: string;
    bank_code: number;
    BankDetails(): void;
}

interface BankAddress {
    bank_branch: string;
    bank_gmail: string;
    BankAddress(): void;
}

class CustomerDetails {
    public cs_name: string;
    public cs_bankName: string;
    private ATMPin: number;

    constructor(cs_name: string, cs_bankName: string, ATMPin: number) {
        this.cs_name = cs_name;
        this.cs_bankName = cs_bankName;
        this.ATMPin = ATMPin;
    }

    public resetATMpin(pin: number): void {
        this.ATMPin = pin;
    }

    public getATMPin(): number {
        return this.ATMPin;
    }
}

// Inheritance + Abstraction
abstract class BankOperation extends CustomerDetails {
    protected cs_balance: number;

    constructor(
        cs_name: string,
        cs_bankName: string,
        ATMPin: number,
        amount: number
    ) {
        super(cs_name, cs_bankName, ATMPin);
        this.cs_balance = amount;
    }

    // Method Overloading
    public deposit(amount: number): number;
    public deposit(amount: number, description: string): number;

    public deposit(
        amount: number,
        description?: string
    ): number {
        this.cs_balance += amount;

        if (description) {
            console.log("Deposit:", description);
        }

        return this.cs_balance;
    }

    // Abstract methods
    public abstract withdraw(amount: number): number;
    public abstract checkBalance(): number;
}

// Inheritance + Interface + Method Overriding
class HDFCBank extends BankOperation implements bank, BankAddress {
    public bank_name: string = "HDFC Bank";
    public bank_code: number = 1001;
    public bank_branch: string = "Delhi";
    public bank_gmail: string = "hdfc@gmail.com";

    public BankDetails(): void {
        console.log("Bank:", this.bank_name);
        console.log("Code:", this.bank_code);
    }

    public BankAddress(): void {
        console.log("Branch:", this.bank_branch);
        console.log("Email:", this.bank_gmail);
    }

    // Method Overriding
    public withdraw(amount: number): number {
        if (this.cs_balance - amount < 1000) {
            console.log("HDFC: Minimum balance of 1000 required");
            return this.cs_balance;
        }

        this.cs_balance -= amount;
        console.log("HDFC: Withdrawal successful");

        return this.cs_balance;
    }

    public checkBalance(): number {
        return this.cs_balance;
    }
}

// Inheritance + Interface + Method Overriding
class SBIBank extends BankOperation implements bank, BankAddress {
    public bank_name: string = "SBI Bank";
    public bank_code: number = 2001;
    public bank_branch: string = "Mumbai";
    public bank_gmail: string = "sbi@gmail.com";

    public BankDetails(): void {
        console.log("Bank:", this.bank_name);
        console.log("Code:", this.bank_code);
    }

    public BankAddress(): void {
        console.log("Branch:", this.bank_branch);
        console.log("Email:", this.bank_gmail);
    }

    // Method Overriding
    public withdraw(amount: number): number {
        if (amount > this.cs_balance) {
            console.log("SBI: Insufficient balance");
            return this.cs_balance;
        }

        this.cs_balance -= amount;
        console.log("SBI: Withdrawal successful");

        return this.cs_balance;
    }

    public checkBalance(): number {
        return this.cs_balance;
    }
}

// Creating objects
const hdfc = new HDFCBank(
    "Rahul",
    "HDFC",
    1234,
    5000
);

const sbi = new SBIBank(
    "Amit",
    "SBI",
    5678,
    5000
);

// Method Overloading
console.log("HDFC Balance:", hdfc.deposit(1000));
console.log("HDFC Balance:", hdfc.deposit(2000, "Salary"));

// Method Overriding
hdfc.withdraw(4500);
sbi.withdraw(4500);

// Polymorphism
const bank1: BankOperation = hdfc;
const bank2: BankOperation = sbi;

bank1.withdraw(500);
bank2.withdraw(500);

// Check Balance
console.log("HDFC Final Balance:", hdfc.checkBalance());
console.log("SBI Final Balance:", sbi.checkBalance());

// Interface methods
hdfc.BankDetails();
hdfc.BankAddress();

sbi.BankDetails();
sbi.BankAddress();

// Encapsulation
hdfc.resetATMpin(9999);

console.log("ATM PIN:", hdfc.getATMPin());
```

 ### Output

```
HDFC Balance: 6000
Deposit: Salary
HDFC Balance: 8000

HDFC: Withdrawal successful
SBI: Withdrawal successful

HDFC: Withdrawal successful
SBI: Withdrawal successful

HDFC Final Balance: 3000
SBI Final Balance: 0

Bank: HDFC Bank
Code: 1001
Branch: Delhi
Email: hdfc@gmail.com

Bank: SBI Bank
Code: 2001
Branch: Mumbai
Email: sbi@gmail.com

ATM PIN: 9999
```

 ### All OOP concepts in this one example

```
Class
 ↓
CustomerDetails, BankOperation, HDFCBank, SBIBank

Encapsulation
 ↓
private ATMPin
protected cs_balance

Inheritance
 ↓
BankOperation extends CustomerDetails
HDFCBank extends BankOperation
SBIBank extends BankOperation

Abstraction
 ↓
abstract class BankOperation
abstract withdraw()
abstract checkBalance()

Interface
 ↓
bank
BankAddress

Method Overloading
 ↓
deposit(amount)
deposit(amount, description)

Method Overriding
 ↓
HDFCBank → withdraw()
SBIBank  → withdraw()

Polymorphism
 ↓
const bank1: BankOperation = hdfc
const bank2: BankOperation = sbi

Constructor
 ↓
constructor(...)

super()
 ↓
BankOperation → CustomerDetails

Access Modifiers
 ↓
public
private
protected
```

 This gives you essentially a **single TypeScript OOP practice program covering the major concepts you've been working through**.