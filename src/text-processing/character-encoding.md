# Character Encoding

The process of converting data from one form to another is called `Encoding`. It is used to transform the data so that data can be supported and used by different systems. Encoding works similarly to converting temperature from centigrade to Fahrenheit, as it just gets converted in another form, but the original value always remains the same.

Character "A" in a way is a graphical image. When you read it, it make sense to you because you map it with a sound you speak and what it means to you.

Character encoding is the process of assigning numbers to graphical characters, especially the written characters of human language, allowing them to be stored, transmitted, and transformed using digital computers.

## Fundamentals

A `bit` is either a `0` or a `1`. A `byte` is a set of 8 bits.
Characters are stored in a computer as one or more bytes. Each character is mapped to a fixed number, which can be converted into a binary number and stored in a computer. The mapping of the character to the number is stored in ASCII or something else.

These characters can be an English character, a Latin letter, a Chinese ideograph, any a character in another language.

Characters that are needed for a specific purpose are grouped into a character set (also called a repertoire).

There are two concepts of importance here: the `character repertoire` and the `encoding`. The term `charset` has been used for both of these, which can lead to some confusion.
The character repertoire is the total set of available characters. For HTML this is defined to be `ISO/IEC 10646`, which to all intents and purposes is equivalent to Unicode. You cannot change this; it’s built into HTML.

What you can vary is the encoding, which is how the characters in a given repertoire are represented numerically, i.e., in a form that computers can understand.

Words and sentences in text are created from characters.



## Character Encoding Scheme (CES)

You may have heard of UTF-8 encoding. What is it?

Simple Character encoding scheme

* UTF-8
* UTF-16BE
* UTF-16LE
* UTF-32BE
* UTF-32LE

Compound Character encoding scheme

* UTF-16
* UTF-32
* ISO/IEC 2022

## References

* [Types of Encoding Techniques](https://www.javatpoint.com/types-of-encoding-techniques)
