---
title: "Keychron Q1 Knob 사용기 1"
tags: [keyboard, C, Linux] # 태그 입력
categories:
mathjax: false # MathJax 사용을 위한 태그
comments: true
published: true
---

# Intro
17년 부터 사용하고 있었던 국내 ABKO사의 무접점 키보드 K985p v2가 최근 고장을 일으키는 바람에
새 키보드를 마련할 필요가 생겼다. 키를 입력하는 기능상의 문제는 없었지만 기판의 LED가 어느 순간
전체 소등이 되어버리는 일이 발생했다. 전용 소프트웨어로 초기화를 시켜봤으나 LED에 불이 들어오지
않았다. 따라서 여럿 키보드를 찾아보던 도중, 주로 맥 전용 키보드를 만드는 **Keychron** 이라는 곳에서
키캡, 그리고 키보드의 축까지 완전 커스텀할 수 있는 풀 알루미늄 키보드를 국내에 예약판매 할 예정임을
발견했다. 게다가 마음에 들었던 점은, 텐키리스 키보드보다 더 컴팩트한 75% 배열을 가지고 있고,
심지어는 볼륨 조절이 가능한 '노브'까지 장착이 된 모델이였다. 제품 이름은 **Keychron Q1 Knob version**.
또한 이 키보드의 장점은 오픈소스 키보드 소프트웨어 QMK / VIA를 지원한다는 것이였다. 기존의 독자적인
소프트웨어를 가진 기계식 키보드와는 다르게 정말로 자유로운 커스텀이 가능한 것이 큰 장점으로 보였다.

나는 키캡과 축이 생략된 베어본 모델을 구매하였기 때문에 나머지는 따로 구매했다. 둘 다 모두 최근에
자주 이용중인 Aliexpress에서 구매했다. 키캡은 새로운 프로파일을 사용해보고 싶어 XDA 프로파일 키캡을
구매했고, 축은 사무실에서 사용하기 위해, 넌클릭(택타일) 타입의 저소음 축을 구매했다. 무려 불량률이 높은 것으로
악명이 높았던 OUTEMU사의 제품. 아래에 키보드 및 사용한 키캡과 축에 대해 정리하였다.

# Specs.
- Name: Keychron Q1 Knob version
- Color: Gray
- Layout: ANSI
- Switch: OUTEMU silent gray
- Switch type: non-click (tactile)
- Keycap: XDA profile matcha keycap (KR sublimed)

# QMK / VIA 프로그램
## QMK
QMK. 전체 명칭은 'Quantum Mechanical Keyboard'. 이름만 들어보고 왜? 라는 의문을 남길만한 이름을
가지고 있다. 무튼 이름은 신경쓰지 말고, 조금 알아보니 QMK는 **C**를 바탕으로 만들어진 프로그램 이였다.
그렇다 보니 기본적으로 CLI를 기반으로 하고 있었는데, 커스텀을 하려면 일단 C를 기본적으로 이해하고 있어야...
손을 댈 수 있는 정도인 걸로 판단되었다. 마우스를 키보드에서 사용한다던지, LED의 여럿 효과 등의
이미 로우레벨은 미리 구축되어 있는 것 같은데, 이를테면 어떤 A란 조건에서 B라는 걸 실행하는 것의 레벨에서는
직접 코드를 짜야 한다는 것.

