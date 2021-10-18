# Lecture 4-1: Operator & expression (2)

## number format

[https://en.wikipedia.org/wiki/Computer_number_format](https://en.wikipedia.org/wiki/Computer_number_format)

### Two's compliement

| Decimal value | Two's compliement |
| :-----------: | :---------------: |
|     $$0$$     |      `b000`       |
|     $$1$$     |      `b001`       |
|     $$2$$     |      `b010`       |
|     $$3$$     |      `b011`       |
|    $$-4$$     |      `b100`       |
|    $$-3$$     |      `b101`       |
|    $$-2$$     |      `b110`       |
|    $$-1$$     |      `b111`       |

### IEEE-754 single precision format

![IEEE-754 single precision](img/640px-Float_example.svg.png)

[IEEE-754 Floating Point Converter](https://www.h-schmidt.net/FloatConverter/IEEE754.html)

### Case Study: Fast inverse square root

``` c
float Q_rsqrt(float number)
{
  long i;
  float x2, y;
  const float threehalfs = 1.5F;

  x2 = number * 0.5F;
  y = number;
  i = *(long *) &y;          // evil floating point bit level hacking
  i = 0x5f3759df - (i >> 1); // what the fuck?
  y = *(float *)&i;
  y = y * (threehalfs - (x2 * y * y)); // 1st iteration
//y = y * (threehalfs - (x2 * y * y)); // 2nd iteration, this can be removed

  return y;
}
```

example:

$$ x = 0.15625, \frac{1}{\sqrt{x}} \approx 2.52982 $$

bit representation:

`0011_1110_0010_0000_0000_0000_0000_0000`  Bit pattern of both `x` and `i`

`0001_1111_0001_0000_0000_0000_0000_0000`  Shift right one position: `(i >> 1)`

`0101_1111_0011_0111_0101_1001_1101_1111`  The magic number `0x5F3759DF`

`0100_0000_0010_0111_0101_1001_1101_1111`  The result of `0x5F3759DF - (i >> 1)`


IEEE-754 32-bit representation:

`0_01111100_01000000000000000000000`  $$ y = 1.25 \times 2^{-3} $$

`0_00111110_00100000000000000000000`  $$ y = 1.125 \times 2^{-65} $$

`0_10111110_01101110101100111011111`  $$ y = 1.432430... \times 2^{63} $$

`0_10000000_01001110101100111011111`  $$ y = 1.307430... \times 2^{1} \approx 2.61486 $$

Reference:
* [htchen/i2p-nthu by 陳煥宗老師](https://github.com/htchen/i2p-nthu/tree/master/%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%E4%B8%80/Introduction%20to%20programming)
* [Two's complement - Wikipedia](https://en.wikipedia.org/wiki/Two%27s_complement)
* [Single-precision floating-point format - Wikipedia](https://en.wikipedia.org/wiki/Single-precision_floating-point_format)
* [Fast inverse square root - Wikipedia](https://en.wikipedia.org/wiki/Fast_inverse_square_root)