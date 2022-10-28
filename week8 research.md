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




