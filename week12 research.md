# 3d object compositing
3d 오브젝트들에 여러 map들이 있는데 aov를 활용하면 좋다.  
id 맵과 normal을 활용하면 랜더하고 후에 합성할때 용이하다.  
3d object의 합성 전 jpg-> unpremult-> (color grade color correct등 색에 대한 보정을 하고)-> premult 해주어야 오브젝트의 배경에 자연스럽게 붙는다.  
unpremult는 이미지의 외곽을 조금 더 늘려 랜더링 해주는 것이다.  
그러면 이미지 외곽에 검은색 윤곽이 생기는데 이를 color grading을 통하여 값을 맞춰준 뒤 premult해서 끊어내야 깨끗하게 오브젝트가 배경과 붙는다.  
sharpen
log2lin filter
(log에서 linear로 바꿀 수 있는 것)

(누크에서 작업하는 이미지들은 다 linear파일인데 long2lin필터를 사용하여 operation을 lin2log을 하여 log파일로 바꿔서 color grade을 해주고 
다시 log2lin하여 우리가 작업하는 원본 이미지인 linear파일로 바꿔주어야 한다.)

**shuffle**노드로 기본적으로 다 쪼갠다음에 merge(plus)를 통해서 오브젝트들을 합성해주는데.
basecolor metalness specular emission normal roughness 등등 여러 노드를 셔플 해주어서 값들을 쪼개주고
각각의 노드들에서 mood를 create 후 merge 통해서 합성시킨 후 copy노드를 통해 alpha값을 불러오고 premult 해준 뒤 후에
normal path 한해서 colormatrix 계산 행렬해주는 것인데 axis노드랑 같이 사용
matrix에 차례대로 1 0 0
                 0 1 0
                 0 0 1 값을 적용해주면 normap이 보여지는데 axis는 마야의 locater와 같은 역할을 해주며 
                 local matrix에 specify matrix 컨트롤키 눌러서 드래그 해주어 원래 matrix 안에 넣어주면  
position to points node

maya에서 준 camera 값을 누크에서 넣는 법
fbx 노드는 maya에서 만든 추출 포멧인데 cache export selection alex 
해주어 카메라 값을 뽑고 nuke에서 camera object를 생성 후 read from file해서 maya에서 추출한 카메라의 값을 연결해주면 마야의 값이 그대로 연결된다.

nuke normal path compositing
nuke 3d compositing 
utility node들.

질문할게 프레임 재생하는거 미루는 노드가 time 관련 노드들을 다 써봤는데 안밀린다.
만약에 1프레임부터 1000프레임중에 200에서 300프레임 사이에 합성이미지가 재생되고 나갔으면 좋겠다할때 저번에 보여주셨던 노드 사용법?

1가지 이미지를 불러와서 배경과 컬러코렉트를하고 
              
