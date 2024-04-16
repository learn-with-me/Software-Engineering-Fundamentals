# Data Storage

In the context of computers, data storage is storing information (data) in an electronic storage medium. This information can be human language or electronic data from another computer.

Barcodes and magnetic ink character recognition (MICR) are two ways of recording machine-readable data on paper.

All data gets transformed into bits, and is stored as bits `0`s and `1`s either in RAM or DISK. Decimal number can be easily converted to their binary equivalent. For characters (English and other languages), emojis, etc, there is a collectively agreed mapping to convert these units into specific numeric values, which then gets converted into binary equivalents, and stored.

One of the most popular mapping is ASCII. ASCII can support 127 character set. To convert a word like "HELLO" in ASCII, you look up the relevant decimal value of each character, convert that value to binary, and concatenate them all together to get the storage ready version. In this case, each character becomes 8-bit or 1 byte of binary data.

The process of converting the characters into binary equivalent using the character set is called encoding the string. For decoding, you do everything in reverse.

There are over 10,000 characters in the Chinese language. This is where the `Unicode` standard comes in, which encompses over 100,000 unique characters in over 100 languages, including emojis. Unicode has several encoding strategies with different pros and cons, like UTF-32.

The word `Character` is ambiguous. Use the word `Grapheme` instead, which is a single unit of human writing system.

## References

* YT - [Unicode, in friendly terms: ASCII, UTF-8, code points, character encodings, and more](https://www.youtube.com/watch?v=ut74oHojxqo&ab_channel=StudyingWithAlex) | Studying With Alex
* YT - [ASCII and Unicode Character Sets](https://www.youtube.com/watch?v=I-pQH_krD0M&ab_channel=ComputerScience)
* YT - [Character Encoding and Unicode Tutorial](https://www.youtube.com/watch?v=105IRQXy2oQ&ab_channel=CodeLit)
* [What is UTF-8? UTF-8 Character Encoding Tutorial](https://www.freecodecamp.org/news/what-is-utf-8-character-encoding/) | FreeCodeCamp
* [Charset for Spanish language site](https://www.sitepoint.com/community/t/charset-for-spanish-language-site/5061)
    * [The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets (No Excuses!)](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
    * [UTF-8 History](https://www.cl.cam.ac.uk/~mgk25/ucs/utf-8-history.txt)
* [Character encodings for beginners](https://www.w3.org/International/questions/qa-what-is-encoding) | W3C
* [Types of Encoding Techniques](https://www.javatpoint.com/types-of-encoding-techniques) | JavaPoint
* Java 7
    * https://docs.oracle.com/javase/7/docs/api/java/lang/Character.html#unicode
    * https://docs.oracle.com/javase/7/docs/api/java/nio/charset/Charset.html
* Java 9
    * https://docs.oracle.com/javase/9/docs/api/java/lang/Character.html#unicode
    * https://docs.oracle.com/javase/9/docs/api/java/nio/charset/Charset.html
