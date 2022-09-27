# WHAT IS ACES?
<img src="https://uploads-ssl.webflow.com/5e9033e54576bc13f0b47167/5f59441c4d7b0b7f18fc840e_mIiPyl.png" width="500" height="500" >  

<https://garagefarm.net/ko-blog/what-is-color-space-and-why-you-should-use-aces>  

**ACES는 무엇일까**  
>The Academy Color Encoding System (ACES) is __a free, open, device-independent color management and image interchange system__ developed under the patronage of the Academy of Motion Picture Arts and Sciences.
> It’s meant to __standardize color space__ between different input sources (cameras, VFX, etc). It features a **high dynamic range, an RGB-based workflow, and an ultra-wide color gamut** that encompasses the entire spectral locus.
> For digital artists, the biggest reason to use ACES is that renders look and feel more “photorealistic”. **That’s because of the wider dynamic range.**

>> 즉 색상 관리 및 이미지 교환 시스템이며 서로 다른 소스들의 색 공간을 표준화 하기 위해 제작 되었다. 
앞에서 말하였던 gamut의 범위 중 **가장 넓은 다이나믹 레인지**를 포함하고 있으며  crt모니터의 srgb부터 rec 709, aces 2065-1 , ntsc의 **모든 색 정보**를 포함하고 있다.
우리는 이 기준 색 공간을 **ACES2065-1 (A.K.A) AP0**로 부르기로 했다. 

***  
## ACES WORK FLOW~  
<img src="https://chrisbrejon.com/wp-content/uploads/2020/09/015_ACES_0030_ACES_autodesk_FHD.jpg" >   

**A단계**에서 우리는 다양한 기기로 촬영한 원본 소스들을 불러온다. 이때 **입력장치변환** 즉 **IDT** 과정을 통해 이미지들을 ACES 색상 공간으로 가져오고 변환시킨다.  

**B단계**에서 우리는 **ACESCG(AP1)** 작업을 하며 원본 소스들은 **ACES2065-1**로 저장되어 아카이브된다.  

**c단계**에서 우리는 **RRT**와**ODT** 즉 랜더레퍼런스변환 작업과 출력장치변환 작업을 통하여 각 재생 디바이스에 맞춰 색을 최종 출력한다.  

## 우리는 왜 ACES 2065-1 과 ACESCG를 사용할까?  

ㄴ> **먼저 이들을 왜 사용하는지 아려면 선형 편집 linear workflow부터 이해해야한다.**

**GAMMA**란 무엇인가?

>감마는 디지털 디스플레이에서 검정색이 흰색으로 얼마나 부드럽게 전환되는지로 설명할 수 있습니다. 종종 2.2 또는 2.4와 같은 숫자와 연결됩니다. 이 숫자는 검은색에서 흰색으로 또는 흰색에서 검은색으로 곡선의 범위를 나타냅니다.  

>> **감마란 컴퓨터 모니터에서 보여지는 색의 스펙트럼의 밝기 곡선이다.**  
>>  **그렇다면 linear workflow는 무엇인가?**  
<img src="https://image.benq.com/is/image/benqco/gamma-1?$ResponsivePreset$" width="600" height="400">  

(https://www.benq.com/en-us/knowledge-center/knowledge/gamma-monitor.html)

<img src="https://user-images.githubusercontent.com/60923302/118788622-ecc46600-b8ce-11eb-843c-c985eb6be98e.png" width="600" height="500">  

위의 그림을 보자면 먼저 인간의 눈은 [베버의 법칙](http://www.ktword.co.kr/test/view/view.php?m_temp1=4166)






