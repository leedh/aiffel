# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 이동희
- 리뷰어 : 임정훈


# PRT(Peer Review Template)
- [ ]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
        - 네 첨부되어 있습니다.
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
    퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
        
> 1. pix2pix 모델 학습을 위해 필요한 데이터셋을 적절히 구축하였다. 데이터 분석 과정 및 한 가지 이상의 augmentation을 포함한 데이터셋 구축 과정이 체계적으로 제시되었다. -> O
> 2. pix2pix 모델을 구현하여 성공적으로 학습 과정을 진행하였다. U-Net generator, discriminator 모델 구현이 완료되어 train_step의 output을 확인하고 개선하였다. -> O
> 3. 학습 과정 및 테스트에 대한 시각화 결과를 제출하였다. 10 epoch 이상의 학습을 진행한 후 최종 테스트 결과에서 진행한 epoch 수에 걸맞은 정도의 품질을 확인하였다. -> O
        
        
    
- [ ]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        
    - 네 잘 달려 있습니다. 코드의 기능이 잘 적혀 있습니다.
     
```python
    @tf.function # 빠른 텐서플로 연산을 위해 @tf.function()을 사용합니다. 

    # 하나의 배치 크기만큼 데이터를 입력했을 때 가중치를 1회 업데이트하는 과정
    def train_step(sketch, real_colored):
    with tf.GradientTape() as gene_tape, tf.GradientTape() as disc_tape:
        # Generator 예측
        fake_colored = generator(sketch, training=True)
        # Discriminator 예측
        fake_disc = discriminator(sketch, fake_colored, training=True)
        real_disc = discriminator(sketch, real_colored, training=True)
        # Generator 손실 계산
        gene_loss, l1_loss = get_gene_loss(fake_colored, real_colored, fake_disc)
        gene_total_loss = gene_loss + (100 * l1_loss) # L1 손실 반영 lambda=100
        # Discrminator 손실 계산
```


- [ ]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        
     - 원인과 해결과정은 따로 적혀 있지 않습니다.
     - 추가적으로 LOSS값을 시각화 하였습니다
```python
     # epoch에 따른 loss 시각화
    x_len = np.arange(len(history['l1_loss']))
    plt.plot(x_len, history['gen_loss'], marker='.', c='blue', label="Generator Loss")
    plt.plot(x_len, history['l1_loss'], marker='.', c='red', label="L1 Loss")
    plt.plot(x_len, history['disc_loss'], marker='.', c='green', label="Discriminator Loss")

    plt.legend(loc='upper right')
    plt.grid()
    plt.xlabel('epoch')
    plt.ylabel('loss')
    plt.show()
```
        
- [ ]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        
    
    - 잘 적혀 있습니다    
 > ResNet에서 사용한 skip connection이 U-net에서도 쓰이는 걸 알았다. 생성모델에서도 쓰인다는 점이 신선했다. 그리고 단일 픽셀이 아닌 주변 픽셀까지 포함한 Patch를 계산해서 생성을 고려한다는 점을 배웠다. 코드 상에서는 epoch를 늘릴 수록 생성이미지의 품질이 그럴듯하게 바뀌는 과정이 신기했다.
    -실행 플로우는 따로 그리지 않았습니다.
        
- [ ]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
        
    - 네 모두 잘 준수하였습니다
```python
    class Discriminator(Model):
    def __init__(self):
        super(Discriminator, self).__init__()
        
        filters = [64,128,256,512,1] # filter sizes
        self.blocks = [layers.Concatenate()]
        
        # for문을 통한 blcok 쌓기
        for i, f in enumerate(filters):
            self.blocks.append(
                DiscBlock(
                    n_filters=f,
                    stride=2 if i < 3 else 1,
                    custom_pad=False if i < 3 else True,
                    use_bn=False if i==0 and i==4 else True,
                    act=True if i < 4 else False
            ))
        self.sigmoid = layers.Activation(activation='sigmoid') # 마지막은 sigmoid
        
    
    def call(self, x, y):
        out = self.blocks[0]([x, y])
        out = self.blocks[1](out)
        out = self.blocks[2](out)
        out = self.blocks[3](out)
        out = self.blocks[4](out)
        out = self.blocks[5](out)
        return self.sigmoid(out)
    
    def get_summary(self, x_shape=(256,256,3), y_shape=(256,256,3)):
        x, y = Input(x_shape), Input(y_shape) 
        return Model((x, y), self.call(x, y)).summary()
```

# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
Epoch수가 작아서 loss값의 그래프가 크게 눈에 뛰지 않습니다. 값을 더 크게 해서 하면 좋을 것 같습니다.
```
