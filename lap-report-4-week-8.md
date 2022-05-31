# Lab Report 4 W8

## Links to my Repository:
- [My markdown-parse repository](https://github.com/davidmyoungg/markdown-parser)
- [Reviewed repository](https://github.com/Hiro-229/markdown-parser)

## **Snippet 1 :**

Expected Output:
![Snippet1 EO](https://gyazo.com/0536a25b248cbdd8030cece087c5a858.com)

Because the last three links are valid while the first line is invalid, the output should result to 
```
[`google.com, google.com, ucsd.edu]
```

I turned this code into a test in my MarkdownParseTest.java file
![S1 test](https://gyazo.com/1792dd2948b0e860e5ed4d0606ab2ef2.com)

When I run the test, however, the test produced an error which shows: 
![S1 test output](https://gyazo.com/660f96a2db858b69d6ec094d2505574c.com)

Comparing this output to the implementation I reviewed in Week 7, the corresponding out for Snippet 1 produces:
![S1 reviewed output](https://gyazo.com/f015efb45a1252d8d070cd9986bad9e3.com)



## **Snippet 2:**

Expected Output:
![Snippet2 EO](https://gyazo.com/49b815be08134bd645c1c684b6efb8be.com)

Snippet 2 has multiple links that are valid, including the nested link from line1. However the outer link of line1 isn't valid. So, the expected output should result to
```
[a.com, a.com(()), example.com]
```

My test code for this Snippet contains:
![S2 Test code](https://gyazo.com/f5dddc67d63b21d812c764eac8cedf30.com)
This results in an error that produces:
![S2 Test output](https://gyazo.com/0f570f163e2c197fc246f61c692f119d.com)

Comparing this to the Snippet2 test I reviewed in Week7, that test results in...
![S2 Reviewed test output](https://gyazo.com/4982c69a273ef86dc90e27d5df287c29.com)



## **Snippet 3:**
Expected Output:
![Snippet3 EO](https://gyazo.com/1e0920bd844015e5ddf7e0747e0dc7ca.com)

Based off of this output, we can conclude that only the second line should be produced. Therefore, the expected output should be
```
[https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule]
```


This is the test code I made in my Markdown repository
![S3 Test code](https://gyazo.com/d2cf399d54bf2d9cc3da4d60a4d4cfac.com)

However, it resulted in an error, producing:

![S3 Test output](https://gyazo.com/d2cf399d54bf2d9cc3da4d60a4d4cfac.com)

Comparing this to the test output of the Reviewed code from Weeb 7,
![S3 Reviewed output](https://gyazo.com/eb7d12ccf9b6073cbb0c02f3ca093f3b.com)