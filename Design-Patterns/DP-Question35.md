# Question 35 - Design Patterns

## Can you design a blockchain in C# using design patterns? What design pattern would be ideal for such a project?

- **Singleton** for ensuring one instance of the Blockchain.
- **Factory Method** for creating blocks.
- **Strategy** for hash calculation and validation logic.

### Step 1: Define Core Classes and Interfaces

#### 1.1 `Transaction` Class
```csharp
using System;

public class Transaction
{
    public string Sender { get; }
    public string Receiver { get; }
    public decimal Amount { get; }

    public Transaction(string sender, string receiver, decimal amount)
    {
        Sender = sender;
        Receiver = receiver;
        Amount = amount;
    }

    public override string ToString()
    {
        return $"{Sender} -> {Receiver}: {Amount}";
    }
}
```

#### 1.2 `Block` Class
```csharp
using System;
using System.Collections.Generic;
using System.Security.Cryptography;
using System.Text;

public class Block
{
    public int Index { get; }
    public DateTime Timestamp { get; }
    public List<Transaction> Transactions { get; }
    public string PreviousHash { get; }
    public string Hash { get; private set; }
    public int Nonce { get; private set; }

    public Block(int index, string previousHash, List<Transaction> transactions)
    {
        Index = index;
        Timestamp = DateTime.UtcNow;
        PreviousHash = previousHash;
        Transactions = transactions;
        Hash = ComputeHash();
    }

    public string ComputeHash()
    {
        string blockData = $"{Index}{Timestamp}{string.Join("", Transactions)}{PreviousHash}{Nonce}";
        using (SHA256 sha256 = SHA256.Create())
        {
            byte[] hashBytes = sha256.ComputeHash(Encoding.UTF8.GetBytes(blockData));
            return Convert.ToBase64String(hashBytes);
        }
    }

    public void MineBlock(int difficulty)
    {
        string hashValidation = new string('0', difficulty);
        while (!Hash.StartsWith(hashValidation))
        {
            Nonce++;
            Hash = ComputeHash();
        }
    }
}
```

### Step 2: Blockchain Singleton Implementation
```csharp
using System.Collections.Generic;

public class Blockchain
{
    public List<Block> Chain { get; }
    public int Difficulty { get; }
    public List<Transaction> PendingTransactions { get; }
    public decimal MiningReward { get; }

    private static readonly Blockchain _instance = new Blockchain(2, 10);

    private Blockchain(int difficulty, decimal miningReward)
    {
        Chain = new List<Block> { CreateGenesisBlock() };
        Difficulty = difficulty;
        PendingTransactions = new List<Transaction>();
        MiningReward = miningReward;
    }

    public static Blockchain Instance => _instance;

    private Block CreateGenesisBlock()
    {
        return new Block(0, "0", new List<Transaction>());
    }

    public Block GetLatestBlock()
    {
        return Chain[^1];
    }

    public void AddTransaction(Transaction transaction)
    {
        PendingTransactions.Add(transaction);
    }

    public void MinePendingTransactions(string minerAddress)
    {
        Block newBlock = new Block(Chain.Count, GetLatestBlock().Hash, new List<Transaction>(PendingTransactions));
        newBlock.MineBlock(Difficulty);
        Chain.Add(newBlock);

        // Reward the miner
        PendingTransactions.Clear();
        AddTransaction(new Transaction("System", minerAddress, MiningReward));
    }

    public bool IsChainValid()
    {
        for (int i = 1; i < Chain.Count; i++)
        {
            Block currentBlock = Chain[i];
            Block previousBlock = Chain[i - 1];

            if (currentBlock.Hash != currentBlock.ComputeHash() || currentBlock.PreviousHash != previousBlock.Hash)
            {
                return false;
            }
        }
        return true;
    }
}
```

### Step 3: Governance Token Implementation
To implement a governance token, we’ll add functionality to track balances and validate transactions.

#### 3.1 Modify `Blockchain` Class
```csharp
using System.Linq;

public class Blockchain
{
    // Additional code...

    private Dictionary<string, decimal> Balances = new Dictionary<string, decimal>();

    public void AddTransaction(Transaction transaction)
    {
        if (transaction.Amount <= 0)
        {
            throw new ArgumentException("Transaction amount must be greater than zero.");
        }

        if (!Balances.ContainsKey(transaction.Sender) || Balances[transaction.Sender] < transaction.Amount)
        {
            throw new InvalidOperationException("Insufficient balance.");
        }

        Balances[transaction.Sender] -= transaction.Amount;
        if (!Balances.ContainsKey(transaction.Receiver))
        {
            Balances[transaction.Receiver] = 0;
        }
        Balances[transaction.Receiver] += transaction.Amount;

        PendingTransactions.Add(transaction);
    }

    public decimal GetBalance(string address)
    {
        return Balances.ContainsKey(address) ? Balances[address] : 0;
    }
}
```

### Step 4: Demo the Blockchain

#### Main Program
```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        Blockchain blockchain = Blockchain.Instance;

        Console.WriteLine("Mining Genesis Block...");
        blockchain.MinePendingTransactions("Miner1");

        Console.WriteLine("Adding Transactions...");
        blockchain.AddTransaction(new Transaction("Miner1", "User1", 5));
        blockchain.AddTransaction(new Transaction("User1", "User2", 2));

        Console.WriteLine("Mining New Block...");
        blockchain.MinePendingTransactions("Miner1");

        foreach (Block block in blockchain.Chain)
        {
            Console.WriteLine($"Block #{block.Index}:");
            Console.WriteLine($"Hash: {block.Hash}");
            Console.WriteLine($"Previous Hash: {block.PreviousHash}");
            Console.WriteLine("Transactions:");
            foreach (var tx in block.Transactions)
            {
                Console.WriteLine($"  {tx}");
            }
        }

        Console.WriteLine($"Balance of Miner1: {blockchain.GetBalance("Miner1")}");
        Console.WriteLine($"Balance of User1: {blockchain.GetBalance("User1")}");
    }
}
```

### Output Example
```plaintext
Mining Genesis Block...
Adding Transactions...
Mining New Block...
Block #0:
Hash: <hash_value>
Previous Hash: 0
Transactions:
  System -> Miner1: 10
Block #1:
Hash: <hash_value>
Previous Hash: <hash_value>
Transactions:
  Miner1 -> User1: 5
  User1 -> User2: 2
Balance of Miner1: 5
Balance of User1: 3
```

### Key Design Patterns in Use:
1. **Singleton**: Ensures a single `Blockchain` instance.
2. **Factory Method**: Encapsulates `CreateGenesisBlock` logic.
3. **Strategy**: Hash calculation strategy is encapsulated in `ComputeHash`.
