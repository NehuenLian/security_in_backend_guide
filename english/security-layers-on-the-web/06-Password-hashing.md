## 6. Password Hashing

When we register on a site and enter our password, it must be stored securely in the database to protect it against possible theft or leaks.

### How is the password protected?

When creating an account, your data is inserted into the database. Then, your password is **hashed** and changes from the original text to a string of characters that represent the password, but not the original text.

We don’t need to recover the original password, and this is intentional.

### How is the password verified?

When we log in with our password, the server hashes it again and compares it with the hash stored in the database. If they match, the password is correct because the same input always produces the same output.

### Algorithms for hashing passwords

Not all algorithms are recommended for protecting passwords. For example, algorithms like **SHA256** or **MD5** are not suitable because they are too fast, allowing attackers to try millions of combinations per second (brute-force attacks).

For password hashing, algorithms designed for this purpose are recommended, such as:

- **bcrypt**  
- **argon2**

### Why are these algorithms recommended?

Because they consume more resources and are slower, which makes brute-force attacks harder. They also allow adjusting CPU and memory usage.

### Use of SALT

These algorithms can add a **SALT**, an extra layer of security.

- A **SALT** is a random value added to the password before hashing.  
- It ensures that two identical passwords produce different hashes.  
- It prevents attacks like *rainbow tables*.

### Example

If we take the password:

```
password123
```

And add a SALT, it could become something like:

```
p@ssw0rd!23
```

Then, we apply the hash (for example with bcrypt) and the result would be something like:

```
$2b$12$N9qo8uLOZMRZo5i.u8rJu5PfF6ylCx7jRy8T/HhXqJvW
```

