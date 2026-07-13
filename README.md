# Microbiome Portfolio

경희대학교 식품생명공학과 학부 연구생.
장내 미생물 유전체 분석과 데이터 사이언스를 공부하며 정리하는 공간입니다.

## 관심 분야
- 미생물 동정 및 유전체 분석 (MALDI-TOF, WGS)
- 메타지노믹스 데이터 분석 파이프라인
- 머신러닝 기반 분류·예측 모델

## 프로젝트

### 01. Python & pandas 기초 — 데이터 분석 첫걸음
[`01_python-basics.ipynb`](01_python-basics.ipynb)

Python 기초부터 데이터 분석·시각화까지의 학습 과정을 정리한 노트북입니다.

**다룬 내용**
- Python 기초: 변수, 리스트, 반복문(for)
- pandas: DataFrame 생성, 조건 필터링, `groupby`를 이용한 그룹별 통계
- CSV 파일 입출력 (`read_csv` / `to_csv`)
- seaborn을 이용한 시각화: 산점도(scatterplot), 그룹별 색상 구분

**분석 예시 — Iris 데이터셋 (150개 샘플)**
- 품종(species)별 꽃잎·꽃받침 크기 비교 (groupby)
- 산점도를 통해 품종 간 형태적 차이가 뚜렷하게 구분됨을 확인


### 02. 머신러닝 — Iris 품종 분류 모델
[`01_python-basics.ipynb`](01_python-basics.ipynb) (동일 노트북 후반부)

scikit-learn을 이용해 형태 측정값으로 품종을 예측하는 분류 모델을 구현했습니다.

**분석 과정**
- 특징(X: 꽃받침·꽃잎 길이/너비 4개)과 정답(y: 품종) 분리
- 학습용/검증용 데이터 분할 (7:3, `train_test_split`)
- 의사결정나무(Decision Tree) 모델 학습 및 예측
- 검증 정확도 100% (45개 샘플 전부 정확히 분류)
- 특징 중요도 분석: petal_length가 89%로 분류에 가장 결정적임을 확인

**의의**
동일한 구조를 마이크로바이옴 데이터에 적용하면, 균 조성으로 질병군을 예측하고
어떤 균이 핵심 바이오마커인지 도출하는 분석이 됩니다.
## 사용 도구
Python · pandas · seaborn · matplotlib · scikit-learn · Jupyter Notebook
### 03. 모델 검증과 성능 평가 — 교차검증 · ROC-AUC · Random Forest
[`01_python-basics.ipynb`](01_python-basics.ipynb)

단일 검증의 한계를 확인하고, 신뢰할 수 있는 모델 평가 방법을 적용했습니다.

**분석 과정**
- 5-fold 교차검증(`cross_val_score`)으로 성능 재검증
  → 단일 분할에서 100%였던 정확도가 실제로는 **95.3% ± 3.4%**임을 확인
- ROC-AUC 계산(`predict_proba` → `roc_auc_score`)
  → 불균형 데이터에서 accuracy가 갖는 한계를 보완하는 지표 적용
- Random Forest(앙상블) 모델 적용 및 비교
  → 정확도 96.7% ± 2.1%로 **성능 향상 및 분산 감소** 확인
- 두 모델의 특징 중요도 비교
  → 단일 트리는 특정 변수에 편중, Random Forest는 상관된 변수 간 중요도가 균형적으로 분산됨
