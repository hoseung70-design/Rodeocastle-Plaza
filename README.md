# Rodeocastle-Plaza
Rodeocastle Plaza 매매 사이트
# 로데오캐슬 프라자 소개 페이지

경기도 평택시 청북신도시 "로데오캐슬 프라자" 상가 건물 통매매 소개용 랜딩 페이지입니다.
Flask(Python) 기반의 단일 페이지 사이트이며, 별도 데이터베이스는 사용하지 않습니다.

## 구성 내용

- 핵심 투자 포인트
- 매물 개요 (건물 사진 · 기본 정보)
- 임대 현황 (층별 임차 현황 표)
- 건물 층별 구성 종합 및 층별 상세 평면도
- 매매가 · 임대 조건 · 레버리지 시뮬레이션 · 투자 조건 요약
- 입지 개요 (배후수요 · 신상권 형성 지도)
- 투자 포인트 체크리스트
- 문의처: (주)하이파크시티 / 나연주 실장 / 02-313-3838 / 010-7679-8759

## 로컬 실행 방법

```bash
python3 -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

브라우저에서 `http://localhost:8080` 접속.

## 배포

`requirements.txt`에 `gunicorn`이 포함되어 있어 대부분의 PaaS(호스팅 서비스)에서
GitHub 저장소를 그대로 연결하면 자동으로 인식/배포됩니다.

```bash
gunicorn app:app
```

- **cafe24 AI Space**: 콘솔에서 GitHub 저장소 연동 후 배포 (런타임: Python 3.11)
- **Render / Railway / Fly.io 등**: "Import from GitHub" 후 시작 명령을 `gunicorn app:app`으로 지정

## 폴더 구조

```
.
├── app.py                 # Flask 앱 (라우트 + 콘텐츠 데이터)
├── requirements.txt
├── templates/
│   └── index.html         # 메인 페이지 템플릿
└── static/
    ├── css/style.css
    └── img/                # 건물·매장·평면도·입지 지도 이미지
```

## 콘텐츠/연락처 수정

- 매물 정보, 임대 현황, 수익률 수치, 문의처 등은 모두 `app.py` 상단의 변수
  (`CONTACT`, `PROPERTY_SPECS`, `TENANTS`, `DEAL_STATS`, `LEVERAGE_TILES`,
  `FINANCIAL_TABLE`, `LOCATION_BULLETS`, `CHECKLIST`)에서 관리합니다.
- 디자인은 `static/css/style.css`, 페이지 구조는 `templates/index.html`에서 수정합니다.
