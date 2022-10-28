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

* whitepoint  
가장 밝은 부분을 스포이드로 찍어준다.

화이트밸런스를 자동으로 맞춰준다.

* lift (어두운 암부를 조절하는 기능 [밝은 곳 고정])

* gain (밝은 부분의 밝기를 조절하는 기능 [암부 고정])  

* multiply(gain으로 비슷한데 gain으로 컨트롤이 힘들 경우 multiply 이용해 값 조절을 해줄 수 있다)  

* offset(통채로 이동 [전체적으로 명도의 값을 조절]) 

* gamma (쉐도우와 중부를 담당하는 곳의 값을 조절 [블랙과 화이트는 냅두고 중부를 올림] 가능하면 건들지 말자.)










# color correct
***





