# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 이동희
- 리뷰어 : 류의성


# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
    퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
     
프로젝트 1의 회귀모델 예측정확도가 기준 이상 높게 나왔는가? MSE: 2951.7660
프로젝트 2의 회귀모델 예측정확도가 기준 이상 높게 나왔는가? RMSE: 149.91495105433168
시각화 요구사항이 정확하게 이루어졌는가? 네.
    
- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
"""
losses = []

for i in range(1, 10001):
    dW, db = gradient(X_train, W, b, y_train)
    W -= LEARNING_RATE * dW
    b -= LEARNING_RATE * db
    L = loss(X_train, W, b, y_train)
    losses.append(L)
    if i % 500 == 0:
        print('Iteration %d : Loss %0.4f' % (i, L))
        #learning rate을 0.1로, iteration을 10000번으로 하니 겨우 원하는 성능 만족

"""
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        
- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
→ 자료 내 특정 요인들 간 비교 
###
import matplotlib.pyplot as plt

plt.title('temperature')
plt.scatter(X_test['temp'], y_test, label="true")
plt.scatter(X_test['temp'], predictions, label="predicted")
plt.legend()
plt.show()
![image](https://github.com/Garlic-Ryu/aiffel_review/assets/112372749/9e0348f6-6ac6-4065-9aff-42d9d3dea661)

plt.title('humidity')
plt.scatter(X_test['humidity'], y_test, label="true")
plt.scatter(X_test['humidity'], predictions, label="predicted")
plt.legend()
plt.show()
![image](https://github.com/Garlic-Ryu/aiffel_review/assets/112372749/457bd8a1-8c39-410b-a45c-c5e05f04470a)

###        
- [X]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        
Project1. 분명히 예전 노드에서 배웠는데 자주 안쓰니까 잊어버렸다. 간단하고 자주쓰이는 코드는 암기해서 번거롭게 예전 자료 안찾아보고 쓸 수 있도록 해야겠다. 
학습을 잘 시켜서 성능을 높이기 위해서 learning rate과 iteration을 적절히 바꿔줘야한다는걸 배웠다. 전체적으로 무리없이 잘 코드를 작성하여 만족한다.

Project2. 다변수선형모델에서 scikit-learn을 써서 간단히 써볼 수 있는 프로젝트였다. 변수를 적절히 골라서 예측 성능을 높이는 부분이 인상깊었다. 
시각화 결과를 보기좋게 하기 위해 figure size 바꾸는거나 title을 달았다. 이 외에도 다른 옵션들을 살펴본 후 다음 프로젝트 때는 좀 더 예쁘게 꾸며봐야겠다.

- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
'''
W = np.random.rand(10)
b = np.random.rand()

def model(X, W, b):
    predictions = 0
    for i in range(10):
        predictions += X[:, i] * W[i] 
    predictions += b # y = WX + b
    return predictions

def MSE(a, b):
  mse = ((a - b) ** 2).mean()  # 두 값의 차이의 제곱의 평균
  return mse

def loss(x, w, b, y):
  predictions = model(x, w, b)
  L = MSE(predictions, y)
  return L

def gradient(X, W, b, y):
    # N은 데이터 포인트의 개수
    N = len(y)
    
    # y_pred 준비
    y_pred = model(X, W, b)
    
    # 공식에 맞게 gradient 계산
    dW = 1/N * 2 * X.T.dot(y_pred - y)
        
    # b의 gradient 계산
    db = 2 * (y_pred - y).mean()
    return dW, db
'''
# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# https://velog.io/@yuns_u/%ED%8F%89%EA%B7%A0%EC%A0%9C%EA%B3%B1%EC%98%A4%EC%B0%A8MSE-%ED%8F%89%EA%B7%A0%EC%A0%88%EB%8C%80%EC%98%A4%EC%B0%A8MAE
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
