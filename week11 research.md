# tracking and 3d scene making  
<img src="https://lesterbanks.com/lxb_metal/wp-content/uploads/2015/07/Linking-Tracking-Data-in-Nuke.jpg">  

**tracking**  

트래커를 각 트래킹 시킬 이미지 위에 올려주고 범위를 지정해서 랜더링을 시킨다.
properties 에서 
from 박스를 선택 후 set to input해서 해상도를 맞춰주고
이미지가 바운딩박스에 있는 to 점들을 움직여 위치를 맞춰준다.
conerpin 2d를 만들었다면 copy from을 해준 뒤 
코너핀 2개를 사용한다 했을때 애니메이션을 만든 코너핀 1개랑
위에다가 배경과 사이즈를 맞출 코너핀 1개를 더 만들어 준 뒤 merge시켜 주면 된다.
코너핀 끼리는 연결되어 있으면 값이 공유된다.  
<img src="https://learn.foundry.com/nuke/12.1/content/resources/images/ug_images/tracker_cornerpin1.png">


한두 픽셀 밀리는 지점들은 직접 옮겨주면서 코너핀에 있는 것들의 프레임들 내에 set key 키를 잡아준다. 방향키를 사용해서 키의 값들을 조절할 수 있다.
그다음 타임라인을 넘기며 삐져나간 모서리 부분의 트래커를 잡아준다.
영상 화면속에서 크로마키가 너무 흔들리면 stabilize를 사용하고 나서 
그 노드를 다시 복사하여 invert 해주면 원상태로 돌아온다.  
transformgeo NODE는 3d 오브젝트의 변형을 할 수 있다.  


3D CAMERA에서 PREFERENCE SETTING시 마야랑 똑같이 조작할 수 있다. 3d cam은 누크x에서만 사용가능.
포토샵에서 메트페인팅한 노드들 보면 shuffle 노드를 통해서 각각의 레이어들을 배치를 하고 card 이미지를 만들어서 레이어층을 배치할 수 있다.  
그러면 card 이미지는 3d이기 때문에 camera tracking scene에 넣어줄 수 있다.  
근데 이미지들이 안 맞으면 일일히 맞추는게 시간이 오래 소요되는데  
card z값을 활용하면 멀어지면서 스케일 조정이 같이 된다. 이미지 왜곡이 있는게 아니니까 z값을 이용해서 depth를 표현할 수 있다.
shuffle 노드 안에 [value in1] 해주면 각각의 셔플노드에 네이밍이 맞춰진다.  

project 3d3 node

투사할 이미지의 2d 이미지와 projectioncam과 project3d3
랜더캠과 프로젝트캠의 차이를 잘 이해해야 하는데 카메라를 벌리는 부분은 랜더캠의 부분을 수정해야한다.
프로젝트 실린더를 통해서 화면에 보이는 값을 조절한다. 이걸로 카메라를 움직이는 z값 이미지를 만들어서 들어가는 영상을 만들 수 있다. 

모션 블러 노드를 사용하여 카메라 트레킹 시 더 자연스러운 화면 연출가능.  

트래킹 기능을 할때 영역을 지정하고 
>r range에서 프레임을 지정해서 트래킹을 사용

항상 작업 방식은 색깔이 같은 노드끼리 붙여줘야 한다.
로토에서 e키 누르면 페더값 늘어나고 z를 누르면 베지어가 스무스가 된다.
merge node를 사용할때 opperation 중 bounding box를 b에 맞추어 작업을 해주면 
영상의 랜더 속도를 높힐 수 이다.

셔플 노드의 역할
rgb에 아무 알파 값이 없는 것들의 alpha를 rgba 안에 넣어주는 것인데 
셔플은 이미지 바로 밑에 연결하는 것이 좋다.
alt e를 누르면 초록 연결선을 끊을 수 있다.

노드를 누르고 label을 해주면 노드 분별 쉬움.

postagestamp 노드는 read 노드랑 똑같이 생겼는데 input을 read node에 연결해주면 
같은 푸티지가 2개 생성된다. 그리고 hide input 해주면 연결이 끊겨 보인다.

