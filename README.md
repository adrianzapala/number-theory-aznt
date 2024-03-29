![Python Version](https://img.shields.io/badge/python-3.11-blue/)
![aznt version](https://img.shields.io/badge/aznt-0.0.44-green)
![Beta version](https://img.shields.io/badge/beta-ver.-green)

# `aznt` - From A to Z Number Theory

* Number Theory library for Python with prime numbers.
* **Important:** requires Python >= 3.11.
* You can pass to author's GitHub at
[adrianzapala.github.io](https://adrianzapala.github.io/).

# Install

```python
pip install aznt
```

# Imports

The package `aznt` includes three modules: `azntnumbers`, `azntprimality` and `azntplots`.<br>
**<span style="color: coral">Examples</span>**

```python
import aznt.azntnumbers as azn
import aznt.azntprimality as azpr
import aznt.azntplots as azpt
```

# General info about performance
When working with numbers 
with a large number of digits, calculation results slow down quickly. 
This is especially true for algorithms such as factorization,
searching for dividers etc. So for many large numbers, 
it can take a very long time to get results.


# Usage: `azntnumbers` module functions

## `factorization(n)`

Return prime factors of a number from a function argument.<br>
Time complexity: `O(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> factorization(8)
[2, 2, 2]
>>> factorization(1123243)
[11, 11, 9283]
>>> factorization(20570952)
[2, 2, 2, 3, 17, 127, 397]
```

## `dividers_naive(n)`

Returns divisors of a number from a function argument. It returns 
a list of these divisors.<br>
Time complexity: `O(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> dividers_naive(1123243)
[1, 11, 121, 9283, 102113, 1123243]
>>> dividers_naive(20570952)
[1, 2, 3, 4, 6, 8, 12, 17, 24, 34, 51, 68, 102, 127, 136, 204, 254, 381, 397, 408, 508, 762, 794, 1016, 1191, 1524, 1588, 2159, 2382, 3048, 3176, 4318, 4764, 6477, 6749, 8636, 9528, 12954, 13498, 17272, 20247, 25908, 26996, 40494, 50419, 51816, 53992, 80988, 100838, 151257, 161976, 201676, 302514, 403352, 605028, 857123, 1210056, 1714246, 2571369, 3428492, 5142738, 6856984, 10285476, 20570952]
```

## `dividers_opt(n)`

This function calculates divisors in pairs, which multiplication product creates 
a number from function argument. If the argument is default (`pairs=False`) 
and also if the numbers from these pairs are different it puts these pairs on the 
list and then sort list (if the numbers are equal, it's placing only one number on the list). 
Alternatively, if the argument is `True`  it join pairs of divisors (may be 
equal) into tuples and then append them into a list.<br>
This function works pretty much faster than `dividers_naive()` function.<br>
Time complexity: `O(sqrt(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
dividers_opt(100)
[1, 2, 4, 5, 10, 20, 25, 50, 100]
dividers_opt(100, pairs=True)
[(1, 100), (2, 50), (4, 25), (5, 20), (10, 10)]
```

## `tau(n)`

Count the number of divisors of an integer (including 1 and the number itself).<br>
Time complexity: `O(sqrt(n))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> tau(6)
4
>>> tau(4356)
27
>>> tau(12499674)
16
```

## `sigma(n)`

Return the sum of divisors of an integer 
(including 1 and the number itself).<br>
Time complexity: `O(sqrt(n)))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> sigma(3)
4
>>> sigma(343532)
687120
```

## `s(n)`

Return the sum of proper divisors of an integer 
(excluding `n` itself).<br>
Time complexity: `O(sqrt(n)))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> s(3)
1
>>> s(4438)
3194
```

## `gcd_mod(a, b)`

Return Greatest Common Divisor (GCD) of two positive integers using Euclidean algorithm 
with division.<br>
Time complexity: `O(log n))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> gcd_mod(36, 882)
18
>>> gcd_mod(363, 1287)
33
>>> gcd_mod(23, 3456)
1
>>> gcd_mod(484, 56)
4
```

## `gcd_subtract(a, b)`

Return Greatest Common Divisor (GCD) of two positive integers using Euclidean algorithm 
with subtraction.<br>
Time complexity: `O(n))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> gcd_subtract(36, 882)
18
>>> gcd_subtract(363, 1287)
33
>>> gcd_subtract(23, 3456)
1
>>> gcd_subtract(484, 56)
4
```

## `lcm(a, b)`

Return Lowest Common Multiple (LCM) of two positive integers.<br>
Time complexity: `O(log n))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> lcm(36, 882)
1764
>>> lcm(363, 1287)
14157
>>> lcm(23, 3456)
79488
>>> lcm(484, 56)
6776
```

## `is_gcd_eq_1(n, floor, ceil)`

Return a tuple. First
element of a tuple is a quantity of pairs of numbers which
are relatively prime to themselves, the second element is a density of them and 
the third element is a list of nested lists of them.
All pairs are randomly generated from `floor`
to `ceil` of numbers range (`n`). Based on that a variety of different 
outputs can be possible for the same parameters.<br>
Time complexity: `O(n log n))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> is_gcd_eq_1(25, 100, 10000)
(15, 0.6, [[1470, 8779], [8447, 5117], [7852, 5597], [8111, 7225], [5375, 6721], [9191, 4239], [7101, 6361], [1099, 211], [7036, 9515], [5281, 7212], [948, 2471], [3451, 4541], [3896, 9463], [8006, 845], [4448, 4803]])
>>> is_gcd_eq_1(25, 100, 10000)
(13, 0.52, [[7271, 5402], [9505, 5791], [8608, 1811], [6017, 9782], [1784, 3439], [8135, 9444], [3979, 9078], [2849, 2677], [888, 8171], [6399, 6145], [6647, 3679], [3697, 7051], [557, 553]])
```

## `totient(n)`

Return Euler's totient function (phi) which counts the positive integers up to 
a given integer `n` that are relatively prime to `n`.<br>
Time complexity: `O(log n))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> totient(4)
2
>>> totient(24)
8
>>> totient(424235)
253440
```

## `pnt(n)`

Return the asymptotic distribution of the prime numbers among 
the positive integers.<br>
Time complexity: `O(log n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> pnt(1000)
144.76482730108395 // Real value: 168
>>> pnt(1000000)
72382.41365054197 // Real value: 78498
```

## `prime_probability(n)`

Return probability if a random number is prime to a specific ceil given.<br>
Time complexity: `O(log n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> prime_probability(100)
0.21714724095162588
>>> prime_probability(1000)
0.14476482730108395
```

## `basel_problem(max, n=2)`

Return precise summation of the reciprocals of the squares of the 
natural numbers, i.e. the precise sum of the infinite series. 
The sum of the series is approximately 
equal to 1.644934 (pi^2 / 6 for `n` = 2).<br>
Time complexity: `O(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> basel_problem(345567)
1.6449311730576142
>>> basel_problem(2568, n=4)
1.0823232336914694
```

## `is_mersenne(m)`

Check if a number is Mersenne number, M = 2^n - 1 (prime or composite). Returns a four-element tuple. First element is boolean value - `True` or `False`.
If `True`, then second argument is M with exponent, third is the number in exponent (scientific) notation and the last is whole number.<br>
Time complexity: `O(log n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> is_mersenne(0)
Argument: 0. Mersenne numbers starts from 1.
>>> is_mersenne(1)
(True, 'M1', '1.00e+00', 1)
>>> is_mersenne(2)
False
>>> is_mersenne(7)
(True, 'M3', '7.00e+00', 7)
>>> is_mersenne(100)
False
>>> is_mersenne(255)
(True, 'M8', '2.55e+02', 255)
>>> is_mersenne(511)
(True, 'M9', '5.11e+02', 511)
>>> is_mersenne(1023)
(True, 'M10', '1.02e+03', 1023)
>>> is_mersenne(604462909807314587353087)
(True, 'M79', '6.04e+23', 604462909807314587353087)
```

## `is_fermat(f)`

Check if a number is Fermat number, F = 2^2^n - 1 (prime or composite). Returns a four-element tuple. First element is boolean value - `True` or `False`.
If `True`, then second argument is F with exponent, third is the number in exponent (scientific) notation and the last is whole number.<br>
Time complexity: `O(log (log n))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> is_fermat(-3)
Argument: -3. Fermat numbers starts from 3.
>>> is_fermat(1)
Argument: 1. Fermat numbers starts from 3.
>>> is_fermat(3)
(True, 'F0', '3.00e+00', 3)
>>> is_fermat(5)
(True, 'F1', '5.00e+00', 5)
>>> is_fermat(7)
False
>>> is_fermat(17)
(True, 'F2', '1.70e+01', 17)
>>> is_fermat(257)
(True, 'F3', '2.57e+02', 257)
>>> is_fermat(65537)
(True, 'F4', '6.55e+04', 65537)
>>> is_fermat(4294967297)
(True, 'F5', '4.29e+09', 4294967297)
>>> is_fermat(18446744073709551617)
(True, 'F6', '1.84e+19', 18446744073709551617)
>>> is_fermat(340282366920938463463374607431768211457)
(True, 'F7', '3.40e+38', 340282366920938463463374607431768211457)
>>> is_fermat(115792089237316195423570985008687907853269984665640564039457584007913129639937)
(True, 'F8', '1.16e+77', 115792089237316195423570985008687907853269984665640564039457584007913129639937)
>>> is_fermat(13407807929942597099574024998205846127479365820592393377723561443721764030073546976801874298166903427690031858186486050853753882811946569946433649006084097)
(True, 'F9', '1.34e+154', 13407807929942597099574024998205846127479365820592393377723561443721764030073546976801874298166903427690031858186486050853753882811946569946433649006084097)
```
## `is_perfect(n)`

Check if a number is perfect number. If so, returns True, False otherwise.<br>
Time complexity: `O(sqrt(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> is_perfect(7)
False
>>> is_perfect(8128)
True
```

## `zeta_trivial_value(s, n=10000)`

Return **trivial** (real) value of Riemann zeta function for given argument, where `s` is zeta
function argument, and `n` is number of terms in the series of zeta.<br>
Time complexity: `O(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> zeta_trivial_value(-49)
-1.5001733492153957e+23
>>> zeta_trivial_value(-31)
472384867.72163075
>>> zeta_trivial_value(-19)
26.45621212121214
>>> zeta_trivial_value(-15)
0.44325980392156883
>>> zeta_trivial_value(-5)
-0.003968253968253967
>>> zeta_trivial_value(-4)
0
>>> zeta_trivial_value(0)
0.5
>>> zeta_trivial_value(.1)
-0.6029256240132325
>>> zeta_trivial_value(.5)
-1.4482837427744006
>>> zeta_trivial_value(1)
inf
>>> zeta_trivial_value(5)
1.0369277551433702
>>> zeta_trivial_value(33)
1.0000000001164155
>>> zeta_trivial_value(50)
1.0000000000000009
```

## `nontrivial_zeros_dist(t)`

Return average distance between zeros on a critical line in Riemann zeta function.<br>
Time complexity: `O(log n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> nontrivial_zeros_dist(20)
5.426572570049043
>>> nontrivial_zeros_dist(100)
2.2705167236263177
>>> nontrivial_zeros_dist(1000)
1.2393168126993492
```

## `pstats1(data_rows=29)`

Return statistics of prime numbers up to `data_rows` which in default is equal `29`. 
This value can be changed from a function argument, but it can't be greater 
than that value. It can't be lower than 1 also. Rows statistics starts 
from 10 up to 10^29, and they are for prime numbers in these ranges.<br>
Time complexity: `O(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> pstats1()
<Returns all table>
>>> pstats1(-2)
Incorrect argument
>>> pstats1(5)
    x                  π(x)                      x/π(x)                    logx            (x/π(x) - logx) / x/π(x) [%] 
1e+01     4                             2.5                      2.302585092994046        7.896596280238163             
1e+02     25                            4.0                      4.605170185988092        15.129254649702295            
1e+03     168                           5.9523809523809526       6.907755278982137        16.050288686899894            
1e+04     1229                          8.136696501220504        9.210340371976184        13.195083171587305            
1e+05     9592                          10.42535446205171        11.512925464970229       10.431981059994436            
```

## `pstats2(data_rows=29)`

Return statistics of prime numbers up to `data_rows` which in default is equal `29`. 
This value can be changed from a function argument, but it can't be greater 
than that value. It can't be lower than 1 also. Rows statistics starts 
from 10 up to 10^29, and they are for prime numbers in these ranges.<br>
Time complexity: `O(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> pstats2()
<Returns all table>
>>> pstats2(-2)
Incorrect argument
>>> pstats2(4)
    x               PNT: Li(x)                       π(x)                    PNT: x/logx       
1e+01     6.165599504787298             4                             4.3429448190325175       
1e+02     30.12614158407963             25                            21.71472409516259        
1e+03     177.60965799015221            168                           144.76482730108395       
1e+04     1246.1372158993884            1229                          1085.7362047581294
```

## `pstats3(data_rows=29)`

Return statistics of prime numbers up to `data_rows` which in default is equal `29`. 
This value can be changed from a function argument, but it can't be greater 
than that value. It can't be lower than 1 also. Rows statistics starts 
from 10 up to 10^29, and they are for prime numbers in these ranges.<br>
Time complexity: `O(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> pstats3()
<Returns all table>
>>> pstats3(-2)
Incorrect argument
>>> pstats3(3)
    x                  π(x)                       PNT: Li(x)                Li(x) - π(x)         (Li(x) - π(x)) / π(x) [%]   
1e+01     4                             6.165599504787298             2.165600                 54.139988                     
1e+02     25                            30.12614158407963             5.126142                 20.504566                     
1e+03     168                           177.60965799015221            9.609658                 5.720035
```

## `fib()`
Return dictionary of Fibonacci numbers from `0` to `n`. Key is an index, and a value is a specific Fibonacci number. First must create `Fibonacci` class object and then call `fib()` method on it.
Time complexity: `O(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> fob = Fibonacci(15)
>>> print(fob.fib())
{0: 0, 1: 1, 2: 1, 3: 2, 4: 3, 5: 5, 6: 8, 7: 13, 8: 21, 9: 34, 10: 55, 11: 89, 12: 144, 13: 233, 14: 377, 15: 610}
```

# Usage: `azntprimality` module functions

## `is_prime_naive1(n)`
Return if number is a prime.
Time complexity: `O(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> is_prime_naive1(7)
True
```

## `is_prime_naive2(n)`
Return if number is a prime. This function is faster than `is_prime_naive1()` function.<br>
Time complexity: `O(n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> is_prime_naive2(5)
True
```

## `is_prime_sqrt(n)`
Return if number is a prime. This function is faster than `is_prime_naive2()` function.<br>
Time complexity: `O(sqrt(n)))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> is_prime_sqrt(101)
True
```

## `is_prime_sqrt_odd(n)`
Return if number is a prime. This function is faster than `is_prime_sqrt()` function.<br>
Time complexity: `O(sqrt(n)))`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> is_prime_sqrt(23)
True
```

## `eratosthenes_sieve(n)`
Return list of prime numbers from 2 up to `n` range.<br>
Time complexity: `O(n log n)`.<br>
**<span style="color: coral">Examples</span>**
```python
>>> eratosthenes_sieve(100)
[2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
```

# Usage: `azntplots` module functions

## `critical_strip()`

Return a plot presenting critical strip and critical line of Riemann zeta.<br>

## `riemann_zeta()`

Return a plot presenting Riemann zeta function for critical line arguments.<br>
