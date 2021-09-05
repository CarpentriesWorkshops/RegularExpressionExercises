# Regular Expressions Episode 1 Exercises

## Exercise 1.1

What will the regular expression ```Fr[ea]nc[eh]``` match?

<details>
<summary>Solution
</summary>

```
French
France
Frence
Franch
```

Note that the way this regular expression is constructed, it will match misspellings such as ```Franch``` and ```Frence```. Lacking an “anchor” such as ```^``` or ```\b```, this will also find strings where there are characters to either side of the regular expression, such as ```in French```, ```France's```, ```French-fried```.
</details>

## Exercise 1.2

What will the regular expression Fr[ea]nc[eh]$ match?

<details>
<summary>Solution
</summary>

```
French
France
Frence
Franch
```

This will match the pattern only when it appears at the end of a line. It will also find strings with other characters coming *before* the pattern, for example, in ```French``` or ```faux-French```.
</details>

## Exercise 1.3

What would match the strings ```French``` and ```France``` that appear at the beginning of a line?

<details>
<summary>Solution
</summary>

```
^France|^French
```

This will also find words where there were characters after ```French``` such as ```Frenchness```.
</details>

## Exercise 1.4

How do you match the whole words ```colour``` and ```color``` (case insensitive)??

<details>
<summary>Solution
</summary>

```
\b[Cc]olou?r\b|\bCOLOU?R\b
/colou?r/i
```

In real life, you should only come across the case insensitive variations ```colour```, ```color```, ```Colour```, ```Color```, ```COLOUR```, and ```COLOR``` (rather than, say, coLour). So based on what we know, the logical regular expression is ```\b[Cc]olou?r\b|\bCOLOU?R\b```.

An alternative more elegant option we’ve not discussed is to take advantage of the ```/``` delimiters and add an ‘ignore case’ flag. To use these flags, include ```/``` delimiters before and after the expression then letters after to raise each flag (where ```i``` is ‘ignore case’): so ```/colou?r/i``` will match all case insensitive variants of colour and color.

</details>

## Exercise 1.5

How would you find the whole word ```headrest``` and/or ```head rest``` but not ```head  rest``` (that is, with two spaces between ```head``` and ```rest```?

<details>
<summary>Solution
</summary>

```
\bhead ?rest\b
```

Note that although ```\bhead\s?rest\b``` does work, it will also match zero or one tabs or newline characters between ```head``` and ```rest```. So again, although in most real world cases it will be fine, it isn’t strictly correct.

</details>

## Exercise 1.6

How would you find a string that ends with four letters preceded by at least one zero?
<details>

<summary>Solution
</summary>

```
0+[A-Za-z]{4}\b
```

</details>

## Exercise 1.7

How do you match any four-digit string anywhere?

<details>
<summary>Solution
</summary>

```
\d{4}
```
Note: this will also match four-digit strings within longer strings of numbers and letters.
</details>

## Exercise 1.8

How would you match the date format ```dd-MM-yyyy```?

<details>
<summary>Solution
</summary>

```
\b\d{2}-\d{2}-\d{4}\b
```

Depending on your data, you may choose to remove the word bounding.
</details>

## Exercise 1.9

How would you match the date format ```dd-MM-yyyy``` or ```dd-MM-yy``` at the end of a line only?

<details>
<summary>Solution
</summary>

```
\d{2}-\d{2}-\d{2,4}$
```
Note this will also find strings such as ```31-01-198``` at the end of a line, so you may wish to check your data and revise the expression to exclude false positives. Depending on your data, you may choose to add word bounding at the start of the expression.
</details>

## Exercise 1.10

How would you match publication formats such as ```British Library : London, 2015``` and ```Manchester University Press: Manchester, 1999```?
<details>
<summary>Solution
</summary>

```.* ?: .*, \d{4}```

Without word boundaries you will find that this matches any text you put before ```British``` or ```Manchester```. Nevertheless, the regular expression does a good job on the first look up and may be need to be refined on a second, depending on your data.
</details>
