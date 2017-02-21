# Authentication

Authentication is the process of confirming the validity of credentials, such as a password. There are [three factors](https://en.wikipedia.org/wiki/Authentication#Factors_and_identity) of authentication, but this resource will focus on the **knowledge factor**. Examples of some elements belonging to the knowledge factor would be:
> Something the user knows (e.g., a password, Partial Password, pass phrase, or   personal identification number (PIN), challenge response (the user must answer a question, or pattern), Security question

Authenticating with a single user component would be referred to as single factor authentication. This is the most basic form of authentication, and **should not be used for personally sensitive transactions.**

Authentication should not be confused with **authorization**, which is the act of granting or rejecting a user access to resources based on specific rules or a policy.


## Encryption

Encryption is the process of using an algorithm to encode data into a series of unreadable data of undetermined length. An algorithm usually uses a pseudo-random encryption key to transform the data. There are two types of encryption:

1. Symmetric Key: the encryption key is used to both decrypt and encrypt the data. This key needs to be in possession of all parties needing access to the encrypted data.

1. Public Key: the encryption key is made public for anyone to use to encrypt messages. However, only the receiving party has access to the key to decrypt the message.

#### Why use encryption?

Encryption is ideal for a situation where data needs to be made secure, but at some point it will then need to be decrypted. This ability to reverse the encrypted data makes it less than ideal for authenticating a user's password. If the private encryption key is exposed or the algorithm that was used to encrypt the password is known, an attacker can then decrypt the password.


## Hashing
- salting
- peppering


### Additional Resources

- [Wikipedia Authentication](https://en.wikipedia.org/wiki/Authentication)
