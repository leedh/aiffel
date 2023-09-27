# AIFFEL Campus Online Code Peer Review 
- 코더 : 이동희
- 리뷰어 : 정호재


# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
    퀘스트 문제 요구조건 등을 지칭
        ![screenshot](score.png)
    
- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        ```python
        # 그리드서치 계산해주는 함수
def my_GridSearch(model, train, y, param_grid, verbose=2, n_jobs=5):
    # GridSearchCV 모델로 초기화
    grid_model = GridSearchCV(model, param_grid=param_grid, scoring='neg_mean_squared_error', \
                              cv=5, verbose=verbose, n_jobs=n_jobs)
    
    # 모델 fitting
    grid_model.fit(train, y)

    # 결과값 저장
    params = grid_model.cv_results_['params']
    score = grid_model.cv_results_['mean_test_score']
    
    # 데이터 프레임 생성
    results = pd.DataFrame(params)
    results['score'] = score
    
    # RMSLE 값 계산 후 정렬
    results['RMSLE'] = np.sqrt(-1 * results['score'])
    results = results.sort_values('RMSLE')

    return results
    ```
        
- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 하이퍼 파라미터 범위 추가
        ```python
        param_grid = {
            'n_estimators': [50, 100, 150],
            'max_depth': [1, 10, 20],
        }

        model = lightgbm # 모델
        my_GridSearch(model, data[:train_len], y, param_grid, verbose=2, n_jobs=5)
        ```
        
- [X]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        ```
        모델 성능을 향상시키기 위해서 피쳐엔지니어링과 하이퍼파라미터 튜닝의 중요성을 뼈저리게 느꼈다. 데이터 변수마다의 의미를 정확히 파악하고 전처리를 더 해야겠다. 시간이 생각보다 많이 들어서 다음번에 할 때 더 효율적으로 해결할 수 있는 방법을 모색해봐야겠다. 로그를 씌워서 치우친 분포를 정규분포처럼 만드는 부분이 인상적이었다. 그리드서치하는 부분에서 어떤 하이퍼파라미터를 미리 설정해놔야할지 감이 없었다. 앙상블 모델에 대한 이해를 높일 수 있어서 유익했다.
        ```
        
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
        ```python
        def AveragingBlending(models, x, y, sub_x):
        for m in models : 
            m['model'].fit(x.values, y) 
        predictions = np.column_stack([
            m['model'].predict(sub_x.values) for m in models
        ])
        return np.mean(predictions, axis=1) # 모델들 예측 결과값의 평균값 반환
        
        ```
