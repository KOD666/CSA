
## Des (Data Encryption Standard) 

#### Q) Feistel Structure  : 

**Feistel Structure :**

![[Pasted image 20250311182159.png]]

##### Parameters For Applying This :

-> Block Size 

- Large Block Size Is Provided high security is achieved by diffusion
- 64 bit block is universal block cipher design
- Encryption/Decryption Speed is very Less
 
-> Key Size

- When key size is high the apllied will provide high security
- 128 bit is what commonly used

-> Number Of Rounds 

- A Single Round of this provide less security
- When applied more rounds the security keeps getting increased
- There are 16 rounds in this 

**Round Function :**

![[Pasted image 20250311183219.png]]

##### The process will be like :

- The right half (R) is fed into the round function (F) along with a subkey (K).
- The output of F(R, K is XORed with the left half (L).
- The halves are swapped for the next round.


## Basic Des And Its Architecture 


## Just For Understand :

**![[Pasted image 20250311184042.png]]**


Content :

- DES (Data Encryption Standard) was adopted by NIST in 1977.
- uses a 64-bit input and produces a 64-bit output.
- The main key is 64 bits long, but only 56 bits are used for encryption.
- DES operates through 16 rounds, using 48-bit round keys in each round.

DES Diagram performing 16 rounds of encryption :

![[Pasted image 20250311192032.png]]


S Box :

- DES contains 8 different S-boxes, each transforming 6 input bits into 4 output bits
- The 48-bit result is divided into eight 6-bit pieces
- Each 6-bit piece is processed by one of eight S-boxes
- Each S-box transforms a 6-bit input into a 4-bit output

![[Pasted image 20250311192225.png]]

P Box :

- Takes the 32-bit output from the S-boxes and rearranges the bits according to a fixed pattern
- Maps each input bit to a different output position
- Unlike S-boxes, P-boxes do not change bit values, only their positions

![[Pasted image 20250311192618.png]]

##### Andar Ke Number Random Chalege esa boli to thi twinkle pattern hai par pata nai hai

## Single Round for des :


![[Pasted image 20250311193015.png]]

- Firstly The Dotted Line Is The Mangler Function which performs the most of the encryption part of des (Just For info)

- Each round takes a 64-bit input block and produces a 64-bit output block
- The 64-bit input block is split into two 32-bit halves: Left (L) and Right (R)
- Each round also uses a 48-bit subkey derived from the main 56-bit key through the key schedule
- The 32-bit Right half (R) is expanded to 48 bits by this follwing diagram
- This expansion duplicates some bits according to a fixed table
- The 32-bit data is stretched to 48 bits by repeating certain bits
-  ![[Pasted image 20250311193717.png]]

- The expanded 48-bit Right half is XORed with the 48-bit round subkey
- adds to subkey using XOR
- passes through 8 S-boxes to get 32-bit result
- ![[Pasted image 20250311192225.png]]

- At Last The permuted result is XORed with the original Left half (L)
- This becomes the new Right half for the next round
- This becomes the new Right half for the next round and goes until round 16


## Q) Explain S Box :

S Box :

- DES contains 8 different S-boxes, each transforming 6 input bits into 4 output bits
- The 48-bit result is divided into eight 6-bit pieces
- Each 6-bit piece is processed by one of eight S-boxes
- Each S-box transforms a 6-bit input into a 4-bit output
- ![[Pasted image 20250311192225.png]]

- Draw a random s-box
- ![[Pasted image 20250311195507.png]]
- ![[Pasted image 20250311200331.png]]
- In this the value is defined by a 6 bit value in which the first and last bit are consider as an row for indication and the inner 4 wil be the column for indication.. 
- row selection depends on both data & key this feature is known as autoclaving (autokeying)
- example:
	S(18 09 12 3d 11 17 38 39) = 5fd25e03
- As example :
 ![[Pasted image 20250311212131.png]]


## How can we achieve confusion and diffusion in DES, explain its steps in detail?


-> Confusion and Diffusion

- Claude Shannon introduced these two terms

- More practically Shannon suggested combining S & P elements to obtain:

-> Confusion 

- It is a technique of ensuring that a cipher text gives no clue about plain text
- It is achieved by substitution technique.
###### S-boxes (Substitution Boxes)
- The eight S-boxes in DES are the primary source of confusion
- Each S-box takes 6 bits of input and produces 4 bits of output using a non-linear transformation
- The input bits select a specific value from a lookup table in a way that's not linearly related
- the diagram thing 
    1. The outer bits (1st and 6th) select one of four rows
    2. The inner bits (2nd through 5th) select one of 16 columns
    3. The value at the selected position becomes the 4-bit output
- The S-box design ensures that changing even one input bit changes multiple output bits in an unpredictable way
- The way subkeys are derived from the main key adds another layer of confusion
- This ensures that each bit of the key influences many bits of the ciphertext

-> Diffusion

- increases redundancy of the plain text by spreading it across rows and columns.
- It is achieved by permutation known as transposition technique.
###### Expansion Function (E)
- Expands the 32-bit right half to 48 bits before the S-box operation
- Some bits are duplicated, appearing in multiple positions
- This ensures that each bit potentially affects multiple S-boxes
- One input bit can influence multiple output bits- After the S-box substitution, the 32-bit output undergoes a fixed permutation
- This scatters the output bits from each S-box across different position


- Each round builds upon the previous, creating an avalanche effect