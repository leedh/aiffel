# AIFFEL Campus Online Code Peer Review
- 코더 : 이동희
- 리뷰어 : 정호재


# PR(Peer Review)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
    퀘스트 문제 요구조건 등을 지칭
        - CAM을 얻기 위한 기본모델의 구성과 학습이 정상 진행되었는가? (O)
        ![img1](./assset/img1.png)   
        - 분류근거를 설명 가능한 Class activation map을 얻을 수 있는가? (O)  
        - 인식결과의 시각화 및 성능 분석을 적절히 수행하였는가? (O)
        ![img2](./assset/img2.png)   
        
    
- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
      ![img2](./assset/img4.png) 
        
- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
    ```python
        def get_iou(gt_bbox, pred_bbox):
        # overlap 영역 계산
        x_i = max(gt_bbox[0], pred_bbox[0])
        y_i = max(gt_bbox[1], pred_bbox[1])
        x_f = min(gt_bbox[2], pred_bbox[2])
        y_f = min(gt_bbox[3], pred_bbox[3])

        overlap_area = max(0, x_f - x_i + 1) * max(0, y_f - y_i + 1)

        # 각 box의 area계산하기
        gt_bbox_area = (gt_bbox[2] - gt_bbox[0] + 1) * (gt_bbox[3] - gt_bbox[1] + 1)
        pred_bbox_area = (pred_bbox[2] - pred_bbox[0] + 1) * (pred_bbox[3] - pred_bbox[1] + 1)

        # Area of Union 계산하기
        union_area = gt_bbox_area + pred_bbox_area - overlap_area

        # IOU 계산
        iou = overlap_area / union_area
        return iou
     ```
         
        
- [X]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - ![img3](./assset/img3.png)  
        
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
        네, 준수하였습니다.
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
        ```python
        def compare_results(img):
        print('the number of image: ', img['label'])
    
        plt.figure(figsize=(12,8))
    
        fig_x = 12
        fig_y = 8
    
        plt.subplot(3,3,2)
        plt.imshow(img['image'])
        plt.title('Original Image')
        plt.axis('off')
        #plt.show()

        ...
    ```


# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
