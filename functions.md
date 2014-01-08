[Oracle Database SQL Language Reference][link]
===
[link]: http://docs.oracle.com/cd/E11882_01/server.112/e41084/toc.htm

Functions
===

##ADD_MONTHS
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/add_months.gif)

###Purpose
ADD_MONTHS returns the date date plus integer months. A month is defined by the session parameter NLS_CALENDAR. The date argument can be a datetime value or any value that can be implicitly converted to DATE. The integer argument can be an integer or any value that can be implicitly converted to an integer. The return type is always DATE, regardless of the data type of date. If date is the last day of the month or if the resulting month has fewer days than the day component of date, then the result is the last day of the resulting month. Otherwise, the result has the same day component as date.


##AVG
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/avg.gif)

###Purpose
AVG returns average value of expr.

This function takes as an argument any numeric data type or any nonnumeric data type that can be implicitly converted to a numeric data type. The function returns the same data type as the numeric data type of the argument.

If you specify DISTINCT, then you can specify only the query_partition_clause of the analytic_clause. The order_by_clause and windowing_clause are not allowed.


##COUNT
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/count.gif)

###Purpose
COUNT returns the number of rows returned by the query. You can use it as an aggregate or analytic function.

If you specify DISTINCT, then you can specify only the query_partition_clause of the analytic_clause. The order_by_clause and windowing_clause are not allowed.

If you specify expr, then COUNT returns the number of rows where expr is not null. You can count either all rows, or only distinct values of expr.

If you specify the asterisk (*), then this function returns all rows, including duplicates and nulls. COUNT never returns null.


##INITCAP
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/initcap.gif)

###Purpose
INITCAP returns char, with the first letter of each word in uppercase, all other letters in lowercase. Words are delimited by white space or characters that are not alphanumeric.

char can be of any of the data types CHAR, VARCHAR2, NCHAR, or NVARCHAR2. The return value is the same data type as char. The database sets the case of the initial characters based on the binary mapping defined for the underlying character set. For linguistic-sensitive uppercase and lowercase, refer to [NLS_INITCAP](http://docs.oracle.com/cd/E11882_01/server.112/e41084/functions110.htm#i89841).

This function does not support CLOB data directly. However, CLOBs can be passed in as arguments through implicit data conversion.


##INSTR
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/instr.gif)

###Purpose
The INSTR functions search string for substring. The search operation is defined as comparing the substring argument with substrings of string of the same length for equality until a match is found or there are no more substrings left. Each consecutive compared substring of string begins one character to the right (for forward searches) or one character to the left (for backward searches) from the first character of the previous compared substring. If a substring that is equal to substring is found, then the function returns an integer indicating the position of the first character of this substring. If no such substring is found, then the function returns zero.

* position is an nonzero integer indicating the character of string where Oracle Database begins the search—that is, the position of the first character of the first substring to compare with substring. If position is negative, then Oracle counts backward from the end of string and then searches backward from the resulting position.

* occurrence is an integer indicating which occurrence of substring in string Oracle should search for. The value of occurrence must be positive. If occurrence is greater than 1, then the database does not return on the first match but continues comparing consecutive substrings of string, as described above, until match number occurrence has been found.

INSTR accepts and returns positions in characters as defined by the input character set, with the first character of string having position 1. INSTRB uses bytes instead of characters. INSTRC uses Unicode complete characters. INSTR2 uses UCS2 code points. INSTR4 uses UCS4 code points.

string can be any of the data types CHAR, VARCHAR2, NCHAR, NVARCHAR2, CLOB, or NCLOB. The exceptions are INSTRC, INSTR2, and INSTR4, which do not allow string to be a CLOB or NCLOB.

substring can be any of the data types CHAR, VARCHAR2, NCHAR, NVARCHAR2, CLOB, or NCLOB.

The value returned is of NUMBER data type.

