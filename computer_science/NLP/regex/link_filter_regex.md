---
alias: [Link Filter Regex]
tags: [natural_language_processing, computer_science, example, guide, HOW-TO]
status: complete
edited: 2022-01-14
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

### Updated (2021/01/14)
`r'\b((?:https?://|www\.)(?:[0-9a-zA-Z]+\.?)+(?:(?:/[\w@\-]+)?)+(?:\.\w+)?(?:/)?(?:/?\?\w+=[\w%.+\-_]+(?:(?:&\w+=(?:[\w%.+\-_]+)?)?)+)?)'`

Fixed:
- Query can now accept empty value (e.g. `?query=this&empty=&foo=bar`)

### Updated (2021/01/17)
`r'\b((?:https?://|www\.)(?:[0-9a-zA-Z]+\.?)+(?:(?:/[\w@\-%=]+)?)+(?:\.\w+)?(?:/?\?\w+=[\w%.+\-_=\|]+(?:(?:&\w+=(?:[\w%.+\-_=\|]+)?)?)+)?(?:#\w+)?)'`

Fixed:
- Path now allows Korean (e.g. `./이길로/간다네`)
- Query now allows `=` and `|`
- Content Link `#` added
- File Path with empty filename is not allowed (e.g. `../.html`)
- Path now allows `=` (definitively weird, but this [Amazon URL](https://www.amazon.com/uxcell-GX16-4-Aviation-Connecting-Connector/dp/B00GYUUHVW/ref=pd_sbs_23_1?_encoding=UTF8&pd_rd_i=B00GYUUHVW&pd_rd_r=6e83ea7c-6700-11e8-bb86-fd49c2c21015&pd_rd_w=kZxqA&pd_rd_wg=YARMP&pf_rd_i=desktop-dp-sims&pf_rd_m=ATVPDKIKX0DER&pf_rd_p=5825442648805390339&pf_rd_r=D36QZXGKWKE4TKVN94NA&pf_rd_s=desktop-dp-sims&pf_rd_t=40701&psc=1&refRID=D36QZXGKWKE4TKVN94NA) has this)

New Problem:
- Fixing empty filename issue conflicts with catching slash at the end of URL (e.g. `www.google.com/`), because allowing slash at the end would also allow `../index.html/`. That's no bueno.

### Updated (2021/01/18)
`r'(?:https?:\/\/|www\.)(?:[0-9a-zA-Z]+\.?)+(?:(?:\/[\w@\-%=]+)?)+(?:\.\w+)?(?:\/?\?\w+=[\w%.+\-_=\|]+(?:(?:&\w+=(?:[\w%.+\-_=\|]+)?)?)+)?(?:#\w+)?'`

Fixed:
- Apparently `/` needs to be escaped. Replaced them with `\/`
- Seems `\b` was unnecessary, it's more useful without (`this sitewww.google.com` can't be caught with `/b`)

## Explanation
![[link_filter_regex_guide.svg]]
(Updated 2022/01/18)

## Result
code :
```python
text = """
http://example.com <-- 1) http 체크
https://example.com <-- 2) https 체크
www.example.com <-- 3) www 체크
http://www.example.com <-- 4) http + www 체크
this link.www.example.com <-- 5) URL 앞에 이상한게 붙어있는 경우 체크
www.google.com/search?q=computer+science <-- 6) 경로 및 쿼리 체크
www.example.com/path/go?foo=bar&kung=fu&pan=da <-- 7) 쿼리 연장 체크
map.naver.com <-- 이런 형식의 URL은 필터가 불가능함.
www.example.com/?foo=bar <-- 8) / 뒤에 바로 쿼리가 있는 경우 체크
www.example.com/path/?query=%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94 <-- 9) "한국어" 쿼리 체크
www.example.com/path?query=한국어+..+english&foo=this|that&bar=it-is_ <-- 10) 한국어 및 특수기호 체크
www.example.co.kr으로 오세요 <-- 11) domain extension은 영어만 취급
www.example.com/%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94/path/ <-- 12) 한국어 path 체크
www.이건어쩔수없네요.com <-- 한국어 도메인은 제외
www.example.com/path-like-this/ <-- 13) path 특수기호 체크
www.example.com/path/index.html visit here <-- 14) 파일 경로 체크
www.example.com/index.visit here <-- 14번의 문제(1): URL 뒤에 단어가 붙는 경우, domain ext로 취급해버림
www.example.com/.it is wonderful <-- 15) "가짜" 파일 경로 체크 방지
www.example.com/path?query=this&empty=&foo=bar <-- 16) 빈 쿼리 체크
www.example.com/?query=this&foo==&bar== <-- 17) 쿼리에 =가 있는 경우 체크
www.example.com/path/?query=this#index <-- 18) 콘텐츠 #영역 기능 체크
www.example.com/path/ref=123142?query=this <-- 19) path에 =가 있는 경우 체크
"""

url_regex = r'(?:https?:\/\/|www\.)(?:[0-9a-zA-Z]+\.?)+(?:(?:\/[\w@\-%=]+)?)+(?:\.\w+)?(?:\/?\?\w+=[\w%.+\-_=\|]+(?:(?:&\w+=(?:[\w%.+\-_=\|]+)?)?)+)?(?:#\w+)?'
re.findall(url_regex, text)
```

output :
```python
['http://example.com',
 'https://example.com',
 'www.example.com',
 'http://www.example.com',
 'www.example.com',
 'www.google.com/search?q=computer+science',
 'www.example.com/path/go?foo=bar&kung=fu&pan=da',
 'www.example.com/?foo=bar',
 'www.example.com/path/?query=%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94',
 'www.example.com/path?query=한국어+..+english&foo=this|that&bar=it-is_',
 'www.example.co.kr',
 'www.example.com/%EC%95%88%EB%85%95%ED%95%98%EC%84%B8%EC%9A%94/path',
 'www.example.com/path-like-this',
 'www.example.com/path/index.html',
 'www.example.com/index.visit',
 'www.example.com',
 'www.example.com/path?query=this&empty=&foo=bar',
 'www.example.com/?query=this&foo==&bar==',
 'www.example.com/path/?query=this#index',
 'www.example.com/path/ref=123142?query=this']
```

## Remaining Problems
- [x] Can't handle Query Parameter that comes at index level (e.g. `www.ex.com/?foo=bar`)
    - Fixed with 2021/01/12 Update
- [ ] Can't handle URLs without schemes (e.g. `google.com`). Although fixable, this opens up a whole another issue of grabbing false-positive links.
- [ ] Typos that connect two URLs, like `www.google.comwww.yahoo.com` cannot be handled


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
    
    url_regex = r'(?:https?:\/\/|www\.)(?:[0-9a-zA-Z]+\.?)+(?:(?:\/[\w@\-%=]+)?)+(?:\.\w+)?(?:\/?\?\w+=[\w%.+\-_=\|]+(?:(?:&\w+=(?:[\w%.+\-_=\|]+)?)?)+)?(?:#\w+)?'
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
output:
('Take a look at link/.it is wonderful', 'http://www.myblog.com/posts')
```