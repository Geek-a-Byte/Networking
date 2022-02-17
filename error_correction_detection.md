
## Error correction and detection

> There are many reasons such as noise, cross-talk etc. which may help data to get corrupted during transmission.
Data-link layer uses some error control mechanism to ensure that frames (data bit streams) are transmitted with a certain level of accuracy.

## Redundancy
- Central concept to detect + correct errors
- Extra bit/bits with data
- Added by sender
- Removed by receiver

## Detection
- Looking only if any error has occurred

## Correction
- More difficult than detection
- Exact number of corrupted bits are required along their location

## Forward Error Correction
- Receiver tries to guess the msg from redundant bits
- Possible when errors is small

## Retransmission
- Receiver detects the error and asks the sender to resend
- Resending is repeated until the arrival of error-free msg

## Parity Check for Detection 
- One extra bit is sent along with the original bits to make the number of 1s either 
- even in case of even parity, or 
- odd in case of odd parity.
- The sender while creating a frame counts the number of 1s in it. For example, if 
- Even parity is used and the number of 1s is even then one bit with value 0 is added. 
- This way the number of 1s remains even. 
- If the number of 1s is odd, to make it even a bit with value 1 is added. 

> The receiver simply counts the number of 1s in a frame. If the count of 1s is 
Even and even parity is used, the frame is considered to be not-corrupted and is accepted. 
If a single bit flips in transit, the receiver can detect it by counting the number of 1s. 
But when more than one bit are erroneous, then it is very hard for the receiver to detect the error.

## Checksum for Detection 

- Cyclic Redundancy Check (CRC) for Detection
- This technique involves binary division of the data bits being sent. 
- The divisor is generated using polynomials. 
- The sender performs a division operation on the bits being sent and calculates the remainder. 
- Before sending the actual bits, the sender adds the remainder at the end of the actual bits. 
- Actual data bits plus the remainder is called a codeword. 

## Block Coding

- Redundancy is achieved through various coding schemes
- Coding schemes may be block coding or convolution coding
- In block coding, message is divided into blocks
- Each blocks of k bits is called datawords
- Redundant r bits are added with each block where n=k+r
- Resulting n-bit blocks are called codewords
- Block coding process is one-to-one

<pre>
codeword = n bits
data bits = k bits
check bits = r bits. 
Then 
n = 2^r -1 and k = n-r
</pre>
