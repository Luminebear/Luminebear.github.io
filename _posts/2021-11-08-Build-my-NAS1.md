---
title: "개인 NAS 구축기 - 1장"
tags: [NAS, Linux, Ubuntu] # 태그 입력
categories: NAS
mathjax: false # MathJax 사용을 위한 태그
comments: true
published: true
---

# Intro
작년 이맘 때 캡스톤디자인 프로젝트(주제는 파이썬과 pygame으로 만든 게임인데, ['Quantum Coda'](https://github.com/jiwonchoi-phys/QuantumCoda) 참조)를 위해서 ODROID-H2+ 이라는 싱글보드 컴퓨터(SBC)를 마련했다.
테스트를 위해 제대로된 PC가 있었으면 했지만, 자원이 한정되어서 여러 SBC (예를들면 대표적인 라즈베리 파이4)들 중에 그나마 테스트용으로 성능이 괜찮은 이 SBC를 선택했다. 프로젝트가 끝나고 개발용도로는 끝나서
어떻게 활용을 하면 좋을지 고민하다, 마침 필요하다고 생각했던 NAS로 사용해보기로 했다.

# Hardware
먼저 개인 NAS 구축을 해보려고 마련한 제품은 아래와 같다.

- SBC ODROID H2+
    - CPU: Intel Celeron J4115 (4) @ 2.50 GHz
    - RAM: SAMSUNG DDR4-2666 (PC4-21300) 8GB x1
    - SSD: SAMSUNG PM981a 256GB
    - HDD: TOSHIBA P300 (HDWD120) 3.5" 2TB x2
- Others
    - TUREX SC-80 acrilic case
    - NOCTUA NF-A8 5V PWM 80mm
    - T Technology TG-2535 SSD 2.5 to 3.5 HDD guide
    - Joycool JH-M.2 SSD 6MM BLACK
    - SATA data cable 30cm x2, Coms ND626 mini 4p / SATA power cable x2 **(important product!)**

여기서 이번에 NAS 구축을 하기 위해서 새로 구매한 제품이 HDD와 Others. HDD는 특별히 고민하여 도시바의 P300 시리즈를 선택했다. 이유는 이전에 Seagate 2.5인치 1TB 하드를 이용하다
**데이터를 왕창 날라먹은 적**이 있었기 때문에... 백업도 해놓지 않아서 일부 파일만 복구되었던 좋지 못한 기억이 있다. (앞으로는 절대로 Seagate는 안쓸거다.) 
그래서 보다 안정성이 높은 P300을 선택했다. 또한 한 하드가 망가져 데이터를 복구하지 못하는 불상사를 막기 위해
RAID1을 구성하려고 2개 주문했다. 그 외에는 사실 성능에 직접적인 영향은 안끼치지만 HDD의 진동과, SBC를 그냥 방치시키기엔 조금 뭐해서 필요한 부속품을 구매했다. 사실 이것또한 조금 난감한 상황이 있었는 데, 바로 **케이스와 쿨링용 팬**. 이유는

1. 반도체 수급문제로 ODROID-H2+가 **단종**, 덩달아 NAS용으로 적합했던 **케이스도 단종**.
2. 따라서 대체 케이스를 알리에서 찾다가 국내에서 3bay용 아크릴 케이스를 발견. 투렉스라는 곳에서 만드는 듯.
3. 쿨링용 팬은 5V, PWM, Frequency 조절이 가능한데, 새로 찾은 케이스가 80mm의 사이즈만 지원.
4. 3에 적합한 쿨링팬이 그 비싸다는 녹투아(NOCTUA) 밖에 없어 어쩔 수 없이 이것으로 선택.

그래서 Others 항목의 1,2 제품을 선택했다. 나머지 3,4 두 제품은 각각 하드디스크 가이드와 SSD 방열판인데, 전자는 3bay 케이스 윗단에 SBC를 올리고 따라서 하드디스크 손상 방지를 위한 가이드로,
후자는 단순히 SSD의 발열이 생각보다 심해, 방열판을 붙이려고 구매. 마지막으로 하드디스크 연결을 위한 케이블들을 마련했는데, 특히 오드로이드 H2+는 전원케이블이 조금 특이해서, 찾는데 애를 먹었다. 제품도 단종되는 바람에
케이블도 따로 팔지 않았기 때문.

# Software
처음에는 NAS 구축을 위해 OpenMediaVault라는 것이 있다고 해서 선택했는데, 하필이면 이 프로그램이 지금 컴퓨터에 설치된 Ubuntu와 호환이 안된다고... 이상하게 데비안 OS에는 되어있다고 해서 계열OS인 우분투에 설치하려고 했으나
실패. OS를 밀까도 싶었지만 Ubuntu에 설정해둔 설정이 많았기에 (LAN사용이나 블루투스 모듈 재설정 등의 문제가 있었다.) 그냥 OS는 그대로 두고, '네트워크 드라이브' 방식으로 사용하기로 결정.

- OS: Ubuntu 20.04 LTS
- Samba for internal network
- SFTP / SSHFS for external network

파일 공유 방법은 samba와 SFTP / SSHFS를 선택했다. 찾아보니 samba는 외부연결 설정이 가능은 하나 보안문제가 크다고 하여 내부 네트워크만 사용하는 게 좋다고 한다. 그리고 SFTP / SSHFS는 이미 연구실에서 계산 서버와 통신을 위해
사용하고 있기 때문에 익숙한걸로 사용하기로.

# 마무리
사실 제품은 모두 도착해서 만들어 뒀고, 약간 잘못 만들어진 느낌이 없지 않아 있지만, 일단 퀄리티 자체는 만족할만한 수준.
혹시나 몰라 NAS를 사용할 일이 있을 지 모르니 구축방법을 까먹지 않기 위해 게시글을 작성해보기로.