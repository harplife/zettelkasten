---
alias: [E-mail Filter Regex]
tags: [natural_language_processing, computer_science, example, guide, HOW-TO]
status: complete
edited: 2022-01-12
---

# E-mail Filter Regex
This should be applied _AFTER_ [[link_filter_regex|Link Filter Regex]].

## Regex
`r'[a-zA-Z0-9_]+@[a-zA-Z0-9]+\.[a-zA-Z]+(?:\.[a-zA-Z]+)?'`

## Explanation
simple enough. It looks for patterns like `chars@chars.chars` or `chars@chars.chars.chars`.

## Result
code :
```python
text = """
이메일로 연락:admin@example.com또는 support@example.com.there is a good wine
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
언제나@오세요.그러면 감사하겠습니다.
아니면 no_reply@example.co.kr
"""

email_regex = r'[a-zA-Z0-9_]+@[a-zA-Z0-9]+\.[a-zA-Z]+(?:\.[a-zA-Z]+)?'
re.findall(email_regex, text)
```

output :
```python
['admin@example.com', 'support@example.com.there', 'no_reply@example.co.kr']
```

## Remaining Problems
- [ ] Allowing formats such as `.co.kr` also allows trailing words at the end of URL (e.g. `google.com.go to here --> google.com.go`)

## Python Script
[[python|Python]] script using the Regex.

```python
def no_dot_end(text):
    while text[-1]=='.':
        text = text[:-1]
    return text

def email_filter(text):
    import re
    
    email_regex = r'[a-zA-Z0-9_]+@[a-zA-Z0-9]+\.[a-zA-Z]+(?:\.[a-zA-Z]+)?'
    split_text = text.split()
    emails = set()
    clean_text = []
    # 문장의 "단어" 하나씩 체크해보며 이메일이 있는지 확인
    for st in split_text:
        if len(st)>0:
            # 이메일이 있다면 텍스트에서 이메일을 제거해줌
            match = re.findall(email_regex, st)
            if match:
                match = no_dot_end(match[0])
                stc = st.replace(match,'email')
                if stc:
                    # 이메일 제거후 남아있는게 있다면 돌려줌
                    clean_text.append(stc)
                emails.add(match)
            # 이메일 없다면 돌려줌
            else:
                clean_text.append(st)
    return ' '.join(clean_text), ' '.join(emails)
```

```python
>>> email_filter('이메일:ben@naver.com으로 연락해주세요')
('이메일:email으로 연락해주세요', 'ben@naver.com')
```