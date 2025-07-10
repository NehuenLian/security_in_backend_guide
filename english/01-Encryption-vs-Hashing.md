## 1. Encryption and Hashing: Differences Between Them

Both encryption and hashing aim to protect data, but with different approaches depending on the nature of the data and the context.

### Encryption

Encryption involves transforming data in plain text into an encoded format, using a key.

To retrieve the original data, it must be decrypted, which also requires a key that was previously defined by the developer.

The main feature that distinguishes encryption from hashing is that it is reversible (the original data can be recovered when it's no longer necessary to hide it or when it needs to be read again). This is done through decryption.

Encryption is used when the information needs to be read or processed again later, such as messages, credit card numbers, medical data, etc.

**Example:**

Let's suppose we use the key `"key"` to encrypt a text. If we want to encrypt the message `"Hello World"`, we apply the algorithm with that key and get an encrypted output, for example:

```
3f1e9a7bc2a3e8c5f67a69e70f3c4c2a
```

To read the original message, we apply the inverse algorithm (decryption) using the same key. That gives us:

```
Hello World
```

### Hashing

Hashing is a one-way method of hiding the real content of data to protect it. This means that, unlike encryption, it is not reversible: the original data cannot be recovered in any way once it has been hashed. There is no key to reverse it—it’s a “one-way trip.”

It transforms the data into a fixed-length string made up of meaningless characters that are determined by the original input.

Hashing is used in cases where recovering the original data is not necessary, such as passwords, or to verify the integrity or legitimacy of data.

**Example:**

If we apply a hashing algorithm to the text `"Hello World"`, we get a value like:

```
d9e3f04a363698763cfc3c3cc50a757e7ce2e6a95b2a31eb3e4f639a2e2e3f28
```

This value is unique to that text, but it’s not possible to return to the original message from it. Hashing is a “one-way trip”: once applied, it cannot be reversed.