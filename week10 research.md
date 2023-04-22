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
 
<img src="https://github.com/yongyong1638/2d-digital-compsiting-research/blob/main/corner.PNG">
* 처음 이미지 파일을 가져와서 렌즈의 왜곡을 잡아준다.  
* 트래커를 연결하고 Add track 4개를 해준다. 모서리에 맞춰서 트래킹해준다.   
* transform matchmove를 설치해주고 lens distorion을 맞춰준 plate와 합성할 footage를 
merge over시켜준다.  
* 그렇기하면 일단 달라붙긴하는데 크기가 다를 것이다.  
* 이 크기는 tracker에서 cornerpin2d (use transform ref frame) 이나 (current frame)등 코너핀을 합성할 footage에 연결해주고  
* from창으로 넘어가 set to input해주면 위치가 맞춰지고 cornerpin2d 창으로 넘어가 copy from을 해주면 to point 4개가 생기는데 이를 위치를 맞춰준다면 트래킹이 가능하다.  
* 
   
 **CMAREA TRACKING** 
 
 2d차원에 3d차원 오브제를 넣을때 nuke x에서 사용할 수 있다.
 camera tracking 안에 preview feature를 선택을 해주면 트래킹 가능한 것의 포인트를 알려준다.
 카메라의 정보를 입력해주어야 더 수월한 카메라 트래킹이 이루어진다.
 auto track 에서 최소값과 최대값 설정을 해주고 delete rejected 해주면 초록부분이 남는다.
 export에서 scene으로 설정을 해주고 
 바닥으로 지정하고 싶은 feature을 잡아서 viewer에 연결해주고 우클릭 후 ground 부분 설정후 set to selected해주면 선택한 영역들이 바닥으로 깔리게 된다.
 point cloud는 3d 카메라 영역에서 이정도 위치에 feature가 있다라고 알려주는 것.
 3d 오브젝트들 중 scan light render와 scene과 camera가 연결되어 있어야 2d 화면에서 볼 수 있다. 
 transform geo 노드는 3d의 오브젝트의 transform을 관여할 수 있는데 일반적인 node는 붙지 않는다.
 
 <img src="https://preview.redd.it/ctt8hfsn1ei21.png?width=2484&format=png&auto=webp&s=8be02503f4e3d4036f80f0707d5ba60dd37b378e">
 
 
 
