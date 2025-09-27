# E-Voting System with RSA Homomorphic Encryption


A secure electronic voting system that uses RSA homomorphic encryption to ensure confidentiality, integrity, and verifiability of votes while leveraging cloud infrastructure for scalability and efficiency.

📖 Overview

This project implements an e-voting system that allows voters to cast encrypted ballots using multiplicative homomorphic properties of RSA. The system ensures that votes are tallied without decrypting individual ballots, preserving voter privacy. It consists of a web-based frontend, a cloud-based voting server, and a MySQL database for storing voter and election data.

✨ Features

Homomorphic Encryption: Supports multiplicative homomorphic operations using RSA.
Voter Authentication: Username/password-based authentication with one-vote-per-voter enforcement.
Cloud-Based Architecture: Uses public and private cloud servers for vote storage and tallying.
Result Integrity: Ensures votes cannot be altered once cast.
Admin Interface: For candidate management and result viewing.
Biometric Readiness: Designed to support future integration with government biometric databases.

🏗️ System Architecture

The system operates in five phases:

Registration: Voters register via a central system (with potential biometric verification).
Authentication: Voters log in using credentials to cast a vote.
Key Generation: Unique primes are assigned to candidates; public/private key pairs are generated.
Voting: Votes are encrypted using RSA and sent to the public cloud.
Counting: The private cloud homomorphically combines votes, decrypts the total, and factors it to determine results.

🗃️ Database Schema

The MySQL database includes the following tables:

users: Voter information and authentication details.
candidates: Candidate details.
voting_table: Encrypted votes and voter hashes.
parameter: Stores public key (kpub) and modulus (prime_n).
See online_voting.sql for full schema and sample data.

🔐 Homomorphic Voting Example

If two voters vote for candidate A (prime = 3) and one for candidate B (prime = 5):

Encrypted votes: 
c
1
=
3
e
m
o
d
 
 
n
c 
1
​	
 =3 
e
 modn, 
c
2
=
3
e
m
o
d
 
 
n
c 
2
​	
 =3 
e
 modn, 
c
3
=
5
e
m
o
d
 
 
n
c 
3
​	
 =5 
e
 modn
Combined ciphertext: 
C
=
c
1
×
c
2
×
c
3
m
o
d
 
 
n
C=c 
1
​	
 ×c 
2
​	
 ×c 
3
​	
 modn
Decrypted result: 
P
=
C
d
m
o
d
 
 
n
=
3
2
×
5
1
P=C 
d
 modn=3 
2
 ×5 
1
 
Tally: Candidate A = 2 votes, Candidate B = 1 vote


⚠️ Limitations

Trust in Public Cloud: The public cloud could potentially inject fake votes if not properly monitored.

No Built-in Verification: Voters cannot independently verify their votes after casting.

Single Authority: Relies on a central server for key generation and tallying.


🚀 Future Enhancements

Integrate biometric authentication for stronger voter verification.

Add end-to-end verifiability for voters.

Support for fully homomorphic encryption (FHE) for more complex elections.

📚 References

Zhao, Y., Pan, Y., Wang, S., et al. (2014). An anonymous voting system based on homomorphic encryption.

Sebe, F., Miret, J. M., Puiolas, J., et al. (2010). Hash-based verifiable mixing for remote electronic voting.

Neoo, H., Aung, A. M., et al. (2014). A Survey of Different Electronic Voting Systems.
