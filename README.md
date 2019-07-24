<h3 align="center">
  <img src="assets/diffie_hellman_icon_web.png" width="300">
</h3>

# Diffie-Hellman Key Exchange

Swift implementation of classic cryptographic key exchange method.

## About
Diffie-Hellman Key Exchange allow parties to jointly establish a secure private key without sharing it in any way ([Forward secrecy](https://en.wikipedia.org/wiki/Forward_secrecy)) and then use it for a symmetric key cipher. 

## How does it work?

1. Both parties agree on a common component, which consists of two natural numbers p (modulus) and g (base). They can be completely random to make this work, but in order to make the process significantly harder to break, **p should be a prime and g should be primitive root modulo of p**. Check `DHParameters.swift` for more info.
2. Then both parties generate random private keys and then compute public keys which they share with each other. Public keys are computed as follows **publicKey = g^privateKey mod p**
3. Afterward, both parties can compute common secret key using own private key and peer's public key. They can do it using the following formula **secretKey = peerPublicKey^ownPrivateKey mod p** <br><br> Underlying math: <br> **(g^a mod p)^b mod p = g^ab mod p** <br> **(g^b mod p)^a mod p = g^ba mod p**

4. Now both parties can communicate using symmetric cryptography using a jointly established private key.

<br>

<h3 align="center">
  <img src="assets/dh_illustration.png" width="400">
</h3>

## What's so special about it?

This protocol is considered secure (check disclaimer), because it's relatively hard for eavesdroppers to compute a common secret key knowing only public keys if p is big enough.


### Disclaimer
Don't use it in a production environment. Generated keys are very small (Int64) thus making them easily breakable.
Use already generated [RFC primes](https://www.ietf.org/rfc/rfc3526.txt), but even them [may not be strong enough](https://arstechnica.com/information-technology/2015/10/how-the-nsa-can-break-trillions-of-encrypted-web-and-vpn-connections/).

## Author

**Greg (Grzegorz) Surma**

[**PORTFOLIO**](https://gsurma.github.io)

[**GITHUB**](https://github.com/gsurma)

[**BLOG**](https://medium.com/@gsurma)

<a href="https://www.paypal.com/paypalme2/grzegorzsurma115">
  <img alt="Support via PayPal" src="https://cdn.rawgit.com/twolfson/paypal-github-button/1.0.0/dist/button.svg"/>
</a>

