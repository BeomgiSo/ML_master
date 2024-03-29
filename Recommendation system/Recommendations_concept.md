# 추천시스템

## 추천시스템의 개요

- 사용자의 취향을 이해하고 맞춤상품과 콘텐츠를 제공해 조금이라도 고객을 사이트에 머르게 하기 위해 노력한다.
- 추천시스템의 묘미는 사용자 자신도 좋아하는 몰랐던 취향을 시스템이 발견하고 그에 맞는 콘텐츠를 추천하는것
- 결국 더 많은 데이터가 추천 시스템에 축적되면서 추천이 더욱 정확해지고 다양한 결과를 얻을 수 있다.
- 추천 시스템 구성하는데 사용될 수 있는 특징들
    - 사용자가 어떤 상품을 구매했는가?
    - 사용자가 어떤 상품을 둘러보거나 장바구니에 넣었는가?
    - 사용자가 평가한 영화의 평점은? 제품의 평가는?
    - 사용자가 스스로 작성한 자신의 취향은?
    - 사용자가 무엇을 클릭했는지?


### 추천시스템의 유형

- 콘텐츠기반 필터링(Content based filtering)과 협업 필터링(Collaborating Filtering) 방식으로 나뉨
- 협업 필터링 방식은 최근접 이웃(Nearest Neighbor) 협업 필터링과 잠재요인(Latent Factor) 협업 필터링으로 나뉨

- 초창기에는 콘텐츠 기반 필터링이나 최근접 이웃 기반 협업 필터링이 주로사용
- 넷플릭스 추천 시스템 경영 대회에서 행렬 분해(Matrix Factorization)기법을 이요한 잠재 요인 협업 필터링 방식이 우승을 차지
- 대부분의 온라인 스토어에서 잠재 요인 협업 필터링 기반의 추천시스템 적용
- 하지만 서비스하는 아이템의 특성에 따라 컨텐츠기반 필터링이나 최근접시스템을 적용

## 컨텐츠 기반 필터링 추천 시스템

- 컨텐츠 기반 필터링 방식은 사용자가 특정한 아이템을 매우 선호하는 경우, 그 아이템과 비슷한 컨텐츠를 가진 아이템을 추천하는 방식
    - 사용자가 특정 영화에 높은 평점을 주었다면, 그 영화의 장르, 출연 배우, 감독, 영화 키워드 등의 콘텐츠와 유사한 다른 영화를 추천하는 방식

## 최근접 이웃 협업 필터링

- 친구들에게 물어보는 것과 유사한 방식으로, 사용자가 아이템에 매긴 평점 정보나 삼품 구매 이력과 같은 사용자 행동 양식(User Behavior)만을 기반으로 추천을 수행하는 것이 협업 필터링(Collaborative Filtering) 방식이다.

- 협업 필터링의 주요 목적은 사용자-아이템 평점 매트릭스와 같은 추척된 사용자가 행동 데이터를 기반으로 사용자가 아직 평가하지 않은 아이템을 예측하는 방식(Predicted Rating)

- 협업 필터링 기반의 추천 시스템은 최근접 이웃 방식과 잠재 요인 방식으로 나뉘며, 두 방식 모두 사용자-아이템 평점 행렬 데이터에만 의지해 추천을 수행

- 사용자가 아이템에 대한 평점을 매기지 않기 때문에 희소행렬(Sparse Matrix)의 특성을 가지고 있다.

- 최근접 이웃 협업 필터링은 메모리(Memory) 협업 필터링이라고도 하며, 일반적으로 사용자 기반과 아이템기반으로 다시 나눠질 수 있다.

    - 사용자 기반(User-User) : 당신과 비슷한 고객들이 다음 상품도 구매했습니다.
        - (Customers like you also bought these items)
    - 아이템 기반(Item - Item) : 이 상품을 선택한 다른 고객들은 다음 상품도 구매했다.
        - (Customers who bought this item also bought these items)

- 사용자 기반 최근접 이웃 방식은 특정 사용자와 유사한 다른 사용자를 Top-N으로 선정해 이 Top-N 사용자가 좋아하는 아이템을 추천하는 방식
- 즉, 특정 사용자와 타 사용자간의 유사도를 측정한뒤 유사도가 높은 Top-N 사용자를 추출해 그들이 선호하는 아이템을 추천

- 일반적으로 사용자 기반보다는 아이템 기반 협업 필터링의 정확도가 높다.
    - 비슷한 상품을 구입한다고 해서 삼들이 취향이 비슷하다고 판단하기 어려운 경우가 많기 떄문이다. 예를들어, 비슷한 상품을 구입한다고해서 사람들의 취향이 비슷하다고 판단하기 어려운 경우가 많기 때문이다.
    - 매우 유명한 영화는 취향과 관계없이 대부분의 사람이 관람하는 경우가 많고, 사용자들이 평점을 매긴 상품의 개수가 많지 않은 경우가 일반적인데 이를 사용자 기반 협업 필터링을 사용한다.