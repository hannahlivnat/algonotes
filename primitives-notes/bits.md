# Bits

### Type
Primitive

### Definition
A bit, or binary digit, is the smallest unit of data in a computer and has a single binary value represented by a 0 or 1. Most computers store data in bit multiples called "bytes", which consist of 8 bits.

### Associated Time / Space Complexity
Bitwise operations are faster, so can be good for optimizing a program

### When to Use
Used in data encryption/decoding, data or file compression / extraction, converting data between different representations

### Common Operations / Implementation
#### Bitwise Operators
NOT (~) converts each individual bit to its opposite
```
const a = 5;     // 00000000000000000000000000000101
const b = -3;    // 11111111111111111111111111111101

console.log(~a); // 11111111111111111111111111111010
// expected output: -6

console.log(~b); // 00000000000000000000000000000010
// expected output: 2
```

AND (&) compares each bit (1 && 1 = 1, anything else is 0)
```
const weekmask = 00000001
const eventmask = 00001111

const bitsCompared = weekmask & eventmask //00000001
```

OR (|) compares each bit (0 && 0 = 0, anything else is 1)
```
const weekmask = 00000001
const eventmask = 00001111

const bitsCompared = weekmask & eventmask //00001111
```

XOR (^) sets each bit to 1 if only one of the bits is 1
```
const weekmask = 00000001
const eventmask = 00001111

const bitsCompared = weekmask & eventmask //00001110
```

Zero Fill Left Shift (<<)
Shifts left by pushing zeros in from the right and let the leftmost bits fall off
```
x = 5 << 1 // 10 (0101 << 1 = 1010)
```

Signed Right Shift (>>)
Shifts right by pushing copies of the leftmost bit in from the left, and let the rightmost bits fall off. Preserves sign.
```
x = 5 >> 1  // 2 
x = -5 >> 1 // 3 (11111111111111111111111111111011 >> 1 = 11111111111111111111111111111101)
```

Zero Fill Right Shift
Shifts right by pushing zeros in from the left, and let the rightmost bits fall off
```
let x = 5 >>> 1; //2 (00000000000000000000000000000101 >>> 1 = 00000000000000000000000000000010)

// convert decimal to binary
(dec >>> 0).toString(2);
```

Binary Addition
* 0 + 0 = 0
* 0 + 1 = 1
* 1 + 0 = 1
* 1 + 1 = 10 (0 carry 1)

### Resource Links
* [Calendar with Bitwise Operators](https://snook.ca/archives/javascript/creative-use-bitwise-operators)
* [W3 Schools](https://www.w3schools.com/js/js_bitwise.asp)

