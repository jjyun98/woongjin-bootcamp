# Web Traffic 분석 프로젝트

캠페인 전후 웹 트래픽 데이터를 분석하여 마케팅 효과를 측정하는 프로젝트입니다.

## 프로젝트 구조

```
api_project/
├── get_logs.ipynb              # API를 통한 로그 데이터 수집
├── project_main.ipynb          # 메인 분석 (EDA, 시각화, 통계검정)
├── quantitative_analysis.ipynb # 정량적 지표 분석
├── .env                        # API Key (보안 - git 제외)
├── .env.example               # 환경변수 템플릿
└── data/
    ├── api_data.csv           # 수집된 로그 데이터
    └── GeoLite2-City.mmdb     # IP 위치 정보 DB
```

## 설치 및 실행

### 1. 필요한 패키지 설치

```bash
pip install requests pandas numpy matplotlib seaborn scipy python-dotenv geoip2
```

### 2. API Key 설정

`.env.example` 파일을 복사하여 `.env` 파일을 생성하고 실제 API Key를 입력합니다:

```bash
cp .env.example .env
```

`.env` 파일 내용:
```
API_KEY=your_actual_api_key_here
```

### 3. GeoIP 데이터베이스 다운로드

MaxMind에서 GeoLite2-City 데이터베이스를 다운로드하여 `data/` 폴더에 저장합니다.
- https://dev.maxmind.com/geoip/geolite2-free-geolocation-data

### 4. 노트북 실행 순서

1. **get_logs.ipynb**: API로 데이터 수집
2. **project_main.ipynb**: 기본 분석 및 시각화
3. **quantitative_analysis.ipynb**: 정량적 지표 분석

## 주요 분석 내용

### 1. project_main.ipynb
- 데이터 탐색 및 전처리
- 일별/시간대별 트래픽 추이
- 트래픽 소스 분석 (utm_medium, utm_source, utm_campaign)
- 페이지 카테고리별 분석
- 캠페인 전후 비교
- 통계적 유의성 검정 (카이제곱, 비율 검정)

## 주요 발견사항

- 캠페인 종료 후 Direct + Organic 트래픽이 유의하게 증가
- Paid 트래픽 의존도 감소로 광고비 절감 효과 확인
- 모든 변화는 통계적으로 유의미함 (p<0.05)

## 보안 주의사항

- `.env` 파일은 절대 GitHub에 올리지 마세요
- `.gitignore`에 `.env`가 포함되어 있는지 확인하세요
- 공유 시에는 `.env.example`을 사용하세요

## 라이선스

This project is for educational purposes.
