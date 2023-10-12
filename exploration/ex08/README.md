# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 이동희 
- 리뷰어 : 리뷰어의 이름을 작성하세요.


# PRT(Peer Review Template)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 1. 한국어 전처리를 통해 학습 데이터셋을 구축하였다.(o)
      ![image](https://github.com/leedh/aiffel/assets/68997408/26f1a59f-6020-4849-bfb6-9487498aa350)

    - 2. 트랜스포머 모델을 구현하여 한국어 챗봇 모델 학습을 정상적으로 진행하였다.
      ![image](https://github.com/leedh/aiffel/assets/68997408/93e2eaeb-c2db-44e3-bac0-847d29de6843)

    - 3. 한국어 입력문장에 대해 한국어로 답변하는 함수를 구현하였다
      ![image](https://github.com/leedh/aiffel/assets/68997408/be1858f7-f1a3-4957-b31c-6c78791f2ab8)
  
    
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    ![image](https://github.com/leedh/aiffel/assets/68997408/8f8fb500-4c9f-4662-ab1f-dfa3d2214df7)

        
- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    ![image](https://github.com/leedh/aiffel/assets/68997408/213e403a-478d-4d70-a2fc-9c22393abf48)

        
- [x]  **4. 회고를 잘 작성했나요?**
    ![image](https://github.com/leedh/aiffel/assets/68997408/6af917c1-6dbd-4df3-a1d5-0e8b1980a4c9)

        
- [x]  **5. 코드가 간결하고 효율적인가요?**
    ![image](https://github.com/leedh/aiffel/assets/68997408/d88ae165-8e1e-411c-8358-19508d0eca1c)



# 참고 링크 및 코드 개선
> 테스트 할 때 이 코드 사용해보시면 좋을 것 같습니다
```python
first_sentence =  '뭐해 빨리 공부해야지?'

print('--------- 1 conv ---------')
_ = sentence_generation(first_sentence)

for i in range(10):
    print(f'--------- {i+2} conv ---------') 
    output = sentence_generation(input())
```

> 수고 많으셨습니다!!
