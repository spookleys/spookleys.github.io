---
layout: post
title:  "Encryption intro"
date:   2024-07-05 21:21:21 +1000
tags: [encryption]
---


Dear readers,

## Introduction

Today I have been having a stab again at encryption. Probably like some of you, it is something that I learn a little of, park it, then return to later to take another small bite. Well, below are some notes on the topic.

## Key terms

**Plaintext** - Unencrypted data that you would like to encrypt.

**Ciphertext** - Encrypted plaintext.

**Algorithm/Cipher** - Series of transformations that converts plaintext to ciphertext using the key.

**Key** - Secret, cryptographic key that is used by the Key Expansion routine to generate a set of Round Keys.

**Key Expansion** - Routine used to generate a series of Round Keys from the Cipher Key. 

**Round Key** - Round keys are values derived from the Cipher Key using the Key Expansion routine; they are applied to the State in the Cipher and Inverse Cipher.

**Nonce** - Number used once. Used to add a variation such that the same Plaintext + Key + Algorithm does not produce the same ciphertext. This is important as to prevent replay attacks or allow an attacker to infer Plaintext by looking for repeating patterns in Ciphertext. The only requirement for a nonce is that it is used one.

**IV** - initialization vector. This is like a nonce but must be random.

## Encryption Algorithms

There are two types of encryption algorithms:
- Symmetric
	- Examples: AES, Salsa20, ChaCha20, RC4
	- Use cases: Fast encryption - such as file encryption in ransomware
	- Disadvantages: Sharing the secret is difficult.
- Asymmetric
	- Examples: RSA, Diffie-Hellman, Elliptic Curve Cryptography (ECC)
	- Use cases: It is slow, so smaller files/data
	- Disadvantages: Slower compared to symmetric alternatives

## Stream VS Block Ciphers

The following diagram is a depiction of a stream cipher. The stream cipher:

1. Takes a Key that it passes that to a Key Stream Generator (Algorithm)
2. The Key Stream Generator generates a stream of bits.
3. The key stream is then XOR'd with a stream of Plaintext to create the Ciphertext.

<img src="/images/blog/20240705-streamcipher.png" />

The following diagram from Wikipedia[1] is a depiction of a block cipher that is a SP-network (Substitutions and Permutations). The block cipher:
1. Takes a Key and Plaintext that it passes to the Algorithm.
2. Using Key Expansion, the Key is expanded in to Round Keys.
3. A set number of Rounds are then performed on the Plaintext, where in each round:
	1. Scrambling (such as Substitutions and Permutations) takes place on the Plaintext
	2. The scrambled data is then combined (such as XOR) with the Round Key.

<img src="/assets/images/blog/20240705-blockcipher.png" />

[1] https://en.wikipedia.org/wiki/Block_cipher#/media/File:SubstitutionPermutationNetwork2.png

 
