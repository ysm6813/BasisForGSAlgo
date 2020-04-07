---
layout: post
title : C++ Operation Precendence
categories : Programming
--- 

연산자 우선순위는 사실 코드를 작성하면서 크게 신경쓰지 않는 부분이나. 다른사람이 작성한 코드를 보거나, 내신에는 기가막기게 내기 좋으니 알아두는게 좋다.
> **Note:** 항상 비트연산 우선순위 꼬여서 틀린다...

| Precedence | Operator          | Description                                               | Associativity |
| ---------- | ----------------- | --------------------------------------------------------- | ------------- |
| 1          | ::                | Scope resolution                                          | Left-to-right |
| 2          | a++   a−−         | Suffix/postfix increment and decrement                    | Left-to-right |
| 2          | type()   type{}   | Functional cast                                           | Left-to-right |
| 2          | a()               | Function call                                             | Left-to-right |
| 2          | a[]               | Subscript                                                 | Left-to-right |
| 2          | .   ->            | Member access                                             | Left-to-right |
| 3          | ++a   −−a         | Prefix increment and decrement                            | Right-to-left |
| 3          | +a   −a           | Unary plus and minus                                      | Right-to-left |
| 3          | !   ~             | Logical NOT and bitwise NOT                               | Right-to-left |
| 3          | (type)            | C-style cast                                              | Right-to-left |
| 3          | *a                | Indirection (dereference)                                 | Right-to-left |
| 3          | &a                | Address-of                                                | Right-to-left |
| 3          | sizeof            | Size-of[note 1]                                           | Right-to-left |
| 3          | co_await          | await-expression (C++20)                                  | Right-to-left |
| 3          | new   new[]       | Dynamic memory allocation                                 | Right-to-left |
| 3          | delete   delete[] | Dynamic memory deallocation                               | Right-to-left |
| 4          | .*   ->*          | Pointer-to-member                                         | Left-to-right |
| 5          | a*b   a/b   a%b   | Multiplication, division, and remainder                   | Left-to-right |
| 6          | a+b   a−b         | Addition and subtraction                                  | Left-to-right |
| 7          | <<   >>           | Bitwise left shift and right shift                        | Left-to-right |
| 8          | <=>               | Three-way comparison operator (since C++20)               | Left-to-right |
| 9          | <   <=            | For relational operators < and ≤ respectively             | Left-to-right |
| 9          | >   >=            | For relational operators > and ≥ respectively             | Left-to-right |
| 10         | ==   !=           | For relational operators = and ≠ respectively             | Left-to-right |
| 11         | &                 | Bitwise AND                                               | Left-to-right |
| 12         | ^                 | Bitwise XOR (exclusive or)                                | Left-to-right |
| 13         | \|                | Bitwise OR (inclusive or)                                 | Left-to-right |
| 14         | &&                | Logical AND                                               | Left-to-right |
| 15         | \|\|              | Logical OR                                                | Left-to-right |
| 16         | a?b:c             | Ternary conditional[note 2]                               | Right-to-left |
| 16         | throw             | throw operator                                            | Right-to-left |
| 16         | =                 | Direct assignment (provided by default for C++ classes)   | Right-to-left |
| 16         | +=   −=           | Compound assignment by sum and difference                 | Right-to-left |
| 16         | *=   /=   %=      | Compound assignment by product, quotient, and remainder   | Right-to-left |
| 16         | <<=   >>=         | Compound assignment by bitwise left shift and right shift | Right-to-left |
| 16         | &=   ^=   \|=     | Compound assignment by bitwise AND, XOR, and OR           | Right-to-left |
| 17         | ,                 | Comma                                                     | Left-to-right |

> Reference : [cppreference.com](cppreference.com)