Both position and occurrence must be of data type NUMBER, or any data type that can be implicitly converted to NUMBER, and must resolve to an integer. The default values of both position and occurrence are 1, meaning Oracle begins searching at the first character of string for the first occurrence of substring. The return value is relative to the beginning of string, regardless of the value of position.


##LPAD
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/lpad.gif)

###Purpose
LPAD returns expr1, left-padded to length n characters with the sequence of characters in expr2. This function is useful for formatting the output of a query.

Both expr1 and expr2 can be any of the data types CHAR, VARCHAR2, NCHAR, NVARCHAR2, CLOB, or NCLOB. The string returned is of VARCHAR2 data type if expr1 is a character data type, NVARCHAR2 if expr1 is a national character data type, and a LOB if expr1 is a LOB data type. The string returned is in the same character set as expr1. The argument n must be a NUMBER integer or a value that can be implicitly converted to a NUMBER integer.

If you do not specify expr2, then the default is a single blank. If expr1 is longer than n, then this function returns the portion of expr1 that fits in n.

The argument n is the total length of the return value as it is displayed on your terminal screen. In most character sets, this is also the number of characters in the return value. However, in some multibyte character sets, the display length of a character string can differ from the number of characters in the string.


##MOD
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/mod.gif)

###Purpose
MOD returns the remainder of n2 divided by n1. Returns n2 if n1 is 0.

This function takes as arguments any numeric data type or any nonnumeric data type that can be implicitly converted to a numeric data type. Oracle determines the argument with the highest numeric precedence, implicitly converts the remaining arguments to that data type, and returns that data type.


##NEXT_DAY
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/next_day.gif)

###Purpose
NEXT_DAY returns the date of the first weekday named by char that is later than the date date. The return type is always DATE, regardless of the data type of date. The argument char must be a day of the week in the date language of your session, either the full name or the abbreviation. The minimum number of letters required is the number of letters in the abbreviated version. Any characters immediately following the valid abbreviation are ignored. The return value has the same hours, minutes, and seconds component as the argument date.


##POWER
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/power.gif)

###Purpose
he n1 power. The base n2 and the exponent n1 can be any numbers, but if n2 is negative, then n1 must be an integer.

This function takes as arguments any numeric data type or any nonnumeric data type that can be implicitly converted to a numeric data type. If any argument is BINARY_FLOAT or BINARY_DOUBLE, then the function returns BINARY_DOUBLE. Otherwise, the function returns NUMBER.


##REPLACE
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/replace.gif)

###Purpose
REPLACE returns char with every occurrence of search_string replaced with replacement_string. If replacement_string is omitted or null, then all occurrences of search_string are removed. If search_string is null, then char is returned.

Both search_string and replacement_string, as well as char, can be any of the data types CHAR, VARCHAR2, NCHAR, NVARCHAR2, CLOB, or NCLOB. The string returned is in the same character set as char. The function returns VARCHAR2 if the first argument is not a LOB and returns CLOB if the first argument is a LOB.

REPLACE provides functionality related to that provided by the TRANSLATE function. TRANSLATE provides single-character, one-to-one substitution. REPLACE lets you substitute one string for another as well as to remove character strings.


##ROUND(date)
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/round_date.gif)

###Purpose
ROUND returns date rounded to the unit specified by the format model fmt. This function is not sensitive to the NLS_CALENDAR session parameter. It operates according to the rules of the Gregorian calendar. The value returned is always of data type DATE, even if you specify a different datetime data type for date. If you omit fmt, then date is rounded to the nearest day. The date expression must resolve to a DATE value.


##ROUND(number)
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/round_number.gif)

###Purpose
ROUND returns n rounded to integer places to the right of the decimal point. If you omit integer, then n is rounded to zero places. If integer is negative, then n is rounded off to the left of the decimal point.

n can be any numeric data type or any nonnumeric data type that can be implicitly converted to a numeric data type. If you omit integer, then the function returns the value ROUND(n, 0) in the same data type as the numeric data type of n. If you include integer, then the function returns NUMBER.

