# 📘 T-SUM: 세종시 전기차 충전소 수요 분석

세종시 각 동(洞)별 전기차 충전소 분포를 분석하고, 충전 수요 대비 공급이 부족한 지역을 도출하는 데이터 분석 프로젝트입니다.

## 🎯 프로젝트 목표

- 세종시 전기차 충전소 위치 및 분포 분석
- 동별 아파트 세대수·전체 세대수와 충전소 수 비교
- 충전기 1대당 세대수 지표를 활용한 충전소 부족 지역 도출
- Folium 기반 인터랙티브 지도로 분석 결과 시각화

## 📂 프로젝트 구조

```text
T-SUM/
│
├── data/                         # 원본 데이터
│   ├── 충전소현황.csv
│   ├── apartments.xlsx
│   └── population.csv
│
├── results/                      # 분석 결과
│   ├── sejong_ev_map.html
│   ├── sejong_ev_priority_map.html
│   └── charts/
│
├── notebooks/
│   └── 01_data_cleaning.ipynb
│
└── README.md

📊 분석 과정
1. 전기차 충전소 데이터 정제
- 위도·경도(lat, lng) 데이터 분리
- 좌표 데이터 숫자형 변환
- 이상값 및 결측치 제거
- 세종시 소재 충전소 데이터만 필터링
2. 주소에서 동 이름 추출
- 충전소 주소 문자열에서 동 정보 추출
- 아파트 법정동 주소에서 동 정보 추출
- 문자열 탐색 기반 사용자 정의 함수 활용
3. 동별 데이터 집계
동별로 다음 데이터를 집계합니다.
항목	설명
charger_count	동별 전기차 충전기 수
apt_households	동별 아파트 세대수
households	동별 전체 세대수


이를 바탕으로 동별 충전 수요 분석 테이블을 생성합니다.
4. 충전 수요 지표 생성
충전소 부족 정도를 파악하기 위해 다음 지표를 계산합니다.
지표	의미
households_per_charger	충전기 1대당 전체 세대수
apt_per_charger	충전기 1대당 아파트 세대수


지표 값이 높을수록 세대수 대비 충전기 수가 적어, 충전소 추가 설치 필요성이 높은 지역으로 해석합니다.

5. 우선 설치 지역 선정
- households_per_charger 상위 10개 동 선정
- apt_per_charger 상위 10개 동 선정
- 두 지표를 종합하여 충전소 우선 설치 후보 지역 도출
6. 지도 시각화
Folium을 활용해 다음 지도를 생성합니다.
- 세종시 전체 전기차 충전소 위치 지도
- 충전소 우선 설치 필요 지역 강조 지도
- 우선 설치 대상 동의 충전소는 빨간색 마커로 표시
🗺️ 주요 결과물
결과물	설명
results/sejong_ev_map.html	세종시 전체 전기차 충전소 위치 지도
results/sejong_ev_priority_map.html	우선 설치 필요 지역을 강조한 충전소 지도
results/charts/	동별 충전 수요 지표 그래프 저장 경로


생성 가능한 그래프
- 충전기 1대당 아파트 세대수 TOP 10
- 충전기 1대당 전체 세대수 TOP 10
- 동별 충전소 수 비교 그래프
🛠️ 사용 기술
- Python
- pandas
- numpy
- folium
- matplotlib
- Jupyter Notebook
🚀 실행 방법
1. 필수 패키지 설치
pip install -r requirements.txt
2. Jupyter Notebook 실행
jupyter notebook
3. 분석 노트북 실행
notebooks/01_data_cleaning.ipynb 파일을 열어 순서대로 실행합니다.
데이터 파일은 프로젝트 구조를 기준으로 자동으로 불러오도록 구성되어 있습니다.
📤 공유 방법
GitHub 저장소 전체 공유
1. GitHub 저장소 링크를 공유합니다.
2. Code → Download ZIP을 선택합니다.
3. 압축 해제 후 위 실행 방법에 따라 분석을 실행합니다.
지도 파일만 공유
results/ 폴더의 HTML 파일은 브라우저에서 바로 열 수 있습니다.
- 별도 프로그램 설치 불필요
- 파일을 더블클릭하거나 브라우저로 열기 가능
👥 Team T-SUM
세종시 전기차 충전 인프라 현황을 분석하고, 데이터 기반의 충전소 우선 설치 지역을 제안하는 프로젝트입니다.
```
