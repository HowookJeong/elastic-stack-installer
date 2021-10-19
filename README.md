# elastic-stack-installer

## 각 stack 경로로 들어가서 실행 하면 됩니다.
## 기본 stack 의 start/stop 스크립트는 포함이 되어 있습니다.

```
$ cd stack/elasticsearch/bin
$ zsh installer
```

```
설치 할 운영체제를 선택 하세요.
0. MACOS
1. LINUX_X86_64
2. LINUX_AARCH64
   0
   선택한 운영 체계는 0 번 입니다.
   설치 할 버전을 입력 하세요.
   예) 7.15.1
   7.15.1
   입력한 버전은 7.15.1 입니다.

VPN 연결을 통해 배포가 이루어 지나요? (y/n)
설치 파일을 먼저 다운로드 받습니다. 이후 설치 스크립트를 재실행 하고 이 단계를 'N' 로 입력하고 스킵 합니다.
n
wget --read-timeout=5 --timeout=5 --no-check-certificate https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.15.1-darwin-x86_64.tar.gz
--2021-10-19 18:31:24--  https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.15.1-darwin-x86_64.tar.gz
artifacts.elastic.co (artifacts.elastic.co) 해석 중... 34.120.127.130
다음으로 연결 중: artifacts.elastic.co (artifacts.elastic.co)|34.120.127.130|:443... 연결했습니다.
HTTP 요청을 보냈습니다. 응답 기다리는 중... 200 OK
길이: 338602042 (323M) [application/x-gzip]
저장 위치: `elasticsearch-7.15.1-darwin-x86_64.tar.gz'

elasticsearch-7.15.1-darwin-x86_64.tar.gz       100%[====================================================================================================>] 322.92M  2.93MB/s    /  1m 57s

2021-10-19 18:33:21 (2.75 MB/s) - `elasticsearch-7.15.1-darwin-x86_64.tar.gz' 저장함 [338602042/338602042]

SSH 통신을 위한 KEY 가 필요 한가요? (y/n)
n
SSH 접속 User 를 입력 하세요.
예) deploy
henry
설치할 인스턴스의 IP 를 입력 하세요.
예)
127.0.0.1
localhost
인스턴스에 설치할 경로를 입력 하세요.
예)
/home/deploy/apps/
/Users/deploy/apps/
인스턴스에 설치 파일을 배포할 경로를 입력 하세요.
예)
/home/deploy/dist/elastic-stack/elasticsearch
/Users/deploy/dist/elastic-stack/elasticsearch
Symbolic link 를 사용하시면 입력 하시고 아니면 엔터를 입력 하세요.
elasticsearch
ssh -p 22 -o StrictHostKeychecking=no henry@localhost mkdir -p /Users/deploy/dist/elastic-stack/elasticsearch
ssh -p 22 -o StrictHostKeychecking=no henry@localhost mkdir -p /Users/deploy/apps/
scp -P 22 -o StrictHostKeychecking=no elasticsearch-7.15.1-darwin-x86_64.tar.gz henry@localhost:/Users/deploy/dist/elastic-stack/elasticsearch
ssh -p 22 -o StrictHostKeychecking=no henry@localhost cd /Users/deploy/dist/elastic-stack/elasticsearch; tar -xvzf elasticsearch-7.15.1-darwin-x86_64.tar.gz
ssh -p 22 -o StrictHostKeychecking=no henry@localhost cd /Users/deploy/dist/elastic-stack/elasticsearch; rm -f elasticsearch-7.15.1-darwin-x86_64.tar.gz
ssh -p 22 -o StrictHostKeychecking=no henry@localhost cd /Users/deploy/dist/elastic-stack/elasticsearch; mv elasticsearch-7.15.1 /Users/deploy/apps/
scp -P 22 -o StrictHostKeychecking=no start henry@localhost:/Users/deploy/apps//elasticsearch-7.15.1/bin/
scp -P 22 -o StrictHostKeychecking=no stop henry@localhost:/Users/deploy/apps//elasticsearch-7.15.1/bin/
ssh -p 22 -o StrictHostKeychecking=no henry@localhost cd /Users/deploy/apps//elasticsearch-7.15.1/bin; chmod 755 start
ssh -p 22 -o StrictHostKeychecking=no henry@localhost cd /Users/deploy/apps//elasticsearch-7.15.1/bin; chmod 755 stop
elasticsearch-7.15.1-darwin-x86_64.tar.gz                                                                                                                  100%  323MB 237.0MB/s   00:01    
x elasticsearch-7.15.1/
...중략...

start                                                                                                                                                      100%  211   572.4KB/s   00:00    
stop                                                                                                                                                       100%   97   283.6KB/s   00:00    
ssh -p 22 -o StrictHostKeychecking=no henry@localhost cd /Users/deploy/apps/; rm -f elasticsearch
ssh -p 22 -o StrictHostKeychecking=no henry@localhost cd /Users/deploy/apps/; ln -s elasticsearch-7.15.1 elasticsearch
다운로드 받은 파일을 삭제 합니다.
rm -f elasticsearch-7.15.1-darwin-x86_64.tar.gz
```