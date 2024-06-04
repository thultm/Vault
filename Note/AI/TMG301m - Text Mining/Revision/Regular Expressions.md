> Regular Expressions, often abbreviated as regex, are sequences of characters that serve as powerful tools for defining search patterns within text data.
# These patterns allow for
- Searching: Regex enables the identification of specific patterns within text, allowing for efficient data extraction and analysis.
- Manipulating: Regex can modify or rearrange text by replacing or transforming substrings based on specified patterns.
- Validating: Regular expressions assist in verifying whether text adheres to a predefined pattern or format, such as checking if an email address is correctly structured.

# Syntax
`^` (Caret): The start of a line or string. It's used to anchor patterns at the beginning.
`$` (Dollar Sign): The dollar sign indicates the end of a line or string. It's used to anchor patterns at the end.
`.` (Dot): The dot matches any single character except a newline. It's a wildcard that can be used to represent any character.
## Quantifiers
`*`(Asterisk): The asterisk matches the preceding character or group zero or more times. ($\geq0$)
`+` (Plus): The plus matches the preceding character or group one or more times. ($\geq1$)
`?` (Question Mark): The question mark matches the preceding character or group zero or one time. (0 or 1)
`{m}`: Curly braces with a specific number (m) indicate exactly m occurrences of the preceding character or group. (x{3} matches "xxx".)
`{m,n}`: Curly braces with a range (m and n) specify a minimum of m occurrences and a maximum of n occurrences of the preceding character or group. (o{2,4} matches "oo", "ooo", and "oooo")
## Groups and Capturing
- Groups in regular expressions, created using parentheses `()`, serve two main purposes:
	- Capturing: Groups allow you to *capture and extract portions of the matched text for further use.*
	- Grouping: Groups help to *define the scope of quantifiers and alternations.*
- Non-Capturing Groups `(?: )` are used when you *need to group parts of a pattern but don't want to capture the matched text*. They don't store the captured value for retrieval.
`re.findall()`: used to find all occurrences of the pattern in the text and return them as a list.