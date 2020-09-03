## General Notes:

### ASIC and GPU attacks:
1. scrypt key derivation function can use arbitrarily large amounts of memory and is therefore more resistant to ASIC and GPU attacks
2. bcrypt password hashing function requires a larger amount of RAM (but still not tunable separately, i. e. fixed for a given amount of CPU time) and is slightly stronger against such attacks
3. 
