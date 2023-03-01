# Regex Tutorial

`Regex` stands for `Regular Expressions`. These are handy tools that can help filter through data/information with a series of parameters that the user sets.

## Summary
___NOTE___: For the full breakdown of each part of the regex refer to [Full Break Down of Regex](#Full-Break-Down-of-Regex)


The example regex that we will be covering is: 

`/((([hH][tT]{2}[pP])|([hH][tT]{2}[pP][sS])|([fF][tT][pP])):[\/]{2})?([a-zA-Z0-9\-\.]+\.[a-zA-Z]{1,4})(:[0-9]+)?\/?([a-zA-Z0-9\-\._\?\,\'\/\\\+&;%\$#\=~]*)/g`

This regex is used to identifying whether or not a set of characters are a `https`, `http`, or `ftp` URL by matching the contents of the text being examined with a prestructured form. Specifically, this regex example will look for text that follow the form:

`Protocol` + `Domain Name` + `Path Name`

Examples of items that would match:

![___PICTURE OF CODE IN ACTION___]()

___NOTE___:
This Regex has its limitations on what it is filtering and what gets caught by accident For example:

![___PICTURE OF CODE IN ACTION___]()

These are both examples of items that would be returned as a false positive.

## Table of Contents

- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Full Break Down of Regex](#Full-Break-Down-of-Regex)

## Regex Components
___NOTE___: These components are not the complete list of regex operations but the ones used in the example above. For a full list of regex operations refer to [Regexr.com](https://regexr.com/), great tool to help with understanding regex.

### Quantifiers
Quantifiers define the number of times that a term is searched.

The quantifiers used in this example are:

`+` = called a `plus`.matches if 1 or more matching value exists.

        - (ie. the regex: `/a+/`  would match `a`, `aa`, or even `aaa`)

`*` = called a `star`. matches if 0 or more matching values exist

        - (ie. the regex `/ba*/` would match `b`, `ba`, `baa`, or even `baaa` )

`{}` = called a `quantifier`. Determines how many values should match

        - (ie. the regex `/a{3}/` would ___only___ match `aaa`)

`?` = added to selection that is optional. 

        - (ie. the regex `/ba?/` would ___only___ match `b` or `ba`)


### OR Operator
`|` = called the `OR operator`. allows regex to match between different values.

        - (ie. the regex `/cat|dog/` would match either values `cat` or `dog` )
        - (ie. the regex `/(red|blue|yellow) car/` would match `red car`, `blue car`, or
             `yellow car`)

### Character Classes
Character classes or character sets tell regex which characters to search for. 

`[]`= called a `character set`. looks for any 1 value within the set.

        - (ie. the regex `/[abc]/` would match `a`, `b`, or `c`)
        - (ie. the regex `/[a1b]/` would match `a`, `1`, or `b` )

### Bracket Expressions
Bracket expressions are character sets that match to multiple different values

`[A-Z]` = called a `bracket expression`. looks for any values between the ranges set

        - (ie. the regex `/[a-z]/` would match any lower case letter `a`, `b`, `c`....`z`)
        - (ie. the regex `/[A-Z]/` would match any upper case letter `A`, `B`, `C`....`Z`)
        - (ie. the regex `/[0-9]/` would match any digits `0`, `1`, `2` ... `9`)


### Flags
Flags are additional search parameters that are added onto the end of a regular expression.

The flag used in the Regex example is: 

`g` = is called `global`. searches the section for everything that fulfills the statement

        - (ie. the regex ___WITHOUT___ the global flag `/b/` would find the first `b` in
            the sentence `big blue bulbs`)
        - (ie. the regex `/b/g` would find all 4 `b`'s in the string `big blue bulbs`)

### Grouping and Capturing
Capturing groups are a way in regex to group a set of terms that can be manipulated

`()` = called a `capturing group`. allows for group modifiers and optional phrases

        - (ie. the regex `/(hot|dog){2}/` will match `hothot`, `hotdog`,`doghot` or `dogdog`)

### Greedy and Lazy Match
Greedy and lazy matches are 2 ways to matching values. The example regex only makes use of Greedy Matches

__Greedy Match__: 

This is the default matching style of Regex quantifiers It will match every character possible. 

        - (ie. the regex `/a+/` tested against the string `aaa` would match `aaa`)

__Lazy Match__: 

This is the opposite matching style of Regex quantifiers It will match the fewest characters possible. This is denoted using the special character `?` after a quantifier.

        -(ie. the regex `/a+?/` tested against the string `aaa` would match `a`, `a`, and `a` as 3 seperate matches)

## Full Breakdown of Regex
Now that we understand the tools that were used in this regex, lets break down each part of the regex part by part. By default regex are noted by 2 forward slash icons `/` with the statement located between them as shown below. anything after the the final `/` symbol is a flag that helps modify the statement (will be explained later in the breakdown).

`/((([hH][tT]{2}[pP])|([hH][tT]{2}[pP][sS])|([fF][tT][pP])):[\/]{2})?([a-zA-Z0-9\-\.]+\.[a-zA-Z]{1,4})(:[0-9]+)?\/?([a-zA-Z0-9\-\._\?\,\'\/\\\+&;%\$#\=~]*)/g`


___Part 1:___

The first part that we will examine is the `Protocol` that this regex looks for:

`((([hH][tT]{2}[pP])|([hH][tT]{2}[pP][sS])|([fF][tT][pP])):[\/]{2})?`

We can further break this down into 2 different sets of information so that we can truly see each component:

```
TLDR; looks for any combination of `http` or `https` or `ftp`

1.  (  ([hH][tT]{2}[pP]) | ([hH][tT]{2}[pP][sS]) | ([fF][tT][pP])  )
    - We have 3 different Capture Groups here

        - ( [hH] [tT]{2} [pP] )
            - in this capture group we are searching for the text `http`
            - with the character set `[]`, we can pass in both the capital and lower case
                letters so any variations of the 4 letters is accepted
            - With the quantifier {2}, we can check for two 't' characters

        - ( [hH] [tT]{2} [pP] [sS] )
            - in this capture group we are searching for the text `https`
            - with the character set `[]`, we can pass in both the capital and lower case
                letters so any variations of the 4 letters is accepted
            - With the quantifier {2}, we can check for two 't' characters

        - ( [fF] [tT] [pP] ) 
            - in this capture group we are searching for the text `ftp`
            - with the character set `[]`, we can pass in both the capital and lower case
                letters so any variations of the 3 letters is accepted

    - Each of these Capture Groups are seperated by a '|' (Alternator symbol) which acts as
        a boolean 'OR'. This means that as long as 1 of these 3 Capture Groups is present,
        it will be found.
```

```
TLDR; looks for `://` 

2.  :[\/]{2}
    - This expression searches for the characters ' :// '
    - The first colon symbol ':' searches for a singular instance of a colon ':'
    - in this character set we are looking for a forward slash symbol '/'
        because forward slash '/' is a special character we need to use the
        backslash symbol '\' to let the regex know that we are searching for this
        specific character and that we are not ending the regex.
    - The quantifier {2} tells the regex to look for 2 backslash symbols '/'.
```
Putting these 2 groups together we get a regex that looks for the following:

`http://`, `https://`, or `ftp://`

By adding a question mark `?` after this statement we make this block __optional__.

___Part 2:___

The second portion that we will look at is the `Domain` segment with domain name + port number:

`([a-zA-Z0-9\-\.]+\.[a-zA-Z]{1,4})(:[0-9]+)?\/?`

We can further break this down into 2 different sets of information as well:

```
TLDR; looks for any length text followed by a period and any 4 letters
(ie. www.google.com)

1. [a-zA-Z0-9\-\.]+   \.   [a-zA-Z]{1,4}
    - The first character set '[]' looks for any lower or upper case letter,any number,
        dash symbol '-', or period symbol '.'
    - the quantifier '+' looks for more than 1 value from the previous character set
    - the back slash symbol '\' makes the regex look for the period symbol '.'
    - the second character set '[]' looks for any lower case or capital letter
    - the quantifier '{}' sets a range BETWEEN 1 and 4 characters that it is looking for
        so it would only match values that are 2 or 3 characters long. 
```
```
TLDR; looks for a colon ':' followed by any length of numbers and forward slash symbol
'/'. Both parts are optional. (this is a port number);
(ie. :80/  or  :3001/ or  /  )

2. (:[0-9]+)?  \/?
    - the first character just looks for a colon ':'
    - the first character set looks for any length of numbers from 0-9
    - the question mark '?' makes the first character set an option group
    - the backslash tells the regex to look for a forward slash symbol '/' rather than
        ending the regex.
```
Putting these 2 groups together we get a regex that looks for the domain name and port number such as:

`www.google.com:443/` or `www.google.com/` assuming no portnumber is passed

___Part 3:___

The third part of this regex statement is the pathing or any additional parameters/keys that are passed by the url:

`([a-zA-Z0-9\-\._\?\,\'\/\\\+&;%\$#\=~]*)`

This section may look complicated but the information presented is actually very simple.
```
TLDR; look for all characters of any length
(ie. courses/2188/assignments/38653?module_item_id=749152)

([a-zA-Z0-9\-\._\?\,\'\/\\\+&;%\$#\=~]*)
    - the character set signifies all the characters to look for
        - `a-z` looks for all lower case letters
        - 'A-Z' looks for all upper case letters
        - `0-9` looks for all digits
        - the following set of values all all special characters that are escaped using a
            back slash '\', telling the regex to look for that specific character rather
            than their special function.
    - the character set is followed by a star symbol '*' which tells the regex to look for
        any number of characters from the characterset 
```
This is pretty much a find all values statement so that it can look for anything after the domain name such as the following paths:

`watch?v=rhzKDrUiJVk` or `terms/a/acidtest.asp`

___Part 4:___

The fourth and final part of this regex is the flags that come after the statement is made:

`g` 

This flag takes the Regex and then applies a global search function onto the statement.

Take the regex without the flag:

`/((([hH][tT]{2}[pP])|([hH][tT]{2}[pP][sS])|([fF][tT][pP])):[\/]{2})?([a-zA-Z0-9\-\.]+\.[a-zA-Z]{1,4})(:[0-9]+)?\/?([a-zA-Z0-9\-\._\?\,\'\/\\\+&;%\$#\=~]*)/`

The default behavior of this is to search for the very first instance of a valid statement and then stop.

![___PICTURE OF CODE IN ACTION___]()

By adding the `g` flag (global flag), we tell the regex to search for every instance that this statement is fulfilled.

![___PICTURE OF CODE IN ACTION___]()


## Author
Ahneb is the author of this gist.
He is currently learning about webdev and made this post to help himself learn how to use and use regular expressions.

[Github](https://github.com/Ahneb)
