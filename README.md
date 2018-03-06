<!--

author:   André Dietrich
email:    andre.dietrich@ovgu.de
version:  1.0.0
language: de_DE
narrator: Deutsch Female

script:   https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js

@NASM:        15
@C_sharp:      1
@CPP:          7
@clang_CPP:   27
@visual_CPP:  28
@clang_C:     26
@visual_C:    29
@LISP:        18
@D:           30
@F_sharp:      3
@GO:          20
@Haskell:     11
@Java:         4
@JavaScript:  17
@LUA:         14
@NodeJS:      23
@Octave:      25
@ObjectiveC:  10
@Pascal:       9
@Perl:        13
@PHP:          8
@Prolog:      19
@Python:       5
@Python3:     24
@evalR:       @eval(31)
@Ruby:        12
@Scala:       21
@Scheme:      22
@SQL_server:  16
@MySQL:       33
@Oracle:      35
@PostgreSQL:  34
@TCL:         32
@BASIC:        2
@ClientSide:  36
@Swift:       37
@BASH:        38
@ADA:         39
@Erlang:      40
@Elixir:      41
@OCaml:       42
@Kotlin:      43
@Brainfuck:   44
@Fortran:     45

@eval
<script>
var result = null;
var error  = false;

$.ajax ({
    url: "http://rextester.com/rundotnet/api",
    type: "POST",
    async: false,
    data: { "LanguageChoice": "@0",
            "Program": `{X}`,
            "Input": "",
            "CompilerArgs" : ""}
    }).done(function(data) {
        if (data.Errors == null) {
            result = data.Result;

            $('#Files').empty();

            if (data.Files != null) {
                for (var key in data.Files)
                {
                    var img_div = $(document.createElement('div'));
                    var img = $(document.createElement('img'));

                    img.attr('src', "data:image/png;base64," + data.Files[key]).height(600).width(700);

                    img.appendTo(img_div);
                    img_div.appendTo($('#Files@1'));
                }
            }
        } else {
            error  = true;
            result = data.Errors;
        }
    }).fail(function(data, err) {
        error = true;
        result = JSON.stringify(err);
    });

if (error)
    throw {message: result};
else
    result;
</script>

<div id="Files@1"> </div>
@end

-->

# rextester_template
Template for executing code snippets in 45 different programming languages.

See the rendered version [here](https://liascript.github.io/?https://raw.githubusercontent.com/liaScript/rextester_template/master/README.md)

## __Python2__

```python
for i in range(10):
    print i
```
@eval(5,0)


## *R-Interaktiv*

```R
require(stats) # for lowess, rpois, rnorm
plot(cars)
lines(lowess(cars))

plot(sin, -pi, 2*pi) # see ?plot.function

## Discrete Distribution Plot:
plot(table(rpois(100, 5)), type = "h", col = "red", lwd = 10, main = "rpois(100, lambda = 5)")

## Simple quantiles/ECDF, see ecdf() {library(stats)} for a better one:
plot(x <- sort(rnorm(47)), type = "s")
points(x, cex = .5, col = "dark red")
```
@eval(31,1)

## test

```@ggg 12, 12, 12

this is a test

```


@ggg(12, 12, 12)@@

this is a test

@@@@@end

