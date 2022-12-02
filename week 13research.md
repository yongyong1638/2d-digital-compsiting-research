# ggul tip  

***  
**segmentation object dection**  
ai의 발달 -> nlp? gen 적대적 인공지능 모델.
조건을 넣으면 이미지를 만들어주는 것. 
ai의 자율 주행에 사용되는 것-> 컴퓨터가 rgb 외에 유틸리티를 실시간 분석하여 차를 운전.  

**copycat node**  
groundtruth input 2가지의 가지가 있는데
start training 기능이 있는데 copycat은 바닥진실이 정답 혹은 에프터 이미지고 input이 비포 이미지이다.
2개를 줘서 인공지는 모델에게 훈련을 시켜 이미지를 뽑는 것.
input이 원본이미지인데 rgb채널만 있고 a 채널이 없는 값의 이미지 대략 6장과
groundtruth가 rgb채널 중 r채널에 해당하는 부분의 로토스코핑을 통해 얻어낸 input이미지와 동일한 이미지의 alpha값을 연결시켜서

training 시키면 6장 정도의 이미지로 한 씬의 대부분의 alhpa 이미지를 추출 가능하다.

copycat의 노드중 그래프 노드 들어가면 loss값이 줄어드는 것을 볼 수도 있는데 이는 truth와 input의 차이가 줄어듬을 의미한다.

gatemedia.co.uk에서 명령어를 가져와 누크에 expression을 주어 animation을 만들 수 있다.  

누크에서 transform 노드중 translate에 x y값을 우클릭 한 후 add expression을 설정한 뒤 사이트에서 얻은 
x,y 키 값을 가져와 입력해주면 애니메이션이 생긴다.

**머싱 러닝과 딥러닝의 차이?**
