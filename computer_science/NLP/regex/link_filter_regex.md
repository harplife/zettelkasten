---
alias: [Link Filter Regex]
tags: [natural_language_processing, computer_science, example, guide, HOW-TO]
status: complete
edited: 2022-01-12
---

# Link Filter Regex
This is the first legit regex I've ever made.

## Motivation
I've been trying to get rid of links in texts (while working on Sentimental Analysis AI).

I've tried several Regex examples on the web but it didn't quite work right or it didn't work at all. Since I couldn't understand Regex very well, trying to fix them was not the right answer.

Eventually, I thought I might as well learn Regex and try to build my own Link Filter Regex. And here we are.

## Regex
`r'\b((?:https?://|www\.)(?:\w+\.?)+(?:(?:/\w+)?)+(?:\.\w+)?(?:\?\w+=[\w%.+]+(?:&\w+=[\w%.+]+)?)?)'`

### Updated (2021/01/12)
`r'\b((?:https?://|www\.)(?:[0-9a-zA-Z]+\.?)+(?:(?:/[\w@\-]+)?)+(?:\.\w+)?(?:/)?(?:/?\?\w+=[\w%.+\-_]+(?:(?:&\w+=[\w%.+\-_]+)?)+)?)'`

Fixed:
- Path can have `@.-` (not yet confirmed with a working URL).
- Query can have `%.+-_`
- Regex for Query was not repeating (e.g. `./path?query=this&add=that&buy=those`)
- Domain Extension should not have non-alphabet chars (e.g. `www.eg.com으로`)
- Query can start without Path? (e.g. `www.eg.com/?foo=bar`)
- URL can end with `/` (e.g. `www.eg.com/path/`)

New Problem:
- `.` at the end of the link cannot be removed (e.g. `example.com.`, `./path?query=this.`)

## Explanation
![[link_filter_regex_guide.svg]]
(This _regex_ is an old version, but it should suffice for explanation)

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
https://www.example.com/python/python_regex.asp?query=%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94.
https://www.example.com/python/python_regex.asp/?query=한국어+..+english
'howdy https://m.blog.naver.com/PostView.nhn?blogId=ako9417&logNo=221172391948&something=else hgere'
www.google.com/?query=me&foo=bar&soap=bar
www.google.com으로 오세요
www.google.com/o-m-g?query=this_and_that&add=those_are.cheap-I-Think
www.google.com/search?쿼리=이래도될까요
www.이건어쩔수없네요.com
www.google.co.kr
Take a look at http://www.myblog.com/posts/.it is wonderful
"""

url_regex = r'\b((?:https?://|www\.)(?:[0-9a-zA-Z]+\.?)+(?:(?:/[\w@\-]+)?)+(?:\.\w+)?(?:/)?(?:/?\?\w+=[\w%.+\-_]+(?:(?:&\w+=[\w%.+\-_]+)?)+)?)'
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
 'https://www.example.com/python/python_regex.asp?query=%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94.',
 'https://www.example.com/python/python_regex.asp/?query=한국어+..+english',
 'https://m.blog.naver.com/PostView.nhn?blogId=ako9417&logNo=221172391948&something=else',
 'www.google.com/?query=me&foo=bar&soap=bar',
 'www.google.com',
 'www.google.com/o-m-g?query=this_and_that&add=those_are.cheap-I-Think',
 'www.google.com/search?쿼리=이래도될까요',
 'www.google.co.kr',
 'http://www.myblog.com/posts/']
```

## Remaining Problems
- [x] Can't handle Query Parameter that comes at index level (e.g. `www.ex.com/?foo=bar`)
    - Fixed with 2021/01/12 Update
- [ ] Can't handle URLs without schemes (e.g. `google.com`). Although fixable, this opens up a whole another issue of grabbing false-positive links.


## Python Script
[[python|Python]] script using the Regex.
- It helps with getting rid of `.` at the end of the URL
- Finds hidden URLs (e.g. `w@ww.on@lyfa@ns.co@m`)

```python
def no_dot_end(text):
    while text[-1]=='.':
        text = text[:-1]
    return text

def url_filter(text, invalid='@'):
    import re
    
    url_regex = r'\b((?:https?://|www\.)(?:[0-9a-zA-Z]+\.?)+(?:(?:/[\w@\-]+)?)+(?:\.\w+)?(?:/)?(?:/?\?\w+=[\w%.+\-_]+(?:(?:&\w+=[\w%.+\-_]+)?)+)?)'
    split_text = text.split()
    links = set()
    clean_text = []
    # 문장의 "단어" 하나씩 체크해보며 링크가 있는지 확인
    for st in split_text:
        if len(st)>0:
            # 링크인데 특수기호로 불분명하게 만든 경우, 특수기호 제거 후 링크가 있는지 확인
            if invalid in st:
                hidden_match = re.findall(url_regex, st.replace(invalid, ''))
                if hidden_match:
                    # 링크임. 넣어줌.
                    hidden_match = no_dot_end(hidden_match[0])
                    links.add(hidden_match)
                else:
                    # 링크가 아니니 돌려줌.
                    clean_text.append(st)
            else:
                # 링크가 있다면 텍스트에서 링크를 제거해줌
                match = re.findall(url_regex, st)
                if match:
                    match = no_dot_end(match[0])
                    stc = st.replace(match,'link')
                    clean_text.append(stc)
                    links.add(match)
                # 링크가 없다면 돌려줌
                else:
                    clean_text.append(st)
    return ' '.join(clean_text), ' '.join(links)
```

```python
>>> url_filter('Take a look at http://www.myblog.com/posts/.it is wonderful')
('Take a look at link.it is wonderful', 'http://www.myblog.com/posts/')
```