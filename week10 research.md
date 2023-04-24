# tracking  
***  
1.**트래킹**

**정의**  
  
 **tracker**는 우리가 지정한 어떤 것을 쫓아가는 것.
 **cameratracker**는 촬영을 했을때 카메라를 추출하는 것.
 
 * add tracker 추가 후 영역 안에 따라가게 만들고 싶은 이미지 올려놓기.
 * 잡고싶은 픽셀들중에 컨트라스트가 강한 이미지나 혹은 보편적으로 가운대를 잡는 편.
 * 작은 네모 안에는 들어갈 오브젝트를 찾아라! 따라가라! 명령하는 것이고 범위를 지정해줘서 색 대비가 큰 편일 수록 잘 따라간다.
 * 카메라가 항상 정속으로 움직이기 않기에 frame by frame으로 지나갔을때 처음에 지정했던 모양이 안쪽에 있을 수 있다라고 bounding 해주는 것이다.

<img src="http://hagbarth.net/wp-content/uploads/2013/10/OBJECT1.jpg">
 
 트래킹을 할때 viewer가 항상 우리가 트래킹하는 것을 보여주지는 않기 때문에 reference frame을 보고 영역이 업데이트 되는 것을 보여준다.
 위에 있는 버튼으로 진행을 시킨다.
 
 **신호등 아이콘**으로 트래킹이 잘 됐는지 점들의 위치를 확인할 수 있다.  
 
 **권투장갑에 x자 적힌 아이콘**은 트래킹 부분을 삭제할 수 있다. 내가 어느 부분부터 삭제하겠다를 정할 수 있다.  
 
 <img src="https://d2x313g9lpht1q.cloudfront.net/optimized/3X/a/b/abdb8dc9d81e4a8487c19d6146c16f8cdb3a5f23_2_690x659.png">
 
 tracker에서 transform중에 translate와 center 노드가 있는데 저기 위에 어떤 요소와 같은 위치에 배치를 할 수 있다.
 내가 트래킹하고 싶은 부분에 올려다놓고 그 위에 이미지를 올려놓고 값을 연결시키면 따라가게 된다.
 tracking 부분에서 export 창에서 transform을 선택해 stabilize (화면 안정화) matchmove (같은 애니메이션을 가진 노드 제작) 
 만약 이미지를 위에 덮고 싶으면 merge over을 통해 원하는 이미지를 화면상에 불러오고 
 transform을 통해 scale조절 후 trakcer노드를 연결해 matchmove export 노드를 연결해 주면 똑같이 화면상에서 트래킹해서 움직인다.
 frame hold 기능은 우리가 배경에서 따오고 싶은 이미지의 1프레임만 가져와서 쓰는 것이다. 왜냐면 배경의 이미지도 같이 움직이 때문에 트래킹을 같이 잡아주지 않을거면
 holding을 해주자.  
 two point stabilize 필요
 
 transform baked node는 구워버리기 때문에 직접적으로 키가 연결되어 있다. 수정 불가.
 만약에 매치무브 노드를 쓰고 싶지 않다 싶으면 transform노드안에 matchmove 노드의 translate 값과 center값의 커브를 ctrl키 누르고 복사해서 transform 노드안에 위치시켜주면 
 transform 노드도 tracker 역할을 할 수 있다.  
 
 two points tracker t와 r에 체크를 해주었고 
 
 three points tracker 역시 stabilzie 기능을 위한 t r s 값을 선택할 수 있는데 
 간판이나 판플렛 교체할때 stabilize 사용해서 위치 옮겨놓고 다시 역방향으로 stabilize 걸어주면 원본느낌대로 움직임.
 
 4 points는 connerpin 2d node사용이 가능한데 from 가서 set to input을 눌러주면 트래킹 정보가 매칭이 된다.  
 
 ***  
 **cornerpin2d**
 
<img src="https://github.com/yongyong1638/2d-digital-compsiting-research/blob/main/corner.PNG">  

