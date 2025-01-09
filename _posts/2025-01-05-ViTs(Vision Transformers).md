---
layout: categories
title:  "ViTs(Vision Transformers)"
---

(1) 기본 개념   

ViT는 NLP에서 주로 사용되었던 Transformer를 Computer vision 분야에 적용한 모델이다. CNN을 사용하지 않고 Transformer의 multi-head self-attention을 수행하여 우수한 퍼포먼스를 보였다는 의의가 있다.

![image](https://github.com/user-attachments/assets/3b83a0c6-dfb6-4bd6-9069-be6a6686d590)

Input 이미지를 같은 크기의 패치 이미지로 나누고, 이미지 패치로부터 임베딩 벡터를 만든다. 패치 임베딩과 더불어 추가로 CLS token(분류 토큰) 및 Position Embedding(각 패치가 원래 이미지 내에서 어디에 위치했는지를 의미)을 추가한다. 패치들은 transformer encoder에 입력되고, 이들은 정규화 후 하나의 sequence로 concatenate된다. 이후 patch들 간의 관계 학습을 위해 self-attention이 수행된다. skip-connection과 normalization 이후 최종 Output이 도출된다.   

모든 patch들 간의 관계나 위치 정보는 모델이 학습을 통해 직접 알아내야 한다. 따라서, 데이터가 충분하지 않다면 학습에 어려움이 있을 수 있다.   

(2) Token Pruning, Token Merging
Token Pruning은 중요도가 낮은 토큰을 제거하거나 무시함으로써 계산량을 줄이는 방법이다.   
Token Merging은 중요도가 낮은 토큰들을 합병하여 정보를 집약시키는 방법이다. 
