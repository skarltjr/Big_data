- http://recordingbetter.com/python/2017/05/23/Python-%EC%A0%95%EA%B7%9C%ED%91%9C%ED%98%84%EC%8B%9D
```
# b~d까지의 문자를 모두 a로 치환하고 싶다.
# replace를 통해 바꾸면 b다 찾고 바꾸고 c 다찾고 ...~
# 정규표현식을 다루는 모듈 re를 사용
import re
txt1 = "life is too short, you need python"
txt2 = "my baby is my life"

# match는 맨 처음부터 일치하는 경우만 찾아준다
print(re.match('life',txt1)) # <re.Match object; span=(0, 4), match='life'>
print(re.match('life',txt2)) # none -> not match

# search는 어디에 있든지 찾아준다
print(re.search('life',txt1)) 
print(re.search('life',txt2)) 

#group 함수를 통해서 매칭된 값을 얻을 수 있다.
match = re.search('life',txt1)
print(match.group()) # match는 무엇을 매칭한것인지를 알 수 있다.
print(match.span()) # txt1에서 life를 re.search했을 때 어디서부터 어디까지인지 0부터 4번전까지

# 대소문자 구분없이 찾고싶다  selection  Life|life
print(re.search("Life|life",txt1).group())

# 공백까지 포함해서 찾고자하는 경우
txt3 = "   life is life   "
print(re.search("life",txt3))
print(re.search("\s*life\s*",txt3))

# match와 search는 맨 처음 등장한 한 번만 찾아준다.
# 모두 찾고싶다면 findall
print(re.findall("life",txt3))
```

```
# 메타문자와 정규표현식
import re
str ="ABBA"

# .은 임의의 한 문자
print(re.search('A.A',str)) # -> 매칭 x
print(re.search('A..A',str)) # -> 매칭 o A와 A사이에 임의의 두 문자 존재하니까

# *은 0개 이상의 일치하는 문자
print(re.search('AB*',str))
print(re.search('AB*','X-MAN')) # -> A뒤에B가0개이상이냐?-> o -> A뒤에 B가0개잖아 지금

# +는 적어도 1개 이상 일치하는 문자
print(re.search('AB+','A'))
print(re.search('AB+','ABBBA'))
```

```
import re

# AI로 시작하는 과목 코드만 떼어와보자
# AI숫자 -> 과목코드 
# AIandsociety는 제외시키면서
text = """
CS101 Python
AI101 AIandsociety
AI102 PyTorch
CS102 TeamProject
"""

# \d는 숫자만해당
print(re.findall("AI\d+",text))
```

```
# sub함수를 통해 문자 대체 가능
import re

str = "today's melon chart #1 is IU"
print(re.sub('IU','kiseok',str))
```

```
# nltk 

# 토큰화
# 정제
# 정규화 순으로 전처리한다

import wikipedia
import nltk
from nltk.tokenize import word_tokenize
# punkt라는 데이터셋이 필수
nltk.download('punkt')

#토큰화 예시
wiki=wikipedia.page('Big data').content.split(".")[0]
print(wiki)
print(word_tokenize(wiki))
```
- ![image](https://user-images.githubusercontent.com/62214428/159698201-64b5dc35-363b-4fd1-8143-15e9458b3b8a.png)

```
# 정제 : 갖고 있는 코퍼스로부터 노이즈 데이터를 제거
# ex) stop word 제거 등

# 정규화 : 표현 방법이 다른 단어들을 통합시켜 같은 단어로 만든다
# ex) US와 USA는 결국 같지만 다른 단어 -> 통합
# 대소문자 통합 등 
```

```
import wikipedia
import nltk
from nltk.tokenize import word_tokenize
# punkt라는 데이터셋이 필수
nltk.download('punkt')


wiki=wikipedia.page('Big data').content.split(".")[0]
print(wiki)
tokens = word_tokenize(wiki)
from nltk.tag import pos_tag
nltk.download('averaged_perceptron_tagger')
# 단순히 공백 등으로 나누는것말고 단어의 품사를 태깅할수도있다
print(pos_tag(tokens)) # 각 단어의 품사 파악

nouns = [x for x in pos_tag(tokens) if x[1] == "NN"]
print(nouns)
```
```
문자 파악해보기
import string
printable = string.printable

# 출력 가능한 모든 문자 출력
print(printable)

# 각 정규표현식의 패턴 문자 확인
print('\w', re.findall('\w', printable))
print('\W', re.findall('\W', printable))
print('\d', re.findall('\d', printable))
print('\D', re.findall('\D', printable))
print('\s', re.findall('\s', printable))
print('\S', re.findall(r'\S', printable))
print('\\b', re.findall(r'\b', printable))
print('\B', re.findall(r'\B', printable))
```