ROUND is implemented using the following rules:

1. If n is 0, then ROUND always returns 0 regardless of integer.
2. If n is negative, then ROUND(n, integer) returns -ROUND(-n, integer).
3. If n is positive, then

``
ROUND(n, integer) = FLOOR(n * POWER(10, integer) + 0.5) * POWER(10, -integer)
``

ROUND applied to a NUMBER value may give a slightly different result from ROUND applied to the same value expressed in floating-point. The different results arise from differences in internal representations of NUMBER and floating point values. The difference will be 1 in the rounded digit if a difference occurs.


##TRUNC(date)
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/trunc_date.gif)

###Purpose
The TRUNC (date) function returns date with the time portion of the day truncated to the unit specified by the format model fmt. This function is not sensitive to the NLS_CALENDAR session parameter. It operates according to the rules of the Gregorian calendar. The value returned is always of data type DATE, even if you specify a different datetime data type for date. If you omit fmt, then the default format model 'DD' is used and the value returned is date truncated to the day with a time of midnight. Refer to ["ROUND and TRUNC Date Functions"](http://docs.oracle.com/cd/E11882_01/server.112/e41084/functions255.htm#i1002084) for the permitted format models to use in fmt.


##TRUNC(number)
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/trunc_number.gif)

###Purpose
The TRUNC (number) function returns n1 truncated to n2 decimal places. If n2 is omitted, then n1 is truncated to 0 places. n2 can be negative to truncate (make zero) n2 digits left of the decimal point.

This function takes as an argument any numeric data type or any nonnumeric data type that can be implicitly converted to a numeric data type. If you omit n2, then the function returns the same data type as the numeric data type of the argument. If you include n2, then the function returns NUMBER.


##NVL
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/nvl.gif)

###Purpose

NVL lets you replace null (returned as a blank) with a string in the results of a query. If expr1 is null, then NVL returns expr2. If expr1 is not null, then NVL returns expr1.

The arguments expr1 and expr2 can have any data type. If their data types are different, then Oracle Database implicitly converts one to the other. If they cannot be converted implicitly, then the database returns an error. The implicit conversion is implemented as follows:

* If expr1 is character data, then Oracle Database converts expr2 to the data type of expr1 before comparing them and returns VARCHAR2 in the character set of expr1.

* If expr1 is numeric, then Oracle Database determines which argument has the highest numeric precedence, implicitly converts the other argument to that data type, and returns that data type.


##NVL2
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/nvl2.gif)

###Purpose
NVL2 lets you determine the value returned by a query based on whether a specified expression is null or not null. If expr1 is not null, then NVL2 returns expr2. If expr1 is null, then NVL2 returns expr3.

The argument expr1 can have any data type. The arguments expr2 and expr3 can have any data types except LONG.

If the data types of expr2 and expr3 are different, then Oracle Database implicitly converts one to the other. If they cannot be converted implicitly, then the database returns an error. If expr2 is character or numeric data, then the implicit conversion is implemented as follows:

* If expr2 is character data, then Oracle Database converts expr3 to the data type of expr2 before returning a value unless expr3 is a null constant. In that case, a data type conversion is not necessary, and the database returns VARCHAR2 in the character set of expr2.

* If expr2 is numeric data, then Oracle Database determines which argument has the highest numeric precedence, implicitly converts the other argument to that data type, and returns that data type.


##NULLIF
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/nullif.gif)

###Purpose

NULLIF compares expr1 and expr2. If they are equal, then the function returns null. If they are not equal, then the function returns expr1. You cannot specify the literal NULL for expr1.

If both arguments are numeric data types, then Oracle Database determines the argument with the higher numeric precedence, implicitly converts the other argument to that data type, and returns that data type. If the arguments are not numeric, then they must be of the same data type, or Oracle returns an error.

The NULLIF function is logically equivalent to the following CASE expression:

