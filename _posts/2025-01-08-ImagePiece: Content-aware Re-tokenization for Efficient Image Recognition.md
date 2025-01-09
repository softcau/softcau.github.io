**논문 제목 : ImagePiece: Content-aware Re-tokenization for Efficient Image Recognition**

**Abstract**   
ViT의 huge computational cost를 줄이기 위해, 효율적인 token pruning 이나 token merging을 통해 토큰의 수를 줄이기 위한 연구가 진행되고 있음.   
그럼에도, ViT 토큰들은 non-overlapping grid patches에서 생성되기 때문에, 충분한 의미를 담기 어려움.   
따라서, 본 논문에서는 ImagePiece라는 새로운 방법을 제시함. 이는 NLP의 MaxMatch 전략을 차용하여,
semantically insufficient yet locally coherent tokens(의미론적으로 불충분하지만 지역적으로 일관된 토큰
)들을 의미를 전달할 때까지(의미 있는 토큰이 될 때까지) 그룹화함.   

**주요 기법**   
1. Re-tokenizing Non-semantic Tokens   
Step 1. 토큰 중요도 평가 : CLS 토큰과의 attention 점수를 기반으로 의미가 부족한 토큰 식별.   
Step 2. 그룹화 및 병합 : 의미가 부족한 토큰을 두 그룹으로 나누어 유사한 토큰을 병합.   
Step 3. Recalculate : 병합 후 의미가 생긴 토큰은 보존하고, 여전히 의미 없는 토큰은 제거.   

2. Local Coherence Bias   
indiviual scope 에서 의미를 구분하기 힘든 패치의 경우, 주변의 패치들과 함께 고려된다면 의미있는 정보를 담을 수 있음.   
이전 연구에서 진행되었듯이 token을 drop-out하는 전략을 쓰는 대신, non-semantic token들을 빠르게 지역적으로
인접한 토큰과 합쳐 초기 트랜스포머 레이어에서 의미를 형성하는 데 기여함.

**실험 결과**   
기존 기법(DynamicViT, ToMe) 대비 정확도 및 속도 모두 우수하게 나타남.
