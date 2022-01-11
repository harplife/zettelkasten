---
alias: [Link Filter Regex]
tags: [natural_language_processing, computer_science, example, guide, HOW-TO]
status: complete
edited: 2022-01-11
---

# Link Filter Regex
This is the first legit regex I've ever made.

## Motivation
I've been trying to get rid of links in texts (while working on Sentimental Analysis AI).

I've tried several Regex examples on the web but it didn't quite work right or it didn't work at all. Since I couldn't understand Regex very well, trying to fix them was not the right answer.

Eventually, I thought I might as well learn Regex and try to build my own Link Filter Regex. And here we are.

## Regex
`r'\b((?:https?://|www\.)(?:\w+\.?)+(?:(?:/\w+)?)+(?:\.\w+)?(?:\?\w+=[\w%.+]+(?:&\w+=[\w%.+]+)?)?)'`

## Explanation
![[link_filter_regex_guide.svg]]

## Result
code :
```python
text = """
https://example.com/python/learn/regex.html
http://www.youtu.be/awefawlin.
check it out.www.naver.me https://www.google.com/search?q=computer+science and
that https://goog.le/search?query=hi
https://goog.le/search?query=hi&key=doit
map.naver.com
https://www.example.com/python/python_regex.asp?query=%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94
https://www.example.com/python/python_regex.asp?query=한국어+..+english
"""

url_regex = r'\b((?:https?://|www\.)(?:\w+\.?)+(?:(?:/\w+)?)+(?:\.\w+)?(?:\?\w+=[\w%.+]+(?:&\w+=[\w%.+]+)?)?)'
re.findall(url_regex, text)
```

output :
```python
['https://example.com/python/learn/regex.html',
 'http://www.youtu.be/awefawlin',
 'www.naver.me',
 'https://www.google.com/search?q=computer+science',
 'https://goog.le/search?query=hi',
 'https://goog.le/search?query=hi&key=doit',
 'https://www.example.com/python/python_regex.asp?query=%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94',
 'https://www.example.com/python/python_regex.asp?query=한국어+..+english']
```