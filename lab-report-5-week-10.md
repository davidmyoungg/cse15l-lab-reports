# Lab Report 5 W10

When working on Lab 9, we experimented and learned how to compare different tests
in MarkdownParse using vimdiff. By comparing the two different versions of 
markdown parsers by using vimdiff, our group found many tests that gave different
outputs. 

We will focus on two of the many test cases we found, namely:

- [Test 194](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/194.md)

- [Test 22](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/22.md)

## Test 194:
Given the results provided below, we can see that the left side results to nothing while the right side resulted in a `url` found.

![Test194vimdiff](https://gyazo.com/d10546029fd6ad8e51e85a335ff8658b.com)

Given these test results, if we go back to CommonMark demo, we can see that again, both tests are wrong.

![Test194CommonMark](https://gyazo.com/48f7b306cf9b5d1a4cf6c867f22a2971.com)

The expected result should include all of `my_(url)` instead of providing only the `url`. 

![Test194fix](https://gyazo.com/4829703aec27e9cd09a76453dac30d43.com)

Let's take a look at the code above. The code as it is right now only covers the bare minimum of what a link actually is. Because our initial implementation of checking for links was in the format of `[]()`, there are error when there are nested brackets and parentheses inside. We have to edit the code so that it takes in all the other brackets inside the outer brackets so we dont mess up the code.


## Test 22:
For test22, the results that we got using vimdiff provided below shows the output of our MarkdownParse(left) and the provided MarkdownParse(right).

![Test22vimdiff](https://gyazo.com/d3a9db8318880a5552f3ffe1fc4e5f47.com)

Using CommonMark Demo, we discovered that both results were wrong. We see that the actual result should produce just `bar*`.

![Test22CommonMark](https://gyazo.com/f5fa67b240587287d52259bde9d205fc.com)

The `ti\*tle"` should not be included in the result, but it does so because our current implementation of Markdownparse takes in everything inside the parentheses as a valid argument.

![Test22fix](https://gyazo.com/41fb3bc292b331cc2513059094b0164b.com)

Looking at the code provided above, if the if statement runs, then we return everything starting from the first parentheses until the closing parentheses. We have to edit the code so that if it detects a quotation, we have to ignore everything inside it until the end quotation mark.