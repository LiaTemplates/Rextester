<!--

author:   Andre Dietrich
email:    dietrich@ivs.cs.uni-magdeburg.de
version:  1.0.0
language: de_DE
narrator: Deutsch Female

script:   https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js

@R:       31

@eval
<script>
var result = null;
var error  = false;

$.ajax ({
    url: "https://crossorigin.me/http://rextester.com/rundotnet/api",
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
Template for executing code snippets in 26 different programming languages


## *R-Interaktiv*<!-- class = "animated infinite bounce" style = "color: red;" -->

```R
require(stats) # for lowess, rpois, rnorm
plot(cars)
lines(lowess(cars))

plot(sin, -pi, 2*pi) # see ?plot.function

## Discrete Distribution Plot:
plot(table(rpois(100, 5)), type = "h", col = "red", lwd = 10,
     main = "rpois(100, lambda = 5)")

## Simple quantiles/ECDF, see ecdf() {library(stats)} for a better one:
plot(x <- sort(rnorm(47)), type = "s")
points(x, cex = .5, col = "dark red")
```
@eval(@R,1)
