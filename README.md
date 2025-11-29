📘 T-SUM 프로젝트: 세종시 전기차 충전소 수요 분석

세종시 각 동(洞)별 전기차 충전소 분포를 분석하고
**충전소 부족 지역(우선 설치 필요 지역)**을 도출하는 데이터 분석 프로젝트입니다.

📂 프로젝트 구조
T-SUM/
│
├── data/                    # 원본 데이터 (전기차 충전소, 아파트 단지, 인구·세대 정보)
│   ├── 충전소현황.csv
│   ├── apartments.xlsx
│   └── population.csv
│
├── results/
│   ├── sejong_ev_map.html            # 세종시 전체 충전소 지도
│   ├── sejong_ev_priority_map.html   # 우선 설치 대상 지역 강조 지도
│   └── charts/                       # 분석 결과 그래프 (필요 시 추가)
│
├── notebooks/
│   └── 01_data_cleaning.ipynb        # 전체 분석 Jupyter Notebook
│
└── README.md                         # 프로젝트 설명 문서

📊 분석 내용 요약
1) 전기차 충전소 데이터 정제

위경도(lat/lng) 분리

숫자형 변환 및 이상값 처리

NaN 좌표 제거

세종 지역만 필터링

2) 주소에서 동(洞) 이름 추출

충전소 주소 문자열에서 동 정보 추출

아파트 법정동 주소에서 동 정보 추출

문자열 탐색 기반 사용자 정의 함수 활용

3) 동별 집계 작업

충전소 개수(charger_count)

아파트 세대수(apt_households)

전체 세대수(households)

동별 통계 테이블 생성

4) 충전 수요 지표 생성

동별로 아래 두 핵심 지표를 계산:

지표	의미
households_per_charger	충전기 1대당 전체 세대수
apt_per_charger	충전기 1대당 아파트 세대수

→ 값이 높을수록 충전 수요가 높고, 충전기가 부족함을 의미함.

5) 우선 설치 지역 선정

두 지표의 상위 TOP10 동 선별

데이터 기반으로 가장 충전소가 부족한 지역 식별

6) Folium 지도 시각화

세종시 전체 충전소 위치 지도 생성 (sejong_ev_map.html)

우선 설치 필요 지역(동)이 있는 충전소는 빨간색 마커로 강조
(sejong_ev_priority_map.html)

HTML 파일로 저장하여 브라우저에서 바로 열람 가능

📍 주요 결과물
🔹 전체 충전소 지도

results/sejong_ev_map.html
👉 세종시 모든 충전소 위치 시각화

🔹 우선 설치 필요 지역 강조 지도

results/sejong_ev_priority_map.html
👉 우선 설치 필요 동(예: 다정동, 대평동 등) 마커가 빨간색으로 표시됨

🔹 그래프 예시

충전소 대비 아파트 세대수 TOP10

충전소 대비 전체 세대수 TOP10

이미지 파일은 /results/charts/에 추가 저장 가능

🛠 사용 기술

Python

pandas

numpy

folium

matplotlib

Jupyter Notebook

📤 공유 방법
✔ 1) GitHub에서 ZIP 다운로드

친구에게 레포 링크를 보내고

Code → Download ZIP


하면 전체 프로젝트 실행 가능.

✔ 2) HTML 지도만 공유

results/*.html 파일은 브라우저에서 더블클릭만 하면 열림
→ 별도 프로그램 필요 없음

📌 실행 안내
1) 필수 패키지 설치
pip install -r requirements.txt

2) Jupyter Notebook 실행
jupyter notebook

3) 노트북에서 데이터 경로는 프로젝트 구조 기준으로 자동 로드됨
👥 Team T-SUM

데이터 분석 및 전기차 충전소 수요 파악 프로젝트
