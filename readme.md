# risc-v-crypto

This repository solely of this text file, which collects pointers to
Jasmin implementations of secure cryptographic applications that can
be compiled to RISC-V.

## Repositories

- [formosa-mldsa](https://github.com/davidedavoli/formosa-mldsa)
- [formosa-mlkem](https://github.com/davidedavoli/formosa-mlkem)
- [jazzar](https://github.com/davidedavoli/jazzar)

Details about the contents of each repository are provided below:

### formosa-mldsa

The repository [formosa-mldsa](https://github.com/davidedavoli/formosa-mldsa) contains a Jasmin implementation of the ML-DSA digital signature scheme, supporting compilation to RISC-V. 

The following branches are available:

- `feature/constant-time`, containing the constant-time implementation of the scheme.
- `feature/slh`, containing the *speculative* constant-time implementation protected with Jasmin's `protect` instruction (manual SLH protections). 
- `feature/dfence`, containing the *speculative* constant-time implementation protected with the experimental `dfence` primitive. 
- `feature/fence`, containing the *speculative* constant-time implementation protected with `fence` instructions. 


### formosa-mlkem

The repository [formosa-mlkem](https://github.com/davidedavoli/formosa-mlkem) contains a Jasmin implementation of the ML-KEM key exchangement mechanism, supporting compilation to RISC-V. 

The repository follows the same branch structure as the previous one.

### jazzar

The repository [jazzar](https://github.com/davidedavoli/jazzar) contains a collection of Jasmin programs based on [this repository](https://gitlab.inria.fr/vlaporte/jazzar). The collection has been ported to RISC-V and extended. 

As of writing, it includes implementations of the following cryptographic applications:

- The Gimli pseudorandom permutation
- The curve X25519
- The keccak permutation, at the basis of SHA-3
- The Poly1305 message authentication code

This repository also follows the same branching conventions as the others.

## Compiling 

The `feature/constant-time` branches can be compiled using any RISC-V compatible Jasmin compiler. To compile other branches, it is necessary to use the [my fork of the Jasmin compiler](https://github.com/davidedavoli/formosa-mldsa).

## Disclaimer

The RISC-V specification of the `fence` instruction does not describe it as a speculation barrier. Therefore, our cryptographich implementation protected with `fence` are only secure on modified hardware where `fence` acts as a specualtion barrier. 
