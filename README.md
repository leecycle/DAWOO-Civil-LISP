# DawooCivilLISP

DawooCivilLISP는 토목·CAD 실무에서 반복되는 도면 작성, 편집 및 조회 작업을 빠르고 일관되게 처리하기 위한 통합 LISP·CAD .NET 도구 모음입니다. 하나의 배포 파일로 AutoCAD와 ZWCAD 2024를 함께 지원하며 설치, 자동 로드, 메뉴·도구막대·리본 등록, 업데이트 및 복원 기능을 제공합니다.

## 현재 버전

- 정식버전: [DawooCivilLISP 2.0.0](https://github.com/leecycle/DAWOO-Civil-LISP/releases/tag/v2.0.0)
- 공개베타: [DawooCivilLISP 2.7.19](https://github.com/leecycle/DAWOO-Civil-LISP/releases/tag/v2.7.19)
- 공용 설치 폴더: `C:\DAWOO\DAWOO-Civil-LISP`

## 지원 환경

- AutoCAD 2021~2027 (Windows x64, 정규 AutoCAD; 제품·버전별 실기 검증 별도)
- ZWCAD 2024 (Windows x64; 제품별 실기 검증 별도)
- DLL 빌드 기준: AutoCAD 2021~2024 .NET Framework 4.8 / 2025~2026 .NET 8 / 2027 .NET 10 / ZWCAD 2024 .NET Framework 4.8
- Excel 연동 기능은 Windows용 Microsoft Excel이 필요합니다.

## 주요 기능

- 삼각망·도로 선형·종단·횡단 작성 및 표고 처리
- 좌표 작성과 Excel 좌표 가져오기·내보내기
- CAD 표와 Excel 표 변환 및 연결 데이터 업데이트
- 레이어·문자·치수·객체 편집과 도면 정리
- 면적·거리·누계 조회
- 속성 도곽 일괄수정과 뷰포트 작업
- AutoCAD와 ZWCAD 자동 판별 및 버전에 맞는 실행 파일 로드
- 명령어 변경, 사용자 설정 저장, 모델리스 설정창
- 프로그램 내 업데이트와 백업 버전 복원
- PDF 도움말 및 DawooCivilLISP 메뉴 제공

> 토목좌표 기본 단위는 도면거리 `1 = 1.00 m`입니다.

### 주요 명령

아래는 기본 실행명입니다. 실제 고정 명령어는 `DWC_` 접두어를 사용하며, `DWCOP`의 명령어 변경에서 실행명을 바꿀 수 있습니다.

- `DWTIN` 삼각망 그리기
- `DWDPL` 선형 작성
- `DWGRP` 종단 추출
- `DWDVL` 종단 작성
- `DWFM` 횡단 추출
- `DWFW` 표고 작성 / `DWFEL` 표고 찾기
- `DWS3P` 선형 표기
- `DWXY` 좌표 작성
- `DWCEX` 좌표 Excel 보내기 / `DWCIM` 좌표 Excel 가져오기
- `DWCTE` CAD 표 Excel로 / `DWETC` Excel 표 CAD로
- `DWCLAY` 표준 레이어
- `DWARE` 면적 계산 / `DWVV` 거리 측정
- `DWTU` UCS·화면 방향 설정
- `DWCALS` 속성 도곽 일괄수정

## 설치 방법

1. [릴리스 목록](https://github.com/leecycle/DAWOO-Civil-LISP/releases)에서 사용할 버전의 `DawooCivilLISP.*.zip`을 내려받습니다.
2. ZIP을 완전히 압축 해제합니다.
3. AutoCAD와 ZWCAD를 모두 종료합니다.
4. 압축을 푼 폴더에서 `Install.exe`를 실행합니다.
5. CAD를 다시 시작합니다.
6. 명령창에서 `DWCOP`을 실행하고 버전정보에서 현재 CAD와 DawooCivilLISP 버전을 확인합니다.
7. `DWCHELP`를 실행하면 PDF 도움말이 열립니다.

배포 ZIP에는 `Install.exe`와 `README.txt`가 포함됩니다. 공개베타는 각 버전의 릴리스 페이지에서 받을 수 있습니다.

### 설치 모드와 백업

설치기는 기존 설치 상태를 확인해 신규 설치, 업데이트 또는 구버전 마이그레이션을 처리합니다.

- 신규 설치: Civil의 신뢰 경로·시작하기 세트·PGP 명령 및 메뉴 등록을 처리합니다.
- 업데이트: 기존 사용자 설정과 사용자 지정 명령어를 유지하면서 제품 파일을 교체합니다. 설치 폴더에서 직접 고친 제품 파일은 교체될 수 있습니다.
- 1.x 마이그레이션: 기존 `C:\DAWOO\CivilLISP\DawooCivilLISP.lsp`를 감지하면 구버전 전용 백업을 만들고 새 설치 경로로 연결합니다.
- `DAWOO` 프로파일이 있으면 유지합니다. 없으면 유효한 현재 프로파일을 복사해 만들고 적용하며, 실패 시 기존 상태를 복원합니다.

백업은 서로 섞이지 않게 분리합니다.

- 일반 업데이트: `%LOCALAPPDATA%\DAWOO\DAWOO-Civil-LISP\Backup\2.x`
- 1.x 마이그레이션: `%LOCALAPPDATA%\DAWOO\DAWOO-Civil-LISP\Backup\Migration-1.x`

구버전 폴더는 삭제하지 않습니다. DawooLISP와 다른 시작세트 항목은 유지합니다.

## AutoCAD와 ZWCAD를 함께 사용하는 경우

두 CAD는 같은 `C:\DAWOO\DAWOO-Civil-LISP` 설치 폴더를 사용합니다.

- AutoCAD에서는 `DawooCivilLISP_*.vlx`를 자동으로 불러옵니다.
- ZWCAD 2024에서는 `DawooCivilLISP_*.zelx`를 자동으로 불러옵니다.
- 메뉴 등록 상태는 제품별로 확인합니다.
- 한 번 설치하거나 업데이트하면 두 CAD용 파일이 함께 교체됩니다.
- DLL은 다음 제품·버전별 Runtime 폴더에서 선택합니다.

```text
Runtime/
├─ AutoCAD/
│  ├─ 2021/   # AutoCAD 2021~2024
│  ├─ 2025/   # AutoCAD 2025~2026
│  └─ 2027/   # AutoCAD 2027
└─ ZWCAD/
   └─ 2024/
```

## 업데이트

`DWCOP`에서 정식버전 또는 공개베타 업데이트 채널을 선택하고 저장할 수 있습니다. 기존 사용자의 채널 선택값은 유지합니다.

1. CAD 명령창에서 `DWCUPDATE`를 실행합니다.
2. 설정한 채널에 따라 GitHub의 최신 정식 또는 공개베타 릴리스를 비교합니다.
3. 업데이트를 승인한 뒤 도면을 저장합니다.
4. AutoCAD와 ZWCAD를 모두 완전히 종료합니다.
5. 기존 설치를 백업하고 새 패키지를 검증한 뒤 교체합니다.
6. 실패하면 백업에서 복원을 시도합니다. 복원이 실패하면 안전 백업을 보존해 다시 복구할 수 있게 합니다.

업데이트 실행 파일은 `Updater.exe`입니다. 기본 실행명이 변경된 명령은 이전 기본값과 일치할 때만 새 기본값으로 이전하며, 사용자가 따로 지정한 실행명은 유지합니다.

## 메뉴와 도움말

- `DWCTOOLBAR`: DawooCivilLISP 도구막대 표시
- `DWCTOOLBARRESET`: 메뉴·도구막대 다시 등록
- `DWCHELP`: PDF 도움말 열기
- `DWCUPDATE`: 최신 버전 확인 및 업데이트
- `DWCROLLBACK`: 백업된 이전 버전으로 복원
- `DWCOP`: 설치 폴더·백업·버전·재로드·업데이트 채널·명령어 설정

전체 명령과 사용 방법은 설치 폴더의 `DawooCivilLISP_Help.pdf`에서 확인할 수 있습니다.

### 프로그램 삭제

CAD를 모두 종료한 뒤 설치 폴더의 `Uninstall.exe`로 삭제합니다. 사용자 설정·백업·사용자가 수정한 파일, `DAWOO` 프로파일과 DawooLISP는 보존하도록 처리합니다. 삭제 결과와 보존된 파일은 삭제 안내를 확인하십시오.

## 버전 이력

### 2.7.19 공개베타

- FW·FEL·RZV·XY·CEX·CIM·CALS·VFR·VTH·CBV·BOP·VV·PEL·DCP·DIVL·DDE·DOE의 도면·Excel 실행부를 기존 공용 CAD .NET 연결로 이전했습니다.
- 기존 LISP 설정·입력·숫자 서식과 일부 CAD 기본 명령 호출을 유지합니다.
- 기존 창 디자인·명령어·설정 저장·지반고 및 삼각망 계산을 유지합니다.
- 소스·DLL 빌드와 모의 검사를 수행했으며, 실제 CAD 동작은 별도 확인 대상입니다.
- [2.7.19 공개베타 릴리스](https://github.com/leecycle/DAWOO-Civil-LISP/releases/tag/v2.7.19)

### 2.7.14~2.7.18 공개베타

- AutoCAD 2025 이후용 DLL과 제품·버전별 Runtime 구성을 추가했습니다.
- 설정창의 화면 중앙 배치를 적용했습니다.
- 레이어·문자·치수·종단·삼각망 등의 실행부를 단계적으로 공용 CAD .NET으로 이전했습니다.

### 2.6.x~2.7.x 공개베타

- CAD 표·Excel 표 변환과 도로 선형·종단 작성 기능을 추가했습니다.
- 설정 저장·명령어 변경·모델리스 창과 TU 후 좌표 표기를 보완했습니다.
- `Updater.exe`, `Uninstall.exe`, 사용자 명령어 이전 및 설치·복원 처리를 보완했습니다.

### 2.0.0 정식버전

- 저장소와 공용 설치 경로를 `DAWOO-Civil-LISP`로 전환했습니다.
- AutoCAD·ZWCAD용 메뉴·도구막대·리본과 실행 파일을 함께 배포합니다.
- 기존 등록 경로 전환과 2.x 백업 분리를 적용했습니다.
- [2.0.0 정식 릴리스](https://github.com/leecycle/DAWOO-Civil-LISP/releases/tag/v2.0.0)

전체 변경 이력은 [릴리스 목록](https://github.com/leecycle/DAWOO-Civil-LISP/releases)에서 확인할 수 있습니다.

## 주의 사항

- AutoCAD와 ZWCAD가 실행 중일 때 설치 파일을 강제로 교체하지 마십시오.
- ZIP 내부에서 바로 실행하지 말고 반드시 완전히 압축 해제하십시오.
- LISP 원본은 ANSI(CP949) 인코딩을 유지합니다.
- 설치 패키지에는 AutoCAD용 VLX와 ZWCAD용 ZELX가 모두 포함됩니다.
- 문제가 생기면 CAD를 종료한 뒤 `DWCROLLBACK`을 사용하거나 배포본으로 다시 설치하십시오.
