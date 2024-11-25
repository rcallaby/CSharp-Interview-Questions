# Question 24 - Design Patterns

## Can you develop a program using design patterns that implements AES Encryption/Decryption?

We will use the **Strategy Pattern** to separate encryption and decryption strategies and the **Singleton Pattern** to manage the cryptographic provider.

### Design Overview:
1. **Strategy Pattern**: To separate the encryption and decryption algorithms. This will allow easy switching between different encryption strategies if needed in the future.
2. **Singleton Pattern**: To ensure that the cryptographic provider (AES in this case) is used in a thread-safe and consistent way.

### AES Encryption/Decryption Program in C#:

```csharp
using System;
using System.IO;
using System.Security.Cryptography;
using System.Text;

public class AESFactory
{
    // Singleton for AES provider
    private static readonly AESFactory _instance = new AESFactory();
    private AesCryptoServiceProvider _aesProvider;

    private AESFactory()
    {
        // Initialize AES provider
        _aesProvider = new AesCryptoServiceProvider();
    }

    public static AESFactory Instance => _instance;

    public AesCryptoServiceProvider GetAESProvider()
    {
        return _aesProvider;
    }
}

public interface IEncryptionStrategy
{
    byte[] Encrypt(string plainText, byte[] key, byte[] iv);
    string Decrypt(byte[] cipherText, byte[] key, byte[] iv);
}

public class AESEncryption : IEncryptionStrategy
{
    public byte[] Encrypt(string plainText, byte[] key, byte[] iv)
    {
        using (AesCryptoServiceProvider aes = AESFactory.Instance.GetAESProvider())
        {
            aes.Key = key;
            aes.IV = iv;
            aes.Mode = CipherMode.CBC;
            aes.Padding = PaddingMode.PKCS7;

            ICryptoTransform encryptor = aes.CreateEncryptor(aes.Key, aes.IV);
            using (MemoryStream ms = new MemoryStream())
            {
                using (CryptoStream cs = new CryptoStream(ms, encryptor, CryptoStreamMode.Write))
                {
                    using (StreamWriter writer = new StreamWriter(cs))
                    {
                        writer.Write(plainText);
                    }
                }
                return ms.ToArray();
            }
        }
    }

    public string Decrypt(byte[] cipherText, byte[] key, byte[] iv)
    {
        using (AesCryptoServiceProvider aes = AESFactory.Instance.GetAESProvider())
        {
            aes.Key = key;
            aes.IV = iv;
            aes.Mode = CipherMode.CBC;
            aes.Padding = PaddingMode.PKCS7;

            ICryptoTransform decryptor = aes.CreateDecryptor(aes.Key, aes.IV);
            using (MemoryStream ms = new MemoryStream(cipherText))
            {
                using (CryptoStream cs = new CryptoStream(ms, decryptor, CryptoStreamMode.Read))
                {
                    using (StreamReader reader = new StreamReader(cs))
                    {
                        return reader.ReadToEnd();
                    }
                }
            }
        }
    }
}

public class AESContext
{
    private IEncryptionStrategy _strategy;

    public AESContext(IEncryptionStrategy strategy)
    {
        _strategy = strategy;
    }

    public void SetStrategy(IEncryptionStrategy strategy)
    {
        _strategy = strategy;
    }

    public byte[] Encrypt(string plainText, byte[] key, byte[] iv)
    {
        return _strategy.Encrypt(plainText, key, iv);
    }

    public string Decrypt(byte[] cipherText, byte[] key, byte[] iv)
    {
        return _strategy.Decrypt(cipherText, key, iv);
    }
}

class Program
{
    static void Main()
    {
        // Example usage
        string plainText = "This is a secret message!";
        byte[] key = Encoding.UTF8.GetBytes("1234567890123456"); // 16-byte key for AES-128
        byte[] iv = Encoding.UTF8.GetBytes("1234567890123456");  // 16-byte IV for AES CBC mode

        // Set encryption strategy
        AESContext context = new AESContext(new AESEncryption());

        // Encrypt
        byte[] encrypted = context.Encrypt(plainText, key, iv);
        Console.WriteLine("Encrypted (Base64): " + Convert.ToBase64String(encrypted));

        // Decrypt
        string decrypted = context.Decrypt(encrypted, key, iv);
        Console.WriteLine("Decrypted: " + decrypted);
    }
}
```

### Explanation:

1. **AESFactory (Singleton Pattern)**: 
   - The `AESFactory` class ensures that there is only one instance of the `AesCryptoServiceProvider` (AES provider) in the application, preventing repeated initialization and ensuring that the provider is used consistently.
   - The instance of the AES provider is accessible through the `AESFactory.Instance` property.

2. **IEncryptionStrategy Interface**:
   - The `IEncryptionStrategy` interface defines the contract for the encryption and decryption methods.
   - This allows easy switching between different encryption strategies if you decide to implement another encryption algorithm in the future.

3. **AESEncryption (Strategy Pattern)**:
   - The `AESEncryption` class implements the `IEncryptionStrategy` interface, defining the encryption and decryption logic using AES.
   - It uses AES in CBC (Cipher Block Chaining) mode and applies PKCS7 padding.

4. **AESContext**:
   - This class acts as a context that uses the strategy to encrypt or decrypt data. The context allows changing the encryption strategy at runtime, making it flexible and extensible.

5. **Main Method**:
   - The `Main` method demonstrates how to use the `AESContext` to encrypt and decrypt a simple message using AES. The encrypted message is printed in Base64 format.

### Benefits of Design Patterns:
- **Strategy Pattern**: Encapsulates encryption and decryption strategies, making it easy to swap out AES for another algorithm (like RSA or DES) if required.
- **Singleton Pattern**: Ensures the cryptographic provider is created only once, optimizing resource usage.

This program provides a solid foundation for AES encryption and decryption while utilizing design patterns to promote extensibility and maintainability.