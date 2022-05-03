# LAB REPORT 2 WEEK 4

## **ERROR #1**

![Error1](https://gyazo.com/7f7bd65c1f73eb05877447d4303d2e53.png)

[**Link to fail-inducing input**](https://github.com/davidmyoungg/markdown-parser/commit/b7c8355f1f5b1f0892d2e40144fffbbad179dcf3)

![**Symptom**](https://gyazo.com/194b832486d82fe4720e1309a33b8949.png)

The relationship between the error and the code itself is because the Markdown only checks if the testfile has a valid line after it enters the while loop. Because of this it produces an infinite loop because the error lies inside the while function. In order to fix this we have to check if a valid line is present before we enter the while loop.

-----
-----

## **Error #2**

![Error2](https://gyazo.com/00833463a6fbc34d5dc78e4c58d5190e.png)

[**Link to fail-inducing input**](https://github.com/davidmyoungg/markdown-parser/commit/3afe1df3d20ba3163a8079d7e02df67695d52167)

![Symptom2](https://gyazo.com/470cbdc4425109e5430011e4caeb215e.png)

The relationship between the bug and the code is that it assumes that all "[]"s are markdown references. We can see in our symtom that it causes another infinite loop. Because we call the first openbracket outside the while loop, we have no way of testing whether or not this fail-inducing input is really a markdown reference or nt.

-----
----

## **Error #3**

![Error3](https://gyazo.com/a03840adaa0d1e1a76d1865d439c9e77.png)

[**Link to fail-inducing input**](https://github.com/davidmyoungg/markdown-parser/commit/dd6fb2fe84e8426526870be1d7c90c53651964c5)

![Symptom3](https://gyazo.com/1e15e23ef17109690362d22958feb6ef.png)

The relationship between the bug and code is the fact that the code never checks if there is an invalid link. We see in our output that the terminal returns any link that was passed through a markdown reference, regardless if it was real or not. Because of that, we need to change the while loop to have a checking system for fake links. 