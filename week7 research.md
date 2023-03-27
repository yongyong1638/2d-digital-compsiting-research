# IM A LANTERN BOY~

shift x 누르면 노드 채널의 A B가 바뀐다. RGBA의 하나의 데이터 속에서 픽셀은 겹치는게 안되기 때문에
합쳐질때 ALPHA랑 RGB채널을 곱해서 PREMULT 해준 뒤 MERGE 해야한다.  

뒤에 있는 알파를 1로 보고 A에 있는 ALPHA를 빼주고 뒤에 있는 알파와 곱한다.  

B 배경이 있다면 B배경에 A의 알파값을 구멍내고 거기 위에 A의 알파값을 올려준다.  

머리카락 부분은 좀 작게 범위를 설정하고 FEATHER값을 주는게 따기 더 편하다. 단축키 E  

LIGHT Wrap? 을 찾아보면 우리가 누끼를 딸때 조금 더 작게 따고나서 밀어주어서.. 테두리에 검은 선이 지는 것을 방지할 수 있다.

키보드에서 m키를 누르면 roto딴것의 mask범위를 볼 수 있다. 빨간색으로 볼 수 있다.  

motion blur.
정면 샷과 좌 우측 나눠서 쉐입을 잡아주는게 수정에 용이하다.  
png 파일은 alpha 채널 값을 가지고 있기에 로토 스코핑해도 하얗게 나올 것이다. 그럴때 우리는 shuffle 노드를 사용할 수 있는데.  
roto scoping을 한 부분중 alpha값을 빼고 rgb값만 연결해주면 로토스코핑한 부분의 알파값만 보여질 것이다.

뷰어에 바로 연결하는 1 2 3 4 5 단축키를 활용해서 노드에 꼽을 수 있다. 

**chroma key**

로토보다는 편하다고 느끼겠지만 크로마도 결국 alpha를 추출하는 과정이다.  
촬영되는 영상에 전기적으로 alpha값을 추출해서 matte값과 합쳐져서 실시간 방송.  

동양인의 눈은 갈색과 흑색의 사이이기에 일반적으로 파란배경, 서양인은 푸른 눈이 많기에 초록배경을 사용.

카메라 센서는 그린 키를 더 잘 잡아내기에 크로마키는 일반적으로 그린을 많이 사용.  

georges melies 합성이 없는 영화를 찍다가 이 양반의 노력을 통해서 필름에 이상한 짓을 하여 여러번 촬영해서 
하는 등 매트 페인팅을 했다.

DUNNING PROCESS

BLUE Background and YEllow matte. 흑백 영화에서만 사용가능 했다.

green screen의 발명  
전자적 신호에서 더 밝게 표현  

야외에서 잘 적용이되고  

더 적은 빛을 필요로하고  

의상에서 더 적게 쓰이는 색상이여서 편집에 사용.

카메라 ccd에서 보면 r1 g2 b1인데 g2기 때문에 그린키를 더 잘 잡음.

촬영 시에는 반드시 배우의 배경과 그린 스크린을 채워줄 크로마키가 더 있어야한다. 배경에도 충분한 광량이 있어야 뽑기 수월.  

Anti-Aliasing 과정을 통해서 매끄럽게 만든다.  

**keyer**  
keylight과 ibk gizmo 노드 주로 사용

soft key, hard key+ keymix  

hard key에서 key light과 filtererode를 통하여 딱딱한 인물의 누끼를 따준다.

soft key에서 keymix와 roto를 이용해 주변 배경을 정리하고

channelmerge를 통하여 인물의 누끼와 검은배경을 합친다.



diffrenece key
같은 배경에서 인물만 빼고 싶을때 사용?

*keylight*  
우리가 촬영을 잘해온다면 잘 빠진다.  
soft key는 외곽부분의 soft하게 잡을 수 있는 것, hard key는 내부를 채우는 것 (변함x) + keymix를 사용하여 연결을 해준다.  
키라이트에서 우리는 초록색 배경을 빼기전에 뒤에 배경의 노이즈를 잡아주어야한다. 
ctrl key 누르고 노드를 연결해주면 원이 생기는데 이걸로 노드르 ㄹ정리해야한다.
denoise를 통해서 초록 배경을 다 비슷해보이게 만들어주고 그 다음에 키 라이트를 뽑아준다.
screen colour에서 스포이드로 인물과 가장 가까운 배경을 찝어주고
screen matte값에서 clip black과 clip white를 통해서 주변부를 잘 잡아주면 된다.

그렇지만 한번에 빠지는 키는 없기에 우리는 여러개의 작업을 통해 배경과 인물을 분리한다.



**despill**
일반적으로 green or blue배경에서
키를 빼어 주변부를 회색으로 만들어준다, 그러나 간혹 주변부의 색감을 통해 임의로 바꾸긴한다.

위에서 인물을 배경과 분리했다면 despill을 해주어야하는데 gizmo node를 통해서 인물에 묻은 그린을 gray로 바꿔주는데. 
나중에는 초록 배경억제로 인한 인물에 손상이 있다면 color correction을 해주어야 한다.

**grade color correct의 차이**  

g는 전체적인 톤 조절 color correct는 이미지를 합성 시 b 배경에 어울리는 채도 명암을 잡아줄 때 사용.
gamma는 어두운 것을 어둡게  
gain은 밝은 것을 더 밝게  
black과 white point를 다 찍어주자.  

**color correct**

* 컬러 코렉션 시 range에서 shadow midtone highlight의 범위를 바꿔줄 수 있음.  
* shadow의 range를 바꾸면 어둠이 어디까지 영향을 미추는지 조절 가능함.  
* 미드톤은 쉐도우와 하이라이트를 바꿔주면 자동으로 값이 바뀐다.
암부의 어두운 영역은 gamma값을 조절 하이라이트의 밝은 부분은 gain값 조절.