``
CASE WHEN expr1 = expr2 THEN NULL ELSE expr1 END
``

##COALESCE
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/coalesce.gif)

###Purpose

COALESCE returns the first non-null expr in the expression list. You must specify at least two expressions. If all occurrences of expr evaluate to null, then the function returns null.

Oracle Database uses **short-circuit evaluation**. The database evaluates each expr value and determines whether it is NULL, rather than evaluating all of the expr values before determining whether any of them is NULL.

If all occurrences of expr are numeric data type or any nonnumeric data type that can be implicitly converted to a numeric data type, then Oracle Database determines the argument with the highest numeric precedence, implicitly converts the remaining arguments to that data type, and returns that data type.

This function is a generalization of the NVL function.

You can also use COALESCE as a variety of the CASE expression. For example,

``
COALESCE(expr1, expr2)
``

is equivalent to:

``
CASE WHEN expr1 IS NOT NULL THEN expr1 ELSE expr2 END
``

Similarly,

``
COALESCE(expr1, expr2, ..., exprn)
``

where n >= 3, is equivalent to:

``
CASE WHEN expr1 IS NOT NULL THEN expr1 
   ELSE COALESCE (expr2, ..., exprn) END
``

##DECODE
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/decode.gif)

###Purpose

DECODE compares *expr* to each *search* value one by one. If *expr* is equal to a *search*, then Oracle Database returns the corresponding *result*. If no match is found, then Oracle returns *default*. If *default* is omitted, then Oracle returns null.

The arguments can be any of the numeric types (NUMBER, BINARY_FLOAT, or BINARY_DOUBLE) or character types.

* If *expr* and *search* are character data, then Oracle compares them using nonpadded comparison semantics. *expr*, *search*, and *result* can be any of the data types CHAR, VARCHAR2, NCHAR, or NVARCHAR2. The string returned is of VARCHAR2 data type and is in the same character set as the first *result* parameter.

* If the first *search-result* pair are numeric, then Oracle compares all *search-result* expressions and the first *expr* to determine the argument with the highest numeric precedence, implicitly converts the remaining arguments to that data type, and returns that data type.

The *search*, *result*, and *default* values can be derived from expressions. Oracle Database uses **short-circuit evaluation**. The database evaluates each *search* value only before comparing it to *expr*, rather than evaluating all *search* values before comparing any of them with *expr*. Consequently, Oracle never evaluates a *search* if a previous *search* is equal to *expr*.

Oracle automatically converts *expr* and each *search* value to the data type of the first *search* value before comparing. Oracle automatically converts the return value to the same data type as the first *result*. If the first *result* has the data type CHAR or if the first *result* is null, then Oracle converts the return value to the data type VARCHAR2.

In a DECODE function, Oracle considers two nulls to be equivalent. If *expr* is null, then Oracle returns the *result* of the first *search* that is also null.

The maximum number of components in the DECODE function, including *expr*, *searches*, *results*, and *default*, is 255.

##CONCAT
###Syntax
![NVL_IMA](http://docs.oracle.com/cd/E11882_01/server.112/e41084/img/concat.gif)

###Purpose
CONCAT returns char1 concatenated with char2. Both char1 and char2 can be any of the data types CHAR, VARCHAR2, NCHAR, NVARCHAR2, CLOB, or NCLOB. The string returned is in the same character set as char1. Its data type depends on the data types of the arguments.

In concatenations of two different data types, Oracle Database returns the data type that results in a lossless conversion. Therefore, if one of the arguments is a LOB, then the returned value is a LOB. If one of the arguments is a national data type, then the returned value is a national data type. For example:

* CONCAT(CLOB, NCLOB) returns NCLOB
* CONCAT(NCLOB, NCHAR) returns NCLOB
* CONCAT(NCLOB, CHAR) returns NCLOB
* CONCAT(NCHAR, CLOB) returns NCLOB

This function is equivalent to the concatenation operator (||).