
### `Preview`
---
![KakaoTalk_Photo_2023-08-16-00-27-11](https://github.com/YoungMinDA/Team_project/assets/109095108/5e02065f-3195-4009-ba85-bcac4439b733)
- **팀 구성** : 환경지키조 4인
- **개요 :** 사회의 이해관계와 국가 정책 & 데이터 분석 결과를 바탕으로 ‘**GS25 편의점**’을 폐의약품 수거 플랫폼으로 선정한 **최초의** 입지 분석 프로젝트
- **역할** : 편의점 플랫폼 도입 제안, 데이터 수집 & EDA & 전처리, Tableau 대시보드 개발 **(기여도 30%)**
- **성과 :** 플랫폼 도입에서 **단순 생활인구수**가 아닌 폐의약품 위험도 & 발생량, 기존 수거함 위치를 고려한 **GS25 편의점** **지점** 선정 및 **비즈니스 모델** 제안
- **참여** **공모전** :  동대문구 공공데이터 활용 정책 아이디어 공모전 & 제6회 전국 청년 아이디어톤 대회 & 환경부 에코톤 데이터 활용 및 분석 공모전 
- **결과** : 최우수상 1위 & 본선 입선 & 예선 탈락

## 📋프로젝트 개요
환경보호를 위한 폐의약품 수거율 증진을 목표로 사회의 이해관계와 국가 정책, 데이터 분석 결과를 기반으로 한 ‘GS25 ’ 폐의약품 수거 플랫폼 입지 분석 프로젝트

`분석방법`

#### ✔️Python
<aside>
    
- Selenium 라이브러리를 활용한 전국 GS25 편의점 정보 웹 스크래핑
    - CSRF Token 값 확인됨에 따라 수집 과정에서 무작위 문자열이 포함되는 **문제** 발생
        - **문제** 해결을 위해 requests.Session 함수를 활용하여 토큰값 고정
        - 비즈니스 모델 서비스 제공을 위한 전국 GS25 지점 정보 수집
        ![image](https://github.com/YoungMinDA/Team_project/assets/109095108/f1aeab8b-8ac0-4022-864a-6447c3058fa4)
- Pandas, Numpy, Matplotlib, Seaborn 라이브러리를 활용한 EDA & 전처리
    - 플랫폼 입지 선정에서 생활인구수가 아닌 폐의약품 발생량이 중요하다고 판단 & 가설 수립
        - 입지 분석을 위한 GS25 데이터에서 ‘수원시’ 소속 ‘택배서비스’  제공 지점 추출
            - 효율적인 Tableau 맵 시각화를 위한 위도 & 경도 & 주소 데이터 가공
              ![image](https://github.com/YoungMinDA/Team_project/assets/109095108/e915fd77-d31a-461b-b144-d3dad2e00944)
      - 의약품 주성분 데이터에서 유해도가 높은 의약품 데이터 추출
        - 의약품 안전나라의 약품 코드 조회시스템을 통해 동일 성분의 의약품 확인 &  가공
      - 폐의약품 발생량 도출 & 분석의 신뢰성 **향상**을 위한 생활인구 데이터 전처리 진행
        - 분석의 신뢰성 향상을 위한 국립환경과학원의 기술 통계량 채택
            - 폐의약품별 유해도 & 성별 & 연령별 가중치 적용
        - 폐의약품 발생률 데이터가 없는 0 ~ 19세 연령의 데이터 제거
        - 연령대별(5세 계급 → 10세 계급) 데이터 가공
            ![image](https://github.com/YoungMinDA/Team_project/assets/109095108/e61e1a69-51f6-4eb8-8b95-93c8191effee)

       
- Scikit-learn 머신러닝 라이브러리를 활용한 생활인구에 따른 폐의약품 발생량 **예측** & **통계적 유의성** 확인
    - 성별과 연령대로 구성된 범주형 데이터셋 구조 특성상 분석의 신뢰성이 감소하는 **문제** 발생
        - 다중회귀분석의 통제변수를 위한 성별, 연령대 데이터 가공
            - 성별 : 명목척도 & 연령대 : 비율척도 → 가변수 변환(Dummy Variable)
        - 결정계수(R-squared) : 0.013, F 검정 통계량(F-statistic) : 895.6
            ![image](https://github.com/YoungMinDA/Team_project/assets/109095108/a836c5ae-befb-49a8-8b14-0bc9b6582bbe)

        - **문제** 해결을 위해 서울시 도시정책 기반의 보행자 친화 접근성 기술 통계량 적용 & 신뢰성 부여 (Buffer, 150m~400m)
    - Pivot Table을 활용한 연령대별 폐의약품 발생량이 가장 많은 자치구 도출
    
</aside>

<aside>

#### ✔️Tableau

- 편의점 트렌드 리포트를 통한 국내 4사 편의점 비교 분석 **대시보드** 개발
    - 편의점을 플랫폼으로 선정한 이유
        - 24시간 운영, 택배 서비스를 통한 인프라 확보, 지점 분포, 프로모션 개최 등 폐의약품 수거율 증가에서 큰 장점이 있음
    - GS25 편의점을 플랫폼으로 선정한 이유
        - GS25 → 매출 1위, 위치 선호도 1위, 프로모션 선호도 1위, 점포 수 2위
        - 4사 편의점의 직관적인 비교를 위해 막대 & 파이 차트 채택      
            ![image](https://github.com/YoungMinDA/Team_project/assets/109095108/184cbbac-ae02-4c1e-8367-9d4f1628617e)
            
- 입지 분석 주제에 기반한 수원시 자치구별 데이터셋 비교를 위한 맵 차트 시각화
    - 지리적 역할(시군구) 기능을 활용한 위도 & 경도 테이블 생성
    - 색상 & 레이블 기능을 활용한 자치구별 비교 인사이트 도출
    - 백그라운드 레이어 투명도 기능을 활용한 인사이트 강조  
        ![image](https://github.com/YoungMinDA/Team_project/assets/109095108/8a78129d-b4a7-43dc-a217-5b63c1546b9f)

- 선정 자치구 지점 분포도 & 입지 선정 지점 시각화를 위한 맵 차트 시각화
    - 필터 → 사용자 지정 기능을 활용한 GS25 선정 지점 분류
    - 상용화된 아웃도어 맵 배경을 채택하며 가독성 고려
    - 이중축 & 맵 모양 커스텀 기능을 활용한 수원시 GS25 편의점 지점 분포 맵 시각화
    - 지리적 역할(시군구), 공간함수(Makepoint & Buffer)를 활용한 맵 시각화
        - 7개의 GS25 지점 선정(Buffer, 300m~700m)
        - 도출된 최종 지점 선정(Buffer, 300m)  
        ![image](https://github.com/YoungMinDA/Team_project/assets/109095108/10e99879-46f2-46b4-91ed-4496487ec86a) 
</aside>

<aside>

#### ✔️QGIS

- 행정구역 shp 파일 & GIS 건축물통합정보 데이터 업로드 후 shp 파일 생성
- 생활인구 할당을 위한 지역구 내 격자 생성 후 총면적 계산
- 타겟하는 지역구 내의 GS25  & 폐의약품 수거함 shp 파일 업로드
- GS25, 폐의약품 수거함에 대해서 5 ~ 10분 거리의 Buffer 설정(300m~700m)
- 반복 최적화 후 효율적으로 폐의약품을 수거할 수 있는 Buffer 선정(300m)
</aside>

## 🎯 프로젝트 결과
- Python과 QGIS 를 활용한 입지 분석 및 최종 입점 지점 선정
    - 폐의약품 발생량이 많지만 수거함이 부족한 사각지대 지역 문제 해결
    - 폐의약품 발생량이 가장 많은 지역 선정 : **수원시 권선구**
    - 최우선 플랫폼 도입 지점 선정 : **GS25 수원 삼익점**
    - 플랫폼 도입 지점 후보 : GS25 구운 성원점, GS25 탑동 새롬점, GS25 서둔 햇살점,
                            GS25 고색대성점, GS25 권선오목천점, GS25 고색리치아노점                                                       
    
- 데이터 분석 서비스 공급을 통한 수익성 비즈니스 모델 설계
    - 수원시의 국한되지 않고 서울, 경기도 등 전국 모든 지역에 입지 분석 서비스 활성화 가능
- Tableau를 활용한 수원시의 자치구별 인사이트 & GS25 편의점 지점 관련 다양한 시각화 차트 제공
- 분석 결과를 바탕으로 구체적이고 실용적인 플랫폼 활성화 방안과 법안 & 정책 개선안 제시


## 🛫 아쉬운점, 향후 계획
- 실제 비즈니스 모델 서비스를 제공해보지 못한 점
- 주제 선정 & 데이터셋 문제로 환경부 공모전에 신뢰성 높은 분석 결과를 제공하지 못하여 탈락한 점 → 가중치 설정 & Tableau 맵 시각화 & QGIS 입지 분석 추가
- 아이디어 대회 특성상 데이터 분석을 기반으로 도출된 과정 & 결과를 심사기준에 전혀 고려하지 않은 점 →  분석 대상을 동대문구로 변경하며 고도화 과정을 통해 동대문구 공공데이터 활용 정책 아이디어 공모전 최우수상 수상

## 🧭 직무에 기여할 수 있는 부분
- Python과 Tableau를 활용한 데이터 EDA & 시각화 역량
- 다양한 요소의 상관관계를 고려한 비즈니스적 데이터 분석 역량
- 정보지리체계 도구인 QGIS 입지분석을 위한 공간정보 데이터셋 구축 역량

## 📺 발표 자료
- **제6회 청년 아이디어톤 입선 / 2023 동대문구 공공데이터 활용 정책 아이디어 공모전 최우수상 (1위)**

![image](https://github.com/YoungMinDA/Team_project/assets/109095108/13405cdb-3f4f-443a-a893-be5cab7de5d2)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/3c800ef6-4e0c-4b7c-b4bb-afed76353b97)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/d9ba3ed3-3c22-40ae-a420-2f1581e14a8a)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/274bc1aa-c89f-4d61-9432-b89c261f8959)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/7d6f918f-4198-42f6-b54b-018d13d49a4b)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/c087d555-df3d-4f01-a4fe-e8a0a2f5ec5a)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/754e9c01-25f1-40e1-9694-3dcebd406e1d)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/7e0b3215-7099-4f19-b6fc-ac4dc6328bf1)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/11d0a70d-d02c-4ab5-a41a-61bdeea03ba7)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/336986b5-dddf-4d5f-93c6-df39ad96bf3c)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/0408681c-74f7-4af7-b887-4bc1c7d4230e)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/bffc085a-7395-4448-b0e5-06999d8b4e2f)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/dcbef710-cfde-4ad1-9b2b-3dd5280d3a0b)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/805d15e0-a7f2-4127-91d8-9a0af90c97d6)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/2e368e4c-21a6-4ed3-8742-ec98cbdbe42f)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/8f9c3a1f-a800-40e4-a7b5-ee650804cf82)
![image](https://github.com/YoungMinDA/Team_project/assets/109095108/05a352a2-8e88-4f83-94a5-2a8369469b42)

- **제6회 전국 청년 아이디어톤 대회, 입선**
    
    ![image](https://github.com/YoungMinDA/Team_project/assets/109095108/b7a8eb5a-aa02-4c72-8f32-4db951f4d80e)
    ![image](https://github.com/YoungMinDA/Team_project/assets/109095108/25f19bd4-f468-47b0-a41a-f6a4bbdd8256)


- **동대문구 공공데이터 활용 정책 아이디어 공모전, 최우수상 1위**
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/c1fdcefb-7962-458e-a778-eb23001249d7/c3c61b2c-a7be-4cbb-9e36-98c7f0720ec6/Untitled.jpeg)
    ![image](https://github.com/YoungMinDA/Team_project/assets/109095108/b786b91a-b693-4c2f-a6ac-ab547a3e1f11)