* 처음 이미지 파일을 가져와서 렌즈의 왜곡을 잡아준다.  
* 트래커를 연결하고 Add track 4개를 해준다. 모서리에 맞춰서 트래킹해준다.   
* transform matchmove를 설치해주고 lens distorion을 맞춰준 plate와 합성할 footage를 
merge over시켜준다.  
* 그렇기하면 일단 달라붙긴하는데 크기가 다를 것이다.  
* 이 크기는 tracker에서 cornerpin2d (use transform ref frame) 이나 (current frame)등 코너핀을 합성할 footage에 연결해주고  
* from창으로 넘어가 set to input해주면 위치가 맞춰지고 cornerpin2d 창으로 넘어가 copy from을 해주면 to point 4개가 생기는데 이를 위치를 맞춰준다면 트래킹이 가능하다.  


   
 **CMAREA TRACKING** 
 3d camera tracking node
lens distortion을 먼저 해준 뒤
cameratracker node를 연결해준다.  
mask를 통해 마스킹 되는 부분을 설정해 줄 수 있고
camera part에 있는 것들 값을 다 지정해주고 
setting에서 점들의 위치와 넓이 정도를 만져주고
track시킨다.  
그다음 solve 버튼을 누르면 분석이 완료되는데
* 오렌지색 unsolved  
* 빨간색 reject  
* 초록색은 solved  
solve error 값을 1 밑으로 떨궈줘야 한다.  

error 값을 1밑으로 떨구려면 error max와 max error 값을 ctrl 키 누르면서 클릭을 하면 그래프가 뜬다.
그 다음 max error 값을 낮춰준 뒤 delete rejected
track lens min 과 min length를 클릭해서 min lenght 값을 높혀주고 delete rejected
마지막으로 error max와 max error ctrl를 클릭해서 max track error 값을 낮춰준다. delete rejected 하여 최종적으로 error 값을 1밑으로 낮춘다.  

그 다음 밑에서 create scene해주면 scene과 camera 노드가 생긴다.  
scene을 1번 뷰포트로 연결하고 camera tracking을 2번 뷰포트로 연결한다.   
그다음 씬을 a에 넣고 stack over 누르고 camera tracker을 b에 넣는다.  
그다음 바로 밑에 default를 카메라로 바꿔준 뒤 오른쪽 캠코더 모양 눌러주면 시점이 카메라 시점으로 바뀐다.  


다시 camera tracker로 돌아와서 camera tracker 탭에 있는 scene 들어가서 rotate y축을 조절하여 그래프를
영상과 평행하게 만들어준다.   
그 다음 camera tracker에서 바닥 부분이 제일 많은 프레임에서 바닥을 shift 누르며 선택한 뒤 우클릭 ground plane set to selected 해서 핑크색으로 바닥이 생겼으면
tab 눌러서 modelbuildergeo node를 만들어준 뒤 cam과 src를 각각 camera와 cameratracker에 달아준다.  

왼쪽 측면창에서 create card 해준 뒤 내가 따라갔으면 하는 부위에 그래프를 올려서 모양을 맞춘다.  
모양을 맞출때는 2개이상의 프레임 레인지를 설정해 주어야지 누크가 알아서 tracking한다.    
그 다음 tracking이 얼추 된다면 modelbuilder 탭에 안에 card1을 선택한 뒤 selected geometry를 bake 해준다.  

그러면 modelbuilder노드가 하나 더 생기는데 그 노드에다가 우리가 합성 할 footage를 연결해준다.  
그 다음 scanlinerender을 만들어 준 뒤 화면 속에 합성할 푸티지가 보이는지 확인한다.   
그 다음 merge over를 원본 plate에서 lens distortion한 것에 b를 연결하고 a를 scanlinerender에 붙이면
화면 속에서 합성되어 보인다.  



 

 
 <img src="https://preview.redd.it/ctt8hfsn1ei21.png?width=2484&format=png&auto=webp&s=8be02503f4e3d4036f80f0707d5ba60dd37b378e">
 
 
 
