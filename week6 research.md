# nuke 경로지정
***  
**nuke 절대경로 상대경로** 

절대경로 ex: c:/ usrs/t17810-/desktop/1013/123/2d digital합성 등 우리가 기존에 쓰던 방식이 절대방식이고
**우리가 한 작업물을 공유할때에는 상대경로를 넣어주는데 상대경로는 c:/ usrs/t17810-/desktop/1013/123/2d digital합성 안에서 어디폴더에 있다고 정해주는 것.**
./이라는 표시는 같은 폴더 안에 이미지가 있다라고 알려주는 것. 
그래서 **nk파일**의 상대위치를 우리가 images 폴더 안에 greenscreenboy . tif가 있다면 ./iamges/greenscreenboy.tif를 file명 안에 넣어주면 된다.  

현재 위치= ./  

상위 폴더= ../  

또 그 위에 폴더= ../../  


**절대 경로 위의 폴더 차례대로 뒤에서부터 거슬러 올라간다는 느낌이다.
모든 소스들과 오브젝트들을 한 개의 폴더 안에 다 묶어서 볼러와주자.**  


[foundry](https://support.foundry.com/hc/ko/articles/208961109--Q100154-Nuke-%EC%97%90%EC%84%9C-%EC%B0%B8%EC%A1%B0%ED%95%98%EB%8A%94-%EC%83%81%EB%8C%80-%ED%8C%8C%EC%9D%BC-%EA%B2%BD%EB%A1%9C)

# rotoscoping  
***

**what is rotoscoping?**  


사진에 tracing 작업하여 촬영본에 덧그려서 만드는 작품.  
우리는 원하는 이미지를 원본 플레이트에서 분리하는 작업. -> **따로 분리하여 alpha 채널을 만들어 쉽게 분리하는 것이 목표** 
<img src="https://nickharkerblog.files.wordpress.com/2017/01/363938477_1280x720.jpg?w=1200" width="640" height="360" >

<img src="https://www.foundry.com/sites/default/files/styles/hero_1440_x_825_/public/paragraphs/zoomable-gallery/SmartROTO%20-%20SidebySide%202.jpg?itok=Bsz-BNST" width="640" height="360" >  


+ **직접 스코핑을 해본 결과 이미지를 분리하여서 각각 관절별로 뭉텅이뭉텅이 따주어야 프레임별 수정이 용이하다.**  
   
+ 우리가 shape을 그릴때도 물체가 어떠한 특성을 가지고 움직이는지 파악하고 들어가야한다. hard surface는 변형이 거의 없음으로 하나로 묶어서 표현해도 된다. 
전체 쉐입을 유지해주는 포인트들은 최대한 안건들이는게 낫다.

+ 쉐입이 움직일때 모양이 안맞는다면 변형과 스케일 조절을 하는게 낫긴한데 ctrl shift alt 키를 이용하여 점을 수정하고 그래도 정 안되면 조금만 움직이는게 낫다.
베지어 곡선을 수정할때 미세한 회전을 하고 싶다. 하면 shift 누르고 회전 시키면 snap 기능이 꺼진상태로 조정이 된다.  

+ roto에서 오브젝트를 묶고 싶다면 layer을 만들어 준 다음에 안에 드래그해서 다 넣어준다. 그다음 transform 안에서 모양을 조정
그다음 motion blur을 이용하여 움직임을 더 자연스럽게 만들 수 있다.  


**1. identify motion path**  
frame by frame으로 잡지말고 크게 크게 잡아야한다. 나중에 일일히 key를 다 잡아줘야하는 불상사가 생길 수 있다.

**2. sparate by objects** 
일단 오브젝트 별로 구분하는 것. 물병을 들고 있는 샷에서 물병을 지워야 한다고 해도 잡고있는 손까지도 스코핑을 해야한다.  


**3. stabilize plate**  

일반적인 상황에서는 삼각대 위에서 대부분 찍는다. 흔들리는 것을 로토 딴다고하면 tracking을 통해 움직이는 plate를 역방향으로 회전을 시키면
움직임이 멈춰보인다. 

**4. primary and sccondary forms**  

시퀀스 안에서 메인으로 움직이는 형체와 부수적인 형체를 쪼개서 작업해야한다.  
포인트들을 수정하는 것보다는 scondary thing까지 shape을 맞춰줘야한다.

**5. use rotational points**  
해부학적인 움직임을 추척할때 사용한다.  



## merge operation  

***

**이미지와 이미지를 연결했을때 결과가 나올것인지 계산해주는 공식들이다.**  

<img src="https://t1.daumcdn.net/cfile/tistory/2266BC3E5289F4E420">  




<img src="https://i0.wp.com/artofvfx.com/wp-content/uploads/2019/08/AvengersEndgame_CapvsCap_MOF_VFX.jpg?ssl=1" width="640" height="360">  

<img src="https://beforesandafters.com/wp-content/uploads/2019/05/CapvCap-e1557913128833.jpg" width="640" height="360">


merge operation 중에 over는 layer 2개를 합치는 것인데  

**a+b(1-a)**  

**A라는 레이어의 인물과 B라는 레이어의 배경을 합친다고 하였을때 A의 ALPHA채널을 ROTO작업을 통해 추출하고**   

**B라는 레이어의 배경에 A의 ALPHA값을 빼어 그 부분과 B의 배경을 PREMULT시켜 구멍을 내고 그 위에 A의 이미지를 얹어 배경을 합성한다.**  


+ 위의 크로마키에서 촬영한 캡틴아메리카 A와 빌딩 배경인 B를 준비한다.  

+ 크로마키에서 촬영된 캡틴아메리카를 CHROMA KEY 추출작업과 ROTO를 이용해 ALPHA값을 추출한다.  

+ B의 배경위에 A의 ALPHA값을 빼준뒤 PREMULT 시켜 B의 배경에 구멍을 내고 A의 이미지와 합성한다.  



## rotopaint  

**배경에서 불필요한 요소들을 제거하고 배우나 어떤 사물에 들어있는 불필요한 요소를 지울때 사용한다.** 
일반적인 photoshop의 stamp툴과 비슷하며 clean up 개념이다. 

<img src="https://fiverr-res.cloudinary.com/images/q_auto,f_auto/gigs2/100257298/original/265b1bd8c0ddf2d9e1f24c066c86ec4c294c3a83/stereoscopic-and-remove-background-rotoscoping-24-hours.jpg" width="640" height="360">

~~seems disguesting..~~  

<img src="https://www.fxguide.com/wp-content/uploads/2011/10/Click_After.Life_color_c_roto.jpg" width="640" height="360">  

이와 같이 인물 근처에 뭍은 먼지나 눈에 튀는 부분을 painting을 통해 보여주고자 하는 부분을 명확하게 보여줄때 사용한다.

## merge operation  
**from B-A**  
**mask BA**  
**minus A-B**  
**multiply AB, A IF A<0 and B<0**  
**over a+b(1-a)**  
**plus A+B**  
**stencil B(1-a)**  
**under A(1-b)+B**  
