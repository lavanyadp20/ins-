# INS-# Cipher Implementation and Comparative Analysis

## Overview
This repository contains implementations of classical encryption techniques, including the *Playfair Cipher, Hill Cipher, Vigenère Cipher, and a **Hybrid Cipher* combining AES substitution and transposition techniques. Additionally, a comparative analysis of these ciphers is provided, including cryptanalysis and performance evaluation.

## Ciphers Implemented

### 1. Playfair Cipher
- *Type*: Digraph Substitution Cipher
- *Key*: 5x5 Matrix constructed from a keyword
- *Encryption Process*:
  - Organizes letters into digraphs
  - Applies substitution based on position in matrix
  - Handles duplicate letters and odd-length messages
- *Implementation*: playfair_cipher.py
- *Complexity: **O(n)* for encryption and decryption

### 2. Hill Cipher
- *Type*: Matrix-Based Block Cipher
- *Key*: n x n Matrix (must have an inverse mod 26)
- *Encryption Process*:
  - Converts text into numerical vectors
  - Applies matrix multiplication mod 26
  - Uses modular inverse for decryption
- *Implementation*: hill_cipher.py
- *Complexity: **O(n³)* for decryption (due to matrix inversion)

### 3. Vigenère Cipher
- *Type*: Polyalphabetic Substitution Cipher
- *Key*: Repeated keyword of arbitrary length
- *Encryption Process*:
  - Shifts letters based on the repeating key
  - Implements character-wise modulo arithmetic
- *Implementation*: vigenere_cipher.py
- *Complexity: **O(n)* for encryption and decryption
  
### 4. Feistel Cipher
- *Type*: Block Cipher (Feistel Network)      
- *Key*: Fixed key (can be any length suitable for the algorithm)
- *Encryption Process*:
  - Divides the plaintext into two halves.
  - Performs multiple rounds of substitution and permutation with the round key.
  - After several rounds, the halves are swapped to produce the final ciphertext.
 - *Implementation*: feistel_cipher.py
- *Complexity:** O(n)* per round for encryption and decryption


### 5. DES (Data Encryption Standard)
- *Type*: Block Cipher (Feistel Network)
- *Key*: 56-bit key (with parity bits)
- *Encryption Process*:
   - Data is divided into 64-bit blocks.
   - 16 rounds of permutation and substitution, based on the round key. 
   - Each round involves expansion, substitution (using S-boxes), and permutation.
   - *Implementation*: des_cipher.py
- *Complexity:** O(16n)*, where n is the block size (fixed at 64 bits)

### 6. Monoalphabetic Substitution Cipher
- *Type*: Substitution Cipher
- *Key*: A substitution alphabet mapping
- *Encryption Process*:
   - Each letter in the plaintext is replaced with a corresponding letter in the ciphertext alphabet.
   - The mapping is a simple one-to-one relationship for letters.
   - *Implementation*: monoalphabetic_cipher.py
- *Complexity:** O(n)* for encryption and decryption

## How to Run the Code

### Prerequisites
Before running the scripts, ensure you have the following installed:
- *Python 3.x*
- *NumPy* (for matrix operations in Hill Cipher)
- *PyCryptodome* (for AES encryption in Hybrid Cipher)

Install dependencies using:
sh
pip install numpy pycryptodome


### Using GitHub Codespaces
If using *GitHub Codespaces*, follow these steps:

*Cipher_Codes Codespace*

Use this codespace to run the files

OR 

1. *Open the Repository in Codespaces*
   - Navigate to your repository on GitHub
   - Click on <> Code → Codespaces → New Codespace

2. *Run the Scripts*
   - Open the terminal in Codespaces
   - Run any of the Python scripts using:
     sh
     python3 <script_name>.py
     
   Example:
     sh
     python3 vigenere_cipher.py
     

3. *Provide Input When Prompted*
   - Each script may ask for input (key, plaintext, etc.)

## Example Usage

### Playfair Cipher
sh
python3 playfair_cipher.py

*Input:*

Enter the key: SECRET
Enter the message: HELLO WORLD

*Output:*

Encrypted Message: KFMTHZBQKD


### Hill Cipher
sh
python3 hill_cipher.py

*Input:*

Plaintext: SHORT
Key Matrix: [[7, 8], [11, 11]]

*Output:*

Encrypted: WFJTG


### Vigenère Cipher
sh
python3 vigenere_cipher.py

*Input:*

Plaintext: HELLO
Key: KEY

*Output:*

Ciphertext: RIJVS
Decrypted: HELLO
### Feistel Cipher
sh
python3 feistel_cipher.py

*Input:*

Enter a string : information
Enter a key : ise

*Output:*



Result :  0110100101101110011001100110111101110010011011010110000101110100011010010110111101101110

 key :0110100101101110011001100110111101110010011011010110000101110100011010010110111101101110
 
information

### DES Cipher:
sh
python3 des_cipher.py

*Input:*

Enter a string: attack

*Binary Conversion*:

01001000 01100101 01101100 01101100 01101111

*Generated Keys*:

Key  1  =  0011000111101011000001111010011000
 Key  2  =  0001110001110101100000111001100000
 Key  3  =  1110011101010000001111010011100000
   ….
Key  8  =  0001111101100000000001110100000000

### Monoalphabetic Cipher:

python3 monoalphabetic_cipher.py

*Input:*


Plaintext: information science
Encrypted text: vmslizngvlm hpvrmpr


*Output:*


Decrypted Message: INFORMATIONSCIENCE





## Comparative Analysis
| Cipher       | Type                         | Key Size        | Complexity (Enc/Dec) | Strengths                        | Weaknesses |
|-------------|------------------------------|-----------------|----------------------|---------------------------------|------------|
| Playfair    | Digraph Substitution         | 5x5 Key Matrix  | O(n)                 | More secure than simple monoalphabetic | Still vulnerable to digraph analysis |
| Hill        | Matrix-Based Block Cipher    | n x n Matrix    | O(n³)                 | Stronger encryption, uses algebra | Requires invertible key matrix |
| Vigenère    | Polyalphabetic Substitution  | Variable Length | O(n)                  | Resists simple frequency analysis | Still breakable with Kasiski method |
|Feistel Cipher|	Block Cipher (Feistel)	     |Variable	       | O(n)                 | per round	Flexible, suitable for block ciphers|	Weak if rounds are insufficient|
|DES	Block Cipher |(Feistel)	|56 bits	|O(16n)	|Well-established widely studied|	Vulnerable to brute force (short key)|
|Monoalphabetic|	Substitution Cipher|	26 letters|	O(n)	|Simple to implement and understand|	Easily broken via frequency analysis|


## Future Improvements
- Implement *automated cryptanalysis tools* to break weak ciphers.
- Enhance *key management* for Hill and Playfair ciphers.


For any issues or contributions, feel free to submit a pull request or open an issue in the repository.# ins-
