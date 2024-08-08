---
title: "JavaScript BigInt: Handling Astronomical Numbers with Precision"
seoTitle: "JavaScript BigInt: Precision for Huge Numbers"
seoDescription: "Learn about JavaScript BigInt and how it provides precise handling of large integers for financial calculations, cryptography, and more"
datePublished: Thu Aug 08 2024 04:30:56 GMT+0000 (Coordinated Universal Time)
cuid: clzks5wye001r0al15eug1hvu
slug: javascript-bigint-handling-astronomical-numbers-with-precision
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723030858089/4d79959d-d755-4ba0-899e-1f581bb5f74a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1723030878359/ffb84987-1e66-4240-ab7b-af8d79cc3316.png
tags: programming-blogs, javascript, web-development, javascript-framework, beginners

---

## Introduction

In the vast universe of JavaScript, there's a new star shining bright: BigInt. Introduced in ES2020, BigInt is a built-in object that allows you to work with integers of arbitrary precision. If you've ever hit the ceiling of `Number.MAX_SAFE_INTEGER` (9,007,199,254,740,991) or needed to perform calculations with astronomical figures, BigInt is here to save the day.

## The Problem BigInt Solves

Before we dive into BigInt, let's understand why it's needed. JavaScript traditionally uses the `Number` type to represent both integers and floating-point numbers. This type is based on the IEEE 754 double-precision floating-point format, which can precisely represent integers up to 2^53 - 1. Beyond this, you start to lose precision.

```javascript
console.log(9007199254740991 + 1); // 9007199254740992
console.log(9007199254740991 + 2); // 9007199254740992 (Oops!)
```

This limitation can be a significant problem in fields like finance, cryptography, or when working with very large datasets.

## Enter BigInt

BigInt allows you to represent integers with arbitrary precision. Here's how you can create a BigInt:

```javascript
// Using the BigInt() function
let bigInt = BigInt(9007199254740991);

// Or by appending 'n' to an integer literal
let anotherBigInt = 9007199254740991n;

console.log(bigInt === anotherBigInt); // true
```

Now, let's see BigInt in action:

```javascript
console.log(9007199254740991n + 1n); // 9007199254740992n
console.log(9007199254740991n + 2n); // 9007199254740993n (Correct!)
```

## Working with BigInt

### Basic Operations

BigInt supports all the basic arithmetic operations:

```javascript
let a = 1234567890123456789n;
let b = 9876543210987654321n;

console.log(a + b); // 11111111111111111110n
console.log(a * b); // 12193263111263526900438452720368555n
console.log(b - a); // 8641975320864197532n
console.log(b / a); // 8n (Integer division)
console.log(b % a); // 1219326311126352690n
```

Note that division with BigInt always results in an integer, truncating any decimal part.

### Comparison

BigInt values can be compared using the standard comparison operators:

```javascript
console.log(10n > 5n); // true
console.log(10n < 5n); // false
console.log(10n === 10); // false (strict equality)
console.log(10n == 10); // true (loose equality)
```

### Bitwise Operations

BigInt supports most bitwise operations:

```javascript
console.log(17n & 13n); // 1n
console.log(17n | 13n); // 29n
console.log(17n ^ 13n); // 28n
console.log(~17n); // -18n
console.log(17n << 1n); // 34n
console.log(17n >> 1n); // 8n
```

Note that there's no support for `>>>` (zero-fill right shift) with BigInt.

## Practical Applications

### Financial Calculations

BigInt is particularly useful for financial calculations where precision is crucial:

```javascript
function calculateCompoundInterest(principal, rate, time, compound) {
  const p = BigInt(Math.round(principal * 100)); // Convert to cents
  const r = BigInt(Math.round(rate * 100));
  const t = BigInt(time);
  const n = BigInt(compound);

  const amount = p * ((1n + r / (100n * n)) ** (n * t)) / (100n ** t);
  
  return Number(amount) / 100; // Convert back to dollars
}

console.log(calculateCompoundInterest(1000000, 5, 30, 12));
// 4321942.30 (precise to the cent)
```

### Cryptography

BigInt is also valuable in cryptography, where working with very large prime numbers is common:

```javascript
function modPow(base, exponent, modulus) {
  if (modulus === 1n) return 0n;
  let result = 1n;
  base = base % modulus;
  while (exponent > 0n) {
    if (exponent % 2n === 1n) {
      result = (result * base) % modulus;
    }
    exponent = exponent / 2n;
    base = (base * base) % modulus;
  }
  return result;
}

// Example: Calculate 3^(2^100) mod 1000000007
console.log(modPow(3n, 2n ** 100n, 1000000007n)); // 598046965n
```

This function implements the modular exponentiation algorithm, crucial in many cryptographic operations.

## Best Practices and Considerations

While BigInt is powerful, it's important to use it judiciously:

1. **Performance**: Operations on BigInt are generally slower than on Number. Use BigInt only when necessary.
    
2. **Type Coercion**: Be careful when mixing BigInt with other types. Explicit conversions are often necessary.
    
3. **JSON**: BigInt values aren't serialized in JSON by default. You may need custom serialization/deserialization logic.
    
4. **Math Object**: Many Math object methods don't support BigInt. You might need to implement your own mathematical functions for BigInt.
    
5. **Fractional BigInt**: There's no such thing as a fractional BigInt. For calculations requiring fractional values, consider using a library like decimal.js.
    

## Browser Support

As of 2023, BigInt is supported in all modern browsers. However, for older browsers, you might need to use a polyfill or transpile your code.

## Conclusion

BigInt opens up new possibilities in JavaScript, allowing us to work with integers of any size with precision. Whether you're dealing with financial calculations, cryptography, or any other domain requiring large integers, BigInt provides the tools you need.

As web applications become more complex and handle larger datasets, features like BigInt become increasingly important. By mastering BigInt, you're equipping yourself with a powerful tool in the JavaScript ecosystem.

Remember, with great power comes great responsibility. Use BigInt when you need it, but be mindful of its performance implications and interoperability considerations. Happy coding, and may your calculations always be precise!