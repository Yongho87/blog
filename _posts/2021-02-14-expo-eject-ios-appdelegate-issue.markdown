---
layout: single
author: Yongho
title:  "Problem & Solution #1 - expo eject could not locate a valid AppDelegate at root issue"
date:   2021-02-14 10:17:41 +0900
---


## TL;DR
There are two possible solutions depending on your case.

1. delete `android` and `ios` folders before `expo eject`
2. In `app.json`, change your `expo.name` field value to English value.   

## a little longer version
I encountered this weird issue and wasted about 5 hours on Saturday. There are few google search results relevant to this. The only solution you can get from google is to delete the existing `android` and `ios` folders from the official expo github issue repository. 

But I didn't even have the folders before ejecting expo. So the solution didn't work for my case. 

The real soluition for me was very simple. If you assigned your expo.name field value as non-english character in `app.json`, that is the real culprit. You should **change the field value in English** for `expo eject` to work.

That's it. 

Hope anyone can get a bit of help from my lost 5 hours.


<hr>


React Native를 expo를 통해 개발하다 expo eject할때가 되어 명령을 수행했는데 제목과 같은 문제에 봉착.

다른 프로젝트에서는 아무 문제 없이 되었는데 특정 프로젝트에서 위에 문제가 생기는게 이상하여 이런 저런 방법을 통해 해결해보려고 하다가 의미없이 약 5시간은 날린것 같다. 

어이없게도 해결책은 다음과 같이 굉장히 간단하다.
- expo 설정을 해주는 `app.json`에 **expo.name field가 한글**로 되어 있으면 위의 문제가 발생하므로 이것을 영어로 변경해준다.

근본적인 원인은 expo에서 expo.name을 기반으로 `ios`와 `android`폴더를 생성해주는데 이 안에 저 필드이름을 기반으로 하는 서브폴더들이 생기게 된다. 이때 한글이라면 인식을 못하여 폴더를 생성해주지 못한다. 이런 저런 디버깅을 통해 힌트를 발견하고 겨우 해결했다. 윈도우10도 안되고 macOS Big Sur 11.0.1에서도 안됨.

구체적인 것은 모르겠지만 expo내의 자동으로 폴더 생성하는 코드가 utf-8로 되어 있지 않아 한글을 처리하지 못하는 것으로 보인다. 우리나라가 first world 나라가 아닌 것을 다시 한번 상기시켜주는 문제였음.

혹시 비슷한 문제에 봉착하는 사람들은 구글링이 이 글을 상위에 랭크시켜줄것 같으니 이것을 보고 도움이 되었으면 합니다. 

- 이 문제말고도 다른 문제 때문에 동일한 에러가 나오는 경우가 있는데 이러한 상황에서의 근본문제는 기존 폴더에 `ios`와 `android`폴더가 존재하기 때문이라고 한다. (expo github issue에 찾으면 나옴) 따라서 해결책은 이 폴더들을 삭제하고 `expo eject`을 해주면 됩니다.









