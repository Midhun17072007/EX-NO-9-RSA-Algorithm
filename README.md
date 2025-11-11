# EX-NO-9-RSA-Algorithm

## AIM:
To Implement RSA Encryption Algorithm in Cryptography

## Algorithm:


Step 1: Design of RSA Algorithm  
The RSA algorithm is based on the mathematical difficulty of factoring the product of two large prime numbers. It involves generating a public and private key pair, where the public key is used for encryption, and the private key is used for decryption.

Step 2: Implementation in Python or C 
This algorithm can be implemented in languages like Python or C by performing large integer calculations for key generation, encryption, and decryption, utilizing libraries for modular arithmetic if necessary.

Step 3: Algorithm Description  
1. Key Generation:
   - Select two large prime numbers \( p \) and \( q \).
   - Calculate \( n = p \times q \), which will be used as the modulus.
   - Compute the totient \( \phi(n) = (p - 1)(q - 1) \).
   - Choose a public exponent \( e \) such that \( e \) is coprime with \( \phi(n) \).
   - Compute the private key \( d \), which is the modular inverse of \( e \) mod \( \phi(n) \).

2. Encryption:
   - Convert the plaintext message \( M \) into a numerical form \( m \) (such that \( 0 \le m < n \)).
   - Compute the ciphertext \( c \) using the formula: \( c = m^e \mod n \).

3. Decryption:
   - Use the private key \( d \) to recover \( m \) from \( c \) using: \( m = c^d \mod n \).
   - Convert \( m \) back into the original message \( M \).

Step 4: Mathematical Representation  
- Encryption: \( E(m) = m^e \mod n \)
- Decryption: \( D(c) = c^d \mod n \)

Step 5: **Security Foundation  
The security of RSA relies on the difficulty of factoring large numbers; thus, choosing sufficiently large prime numbers for \( p \) and \( q \) is crucial for security.

## Program:
```
#include <stdio.h> 
#include <string.h> 
int gcd(int a, int b) { return b ? gcd(b, a % b) : a; } 
int modExp(int base, int exp, int mod) { 
int res = 1; 
while (exp) { 
if (exp & 1) res = (res * base) % mod; 
base = (base * base) % mod; 
exp >>= 1; 
} 
return res; 
} 
int modInv(int a, int m) { 
int m0 = m, x0 = 0, x1 = 1; 
while (a > 1) { 
int q = a / m, t = m; 
m = a % m; a = t; 
t = x0; x0 = x1 - q * x0; x1 = t; 
} 
return x1 < 0 ? x1 + m0 : x1; 
} 
int main() { 
int p = 61, q = 53, n = p * q, phi = (p - 1) * (q - 1), e = 17; 
while (gcd(e, phi) != 1) e++; 
int d = modInv(e, phi); 
char msg[100]; printf("Enter plaintext: "); scanf("%s", msg); 
printf("Encrypted: "); for (int i = 0; msg[i]; i++) printf("%d ", modExp(msg[i], e, n)); 
printf("\nDecrypted: "); for (int i = 0; msg[i]; i++) printf("%c", modExp(modExp(msg[i], e, n), d, n)); 
return 0; 
} 
```
## Output:
<img width="633" height="366" alt="image" src="https://github.com/user-attachments/assets/37a64bbb-e6e2-4fb3-87a8-3036476b6bf0" />



## Result:
 The program is executed successfully.
