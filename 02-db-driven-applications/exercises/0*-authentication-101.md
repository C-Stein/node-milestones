# Authentication

Authentication is the process of confirming the validity of credentials, such as a password. There are [three factors](https://en.wikipedia.org/wiki/Authentication#Factors_and_identity) of authentication, but this resource will focus on the **knowledge factor**. Examples of some elements belonging to the knowledge factor would be:
> Something the user knows (e.g., a password, Partial Password, pass phrase, or   personal identification number (PIN), challenge response (the user must answer a question, or pattern), Security question

Authenticating with a single user component would be referred to as single factor authentication. This is the most basic form of authentication, and **should not be used for personally sensitive transactions.**

Authentication should not be confused with **authorization**, which is the act of granting or rejecting a user access to resources based on specific rules or a policy.


## Encryption

Encryption is the process of using an algorithm to encode data (referred to as plain text) into unreadable data (referred to as cipher text) of undetermined length. An algorithm usually uses a self generated, pseudo-random encryption key to transform the data. There are two types of encryption:

1. Symmetric Key: the encryption key is used to both decrypt and encrypt the data. This key needs to be in possession of all parties needing access to the encrypted data.

1. Public Key: the encryption key is made public for anyone to use to encrypt messages. However, only the receiving party has access to the key to decrypt the message.

#### Why use encryption?

Encryption is ideal for a situation where data needs to be made secure, but at some point it will then need to be decrypted. This ability to reverse the encrypted data makes it less than ideal for authenticating a user's password. If the private encryption key is exposed or the algorithm that was used to encrypt the password is known, the password can then be decrypted.


## Hashing

An alternative to encryption would be to use a hash function. A hash function is a mathematical algorithm that can take data of any size (referred to as a message) and convert it into a string of a fixed size (referred to as a hash). Once the data has been hashed, there is no reversal process, unlike encryption. The only way to generate matching hashes is to have matching input messages. Even a small change to the message will generate an extensively different hash.

MD5 is the most widely known hashing function. It produces a 32 digit hexadecimal number. Try running this command in the terminal to hash a string with MD5:

`echo 'hello' | md5  // OUTPUT=> b1946ac92492d2347c6235b4d2611184`

Now try running the same command. Notice how the hash does not change. Try hashing different strings, or change a single letter in `'hello'` and notice the difference.

A common practice is to run the input through the hash function multiple times, which adds more randomness to the generated hash. Try running the following command and compare the hash to the first one:

```
echo 'hello' | md5 | md5 // OUTPUT=> 5db9f475f4cb835f1afccf4bb1a706b7
```




- salting
- peppering


### Additional Resources

- [Wikipedia Authentication](https://en.wikipedia.org/wiki/Authentication)
- [Cryptographic Hash Function](https://en.wikipedia.org/wiki/Cryptographic_hash_function)
