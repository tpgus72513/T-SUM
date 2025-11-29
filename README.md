📘 T-SUM 프로젝트: 세종시 전기차 충전소 수요 분석

세종시 각 동(洞)별 전기차 충전소 현황을 분석하고,
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
│   └── charts/                       # 분석 결과 시각화 이미지(원하면 추가)
│
├── notebooks/
│   └── 01_data_cleaning.ipynb        # 전체 분석 Jupyter Notebook
│
└── README.md               # 프로젝트 설명

📊 분석 내용 요약
1. 전기차 충전소 데이터 정제

위경도 분리(lat/lng)

숫자형 변환

NaN 좌표 제거

세종 지역만 필터링

2. 주소에서 동(洞) 이름 추출

정규식 + 주소 문자열 탐색으로

충전소 주소 → 동 추출

아파트 법정동 주소 → 동 추출

3. 동별 집계

충전소 개수

아파트 세대수

전체 세대수

기타 통계

4. 지표 계산

동별로 아래 지표 생성:

households_per_charger
→ 충전기 1대당 몇 세대가 사용하는지

apt_per_charger
→ 충전기 1대당 아파트 세대수

두 지표가 높을수록 충전 수요가 매우 많은 지역임.

5. 우선 설치 지역 선정

지표 상위 10개 동을 선정
→ top_apt_per_charger
→ top_households_per_charger

6. Folium 지도 시각화

세종시 전체 충전소 표시

우선 설치 필요 지역은 빨간색 마커로 강조

HTML로 저장하여 누구나 브라우저에서 열람 가능.

📍 주요 결과물
🔹 전체 충전소 지도

results/sejong_ev_map.html

🔹 우선설치 필요지역 강조 지도

results/sejong_ev_priority_map.html
(빨간색으로 표시됨)

🔹 그래프 예시

충전소 대비 아파트 세대수 TOP10

충전소 대비 전체 세대수 TOP10

🛠 사용한 기술

Python

pandas

numpy

folium

matplotlib

Jupyter Notebook

👥 Team T-SUM

📤 공유 방법
1) GitHub에서 “Code → Download ZIP”

→ 모든 노트북, 데이터, 결과물 다운받아 실행 가능

2) HTML 지도만 공유

results/*.html 파일은
브라우저에서 바로 열람 가능

📌 사용 안내
🔹 Jupyter Notebook 실행하는 방법
pip install -r requirements.txt
jupyter notebook

🔹 지도 HTML은 뷰어 없이 실행됨

sejong_ev_priority_map.html
더블클릭 → 바로 열림
