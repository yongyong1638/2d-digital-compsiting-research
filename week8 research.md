# tracking and match move
ibk colour 그림 배경 위에 얹어 있는 인물의 이미지 차이를 이용하여 알파값을 뺴는 것.
그레이드노드에서 채널을 알파로 바꿀 수 있는데 rgb를 냅두고 alpha값만 조절이 가능하다.

키 작업을 하고 확인을 해줘야 하는게 뷰어상에서 시컴해 보이지만 y값 루미넌스를 올려서 알파 채널의 하얗게 뜬 부분을 잡아주어야한다.
copy 노드를 사용하여 원본 소스를 가져온 다음에 우리가 작업을 하여 만든 키 값의 alpha값만 연결시켜서 원본 색상을 살리면서 구멍만 내는 기능을 할 수 있다.
HUE CORRECT채널에서 r sup g sup b sup중에 g sup의 값을 떨구면 초록색이 빠진다.
ctrl alt키를 누르고 그래프를 체크하면 우리가 원하는 부분에 점을 찍을 수 있다.

그래서 우리가 항상 알파값 추출을 하는 이미지와 원본 소스를 가져오는 노력을 통해 COPY 노드를 사용하자
소프트 매트를 사용할때 조심해야하는 것은 디테일을 살릴려고 값을 많이 안낮추면 배경이 알파값이 덜 빠져서 합성시 색이 뜰 수 있다.


ERODE FILTER는 하드 매트에 써주는 것인데 ERODE를 통해서 하드 키의 알파값을 안으로 줄여주어 소프트와 합쳐줬을때 경계선이 너무 튀지 않도록 해주는 것이다.
KEYMIX는 소프트 매트에 써주는 것인데 KEYLIGHT으로 배경의 값을 뺏다면 KEYMIX를 통해서 여러개의 KEYLIGHT작업한 것들을 합쳐서
마지막에 CHANNEL MERGE를 통해서 다 합쳐준뒤 합칠 배경의 이미지와 MERGE OVER을 통해 합쳐주면 된다.  

https://github.com/LumaPictures/LumaNukeGizmos.git  누크 루마누크기즈모
https://github.com/CreativeLyons/NukeSurvivalToolkit_publicRelease.git 누크 서바이벌키트

merge operation 중에 lightwrap기능 공부할 것.

노드 선택 후 shift s누르면 a b가 바뀐다.

shift s누르면 preference 창이 뜨는데 nodes 창을 보면 new merge nodes connect a input 창을 끈다. b노드를 우리는 1열로 내리고 a 노드에 추가되는 것들을 넣어주는게 좋다.
tab키를 눌러 자주쓰는 것들을 등록해놓고 쓸 수 있다. favorite창.  
localizationl storage를 우리가 쓸 수 있는 여유 공간만큼 설정을 해놓으면 되고
우리가 파일을 들고 왔을때 localization policy를 on 시키면 외장하드에서 쓰던 파일을 네트워크로 불러오는게 아니라 로컬로 불러오기때문에 작업시 불러오는 속도가 빨라진다.


# grade node
***
* blackpoint  
가장 어두운 암부를 스포이드로 찍어준다.

* whitepoint  가장 밝은 부분을 스포이드로 찍어준다.  

화이트밸런스를 자동으로 맞춰준다.

* lift (어두운 암부를 조절하는 기능 [밝은 곳 고정])

* gain (밝은 부분의 밝기를 조절하는 기능 [암부 고정])  

* multiply(gain으로 비슷한데 gain으로 컨트롤이 힘들 경우 multiply 이용해 값 조절을 해줄 수 있다)  

* offset(통채로 이동 [전체적으로 명도의 값을 조절]) 

* gamma (쉐도우와 중부를 담당하는 곳의 값을 조절 [블랙과 화이트는 냅두고 중부를 올림] 가능하면 건들지 말자.

* blackclamp whiteclamp는 hdr작업을 하거나 exr 작업으로 하는 경우에는 마이너스값과 플러스 값을 가져갈 수 있으나 일반적인
* 8bit 작업을 하면 뭉개지거나 날아간부분에 대한 표현이 안되기에 clamp조절을 통해서 1과0의 사이에 머물게 해주어야 한다.

배경을 a와 constant b를 합친다고 했을때 set bbox to 를 linear가 아닌 b로 놓고 하면 constant의 사이즈로 맞춰서 바운딩을 해준다.
그런데 a배경이 크롭이 된다면 reformat을 해주고 transform을 해주어서 이미지 사이즈를 맞춰줄 수 있다.
reformat을 통해 해상도를 바꾸고 resize type을 설정해주어서 가로폭을 맞출꺼다 세로폭을 맞출꺼다 결정하면된다.
일단은 가로로 놓고 작업하는게 나을듯.
그다음 transform 노드를 통하여 이미지의 위치를 조절할 수 있다.

우리가 이미지를 강제적으로 변경했을때 픽셀이 깨지게 되는데 filter가 그 부분을 어떻게 채울 것인가에 대해 값을 설정해주는데
기본은 cubic으로 되어 있는데 랑코즈는 외곽선이 칼지게 떨어지고 리프만이나 리첼은 부드럽게 떨어지고.
링크는 교수님이 올려주시면 읽어보자. 

필터를 다 같은 값으로 고정하여서 설정을 하는게 원본 훼손이 덜해진다.  
nuke node concatenation
색 보정을 할때 전반적으로 봤을 때 r g b 값의 각기 다른 값들을 모두 개별 수정하여 곱하여야한다.

rgb alpha채널 값을 통해서 두가지 이미지를 w를 눌러서 한 화면에 2개를 띄워놓고.

먼저 lift를 건들어 암부를 맞춰준다. 이때 컬러휠을켜서 각각의 채널의 암부를 맞춰준다.

포토샵에서 우리가 만든 이미지 파일을 png로 불러온다고 하였을때 alpha 채널에 대한 값이 누크에서는 따라오게 되는데
premult를 시켜주어서 rgb채널에 우리가 가져가고자 하는 이미지를 곱하여 알파값을 뽑아낸 뒤 합성할 수 있다.







# color correct
***





