﻿# Take 0
DJMAX를 오마주 삼아 제작한 건반형 리듬 게임.
* 최신 버전 : `v1.1.0` (July 30, 2022)
* 플랫폼 : Windows
* 소스 코드 : <https://github.com/canplane/Take-0>
* 개발자 : canplane (<https://canplane.com>)
* 작업 기간 : 2015. 6. 5. ~ 11.,  2022. 7. 8. ~ 30.
* 사용 기술 : Adobe Flash CS6 (ActionScript 3.0)

### 업데이트 내역
* 직전 :
	* `v1.1.0` :
		* 오프셋 설정 기능 추가.
		* 일시 중지 시에도 피버 타임이 경과되는 버그 수정.
	* `v1.0.0` :
		* 판정 기준 완화 및 일시 중지 메뉴 추가.
		* 기타 버그 픽스, 예외 처리.
* 이전 :
	* 노트 데이터 유효성 판별을 위한 해시값 표시.
	* 판정 시스템 변경 및 결과 화면 추가.
	* 옵션 메뉴, 설정 프로그램 추가.
	* 6키 → 4 ~ 8키 모드로 지원 확대.
	* 노트 시간을 BPM 타임으로 변경.
	* ActionScript 2.0 → 3.0 기반으로 이식.

### 설명
* `play.exe` : 게임 프로그램
* `make.exe` : 노트 데이터 생성 프로그램
* `config.exe` : 키/속도/오프셋 설정 프로그램
* 속도 조작 : 0.5 단위로 1 ~ 5 선택 가능, 단축키 `↑`, `↓`
* 플레이 도중 일시 중지 : `Esc`

### 판정 체계
* 점수 :
	* 기본 300000점 만점 + 피버 가중치에 의한 추가 점수 부여. (피버 발동 없이 `Awesome`으로 올 콤보를 찍으면 300000점이 됨.)
	* 노트당 획득 점수는 `Awesome` : `Cool` : `Good` : `Bad` = 5 : 3 : 2 : 1.
	* 롱 노트는 처음과 끝 두 부분에 대해서만 계산하며, 콤보는 점수에 영향을 미치지 않음.
	* 피버 발동 시 점수 가중치는 `×2` 1.05배, `×3` 1.1배, `×4` 1.15배, `×5` 1.2배.
* 판정 : `Awesome` ±0.05초, `Cool` ±0.1초, `Good` ±0.15초, `Bad` ±0.25초, `Break` (미스), `Fault` (간접 미스).
* HP : 
	* 총 게이지 200, 노트당 `Awesome` 5, `Cool` 3, `Good` 2, `Bad` 1씩 충전.
	* 롱 노트의 처음과 끝을 제외한 부분에서는 0.1초당 1씩 충전.
	* `Break`은 10 감소, `Fault`는 5 감소.
* 피버 : 
	* `×2 ~ 5` 단계가 있으며, 발동부터 해제될 때까지의 지속 시간은 10초로 모두 동일. (`x5` 단계에서 피버를 발동하면 `x5`.)
	* 총 게이지 200, `Awesome`, `Cool`으로 판정된 노트에 한해서만 5씩 충전, 롱 노트의 처음과 끝을 제외한 부분에서는 0.1초당 2씩 충전.
	* 게이지가 차면 피버 키를 눌러 발동할 수 있음.
	* `Break` 판정 발생 시 피버 해제. (게이지에는 영향을 미치지 않음.)
* 콤보 :
	* 피버 단계에 비례하여 증가.
	* 롱 노트의 처음과 끝을 제외한 중간 부분에서는 0.1초마다 증가.
* 정확도 (%) : (100 * `Awesome` + 80 * `Cool` + 60 * `Good` + 30 * `Bad`) / (`Awesome` + `Cool` + `Good` + `Bad`)
* 랭크 :
	* 정확도 기준.
	* 생존 실패 시 `F`, 99% 이상 `SSS`, 98% 이상 `SS`, 97% 이상 `S`, 94% 이상 `AA`, 90% 이상 `A`, 70% 이상 `B`, 30% 이상 `C`, 30% 미만 `D`.

### 주의 사항
* 플레이 시 곡(`.mp3`), 앨범 아트(`.jpg | .png`), 노트 데이터(`.note`) 필요.
* ±250ms 이내 범위에서 오프셋 설정 가능.
* 키 입력 안 되면 `한/영` 키를 전환해 볼 것. (`Caps Lock`은 상관 없음.)
* 최적화 수준이 좋지 않아 끊김 현상이 있을 수 있으므로, 고사양 환경을 권장.
* 파일을 로드하는 시점에서, 파일의 용량이 다소 크다면 프로그램이 강제 종료될 수 있음.
* 노트 데이터는 노트 생성 프로그램에서 직접 키보드를 눌러 생성할 수 있음.

### 노트 데이터 생성 시 참고 사항
* 곡 파일은 정상적인 태그 출력 및 싱크를 위해 [멜론](https://melon.com)에서 다운로드 받아 사용하는 것을 추천.
* 앨범 아트 파일은 [벅스](https://music.bugs.co.kr/)에서 곡을 검색하면 나오는 `200 * 200` 사이즈의 사진을 다운로드하는 것을 추천.
* 노트 데이터 생성 시 참고할 수 있는 BPM 측정기 : <https://vocalremover.org/ko/key-bpm-finder>
* 노트를 생성하고 싶은 타이밍에 맞추어 직접 키를 눌러서 채보를 생성할 수 있음.
* 옵션 설명 :
	* `KEY MODE` : 4키에서 8키까지 선택 가능
	* `BPM` : 사용할 노래의 BPM. BPM에 맞춰 노트를 생성해야 하므로 필요.
	* `MAXIMUM NOTES PER A BEAT` (수정하지 않는 것을 권장) :
		* 한 비트 내에서 몇 박자를 최소 단위로 할 것인지 결정.
		* 예로 들어 4로 설정한 경우, BPM이 100이면 한 비트는 0.6초이므로 0.15초가 최소 박자 길이가 됨.
	* `MINIMUM LENGTH OF LONG NOTES` (수정하지 않는 것을 권장) :
		* 생성되는 롱 노트의 지속 시간이 이보다 길어야 함. 이보다 지속 시간이 짧으면 일반 노트로 인식되어 생성됨.