### 외부링크 모음
- [QMK Docs](https://docs.qmk.fm)
- [QMK Github](https://github.com/qmk/qmk_firmware): QMK 펌웨어를 여기 git을 clone하여 사용할 수 있다.
자세한건 QMK Docs 참조.
- [QMK Toolbox](https://github.com/qmk/qmk_toolbox): QMK 펌웨어를 컴파일한 파일을 키보드에 적용하는 도구. 
현재는 Windows / Mac만 지원하고 linux의 경우 cli의 qmk 명령어로 적용하면 된다.

## VIA
VIA는 QMK보단 사용하기 쉬운 프로그램인데, 기존의 기계식 키보드의 관리 프로그램 정도에 딱 대응이 된다고
말할 수 있다. 키보드 키에 여러 키 지정, 매크로, LED 효과 지정 등. 또한 키가 제대로 눌리는 지에 대한 인식 확인도
내장되어 있다. 하지만 내가 산 Q1 키보드는 모종의 이유로 VIA의 LED lighting을 지원하지 않았으며, 이를 이용하고자
하려면 QMK를 사용해야 하는 것으로 보였다.

### 외부링크 모음
- [VIA](https://www.caniusevia.com/): VIA Configurator 공식 사이트.

# 키크론 Q1 Knob에서 QMK 사용하기
제품을 수령하고 QMK를 적용해보면서 우여곡절을 좀 겪은 끝에(-_-) 지금은 확실하게 알게된 몇 가지를 정리해보면,
(22.02.21 기준)

- QMK Github 페이지에 올라온 키크론 Q1을 위한 QMK는 현재 **노브버전은 없다.**
    - 키크론 키보드에 대한 QMK는 ['여기'](https://github.com/qmk/qmk_firmware/tree/master/keyboards/keychron)있는데, q1에 대한
    모든 버전이 노브없는 버전이다. 이는 직접 qmk 컴파일을 통해서 확인을 해본 부분.
- 따라서 QMK 정식(?) 깃에는 올라와 있지 않더라도, 키크론에서 포크해서 수정하지 않았을까 하여 구글링을 해봤는데, 역시 있었다.
- Keychron 키보드의 QMK 적용 테스트는 ['Keychron이 포크한 사이트'](https://github.com/Keychron/qmk_firmware) 에서 이루어지고 있다.
    - 'lalalademaxiya1' 라는 개발자분이 주로 기여하는 듯.

따라서 키크론에서 포크한 페이지를 git clone해서 내 키보드에 적용해보기로 했다. 하지만 22.02.21 기준 rev_0107을 적용해본 결과, 
특정 열부터 **입력이 되지않는 문제**가 발생... master branch에 올라온 파일이였는데 적용이 되지 않았다.
또한 키보드에 플래싱 도중 중간에 멈춰버리는 상황도 발생하여, 불안정한 모습을 보였다.
매우 당황스럽긴 했지만 구글링을 하여 찾아본 결과 Reddit에 'Caps Lock 켜짐 확인 LED, FN키 지정된 키에 대한 LED 표시, 그리고 슬립모드에서 LED 끄기'
기능을 넣었다는 게시글을 보게 되었다. 링크는 ['여기'](https://www.reddit.com/r/Keychron/comments/s13tru/q1_knob_firmware_turn_lights_off_when_in_sleep/).
'CrazyCoder' 라는 닉네임을 가진 분이 만들었고, [(github 페이지)](https://github.com/CrazyCoder/qmk_firmware/tree/master/keyboards/keychron/q1/rev_0107/keymaps/crazycoder)
git clone에서 qmk 적용을 해보니, 다행히 기본 키 맵핑과 crazycoder가 커스텀한 맵핑 모두 적용이 되는 것을 확인했다. 

그런데 여기서, 내가 굳이 QMK를 만져가며 커스텀 해야하는 이유는, 노브를 사이트 스크롤 기능으로 사용하고 싶었기 때문이다.
하지만 기본적으로 제공되는 VIA로 해본 결과 적용이 되지 않았다. 분명 할당된 키가 있는데도.
따라서 crazycoder의 파일을 좀 살펴보니, 이 버전에서는 마우스를 키보드에서 사용하는 기능이 **적용되어 있지 않았다...**
기능 활성화와 관련된 파일이 rules.mk에 있는 것 같은데, 열어보니 'MOUSEKEY_ENABLE = **no**'로 작성이 되어 있던 것.
이를 yes로 바꿔주고 VIA에 다시 적용하니 정상적으로 작동했다... 이걸 사용하려고 일부러 AutoHotKey라는 프로그램까지 사용했는데...
그럴 필요가 없던 것. 이점에 대해서는 혹시나 다른 Q1 Knob 버전 사용자를 위해서 따로 게시글을 작성해서 정리해봐야 겠다.