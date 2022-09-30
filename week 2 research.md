# WHAT IS ACES?
<img src="https://uploads-ssl.webflow.com/5e9033e54576bc13f0b47167/5f59441c4d7b0b7f18fc840e_mIiPyl.png" width="500" height="500" >  

<https://garagefarm.net/ko-blog/what-is-color-space-and-why-you-should-use-aces>  

**ACES는 무엇일까**  
>The Academy Color Encoding System (ACES) is __a free, open, device-independent color management and image interchange system__ developed under the patronage of the Academy of Motion Picture Arts and Sciences.
> It’s meant to __standardize color space__ between different input sources (cameras, VFX, etc). It features a **high dynamic range, an RGB-based workflow, and an ultra-wide color gamut** that encompasses the entire spectral locus.
> For digital artists, the biggest reason to use ACES is that renders look and feel more “photorealistic”. **That’s because of the wider dynamic range.**

>> 즉 색상 관리 및 이미지 교환 시스템이며 서로 다른 소스들의 색 공간을 표준화 하기 위해 제작 되었다. 
앞에서 말하였던 gamut의 범위 중 **가장 넓은 다이나믹 레인지**를 포함하고 있으며  crt모니터의 srgb부터 rec 709, aces 2065-1 , ntsc의 **모든 색 정보**를 포함하고 있다.
우리는 이 기준 색 공간을 **ACES**로 부르기로 했다. 

***  
## ACES WORK FLOW~  
<img src="https://chrisbrejon.com/wp-content/uploads/2020/09/015_ACES_0030_ACES_autodesk_FHD.jpg" >   

**A단계**에서 우리는 다양한 기기로 촬영한 원본 소스들을 불러온다. 이때 **입력장치변환** 즉 **IDT** 과정을 통해 이미지들을 ACES 색상 공간으로 가져오고 변환시킨다.  

**B단계**에서 우리는 **ACESCG(AP1)** 작업을 하며 원본 소스들은 **ACES2065-1(AP0)**로 저장되어 아카이브된다.  

**c단계**에서 우리는 **RRT**와**ODT** 즉 랜더레퍼런스변환 작업과 출력장치변환 작업을 통하여 각 재생 display의 색 정보에 맞춰 색을 최종 출력한다.  

## 우리는 왜 ACES 2065-1 과 ACESCG를 사용할까?  

ㄴ> **먼저 이들을 왜 사용하는지 아려면 선형 편집 linear workflow부터 이해해야한다.**

**GAMMA**란 무엇인가?  

<img src="https://image.benq.com/is/image/benqco/gamma-1?$ResponsivePreset$" width="600" height="400">  

>감마는 디지털 디스플레이에서 검정색이 흰색으로 얼마나 부드럽게 전환되는지로 설명할 수 있습니다. 종종 2.2 또는 2.4와 같은 숫자와 연결됩니다. 이 숫자는 검은색에서 흰색으로 또는 흰색에서 검은색으로 곡선의 범위를 나타냅니다.  

 **감마란 컴퓨터 모니터에서 보여지는 색의 스펙트럼의 밝기 곡선이다.**  

**왜 gamma 2.2가 표준인가?**   

<img src="https://image.benq.com/is/image/benqco/gamma-3?$ResponsivePreset$">   

우리는 아래에서 나올 베버의 법칙에 의하면 0.0에서 0.1로 변하는 visual encoding과 linear encoding이 있는데 visual encoding에서의 변화가 더 드라마틱하게 느껴진다.  

>This phenomenon was also found in Ebner and Fairchild’s study in 1998, where they found using an exponent of 0.43 to convert linear intensity into lightness for neutrals can provide an optimal perceptual encoding of grays. The exponent of 0.43 is approximately 2.33, quite close to gamma 2.2. Hence, gamma value of 2.2 has become the golden standard of digital display for a proper calibration.  

-> 즉 0.43의 지수를 사용하여 linear intensity를 중성선의 밝기로 변환하면 최적의 회색 지각 범위를 제공할 수 있다. 0.43의 지수는 약 2.33으로 gamma 2.2와 가깝다. 따라서 gamma2.2 적절한 보정을 위한 디지털 디스플레이의 표준이 되었다.




>>  **그렇다면 linear workflow는 무엇인가?**  


(https://www.benq.com/en-us/knowledge-center/knowledge/gamma-monitor.html)

<img src="https://user-images.githubusercontent.com/60923302/118788622-ecc46600-b8ce-11eb-843c-c985eb6be98e.png" width="600" height="500">  

위의 그림을 보자면 먼저 인간의 눈은 [베버의 법칙](http://www.ktword.co.kr/test/view/view.php?m_temp1=4166) 때문에 어두운 색에 훨씬 민감하다. 이로 인해 어두운 환경에서 조금의 빛만 있더라도 감지 할 수 있으나 밝은 환경에서 조금의 빛은 감지할 수 없다. 우리는 gamma color space의 gradation이 더 자연스럽다고 느껴지지만 실제로 수학적으로 정의한 정확한 값은 linear color space이다. 
1. **즉, 선형 색 공간의 그라데이션을 감마 색 공간의 그라데이션처럼 우리가 자연스럽게 인지하려면 감마값을 조정을 해야한다.**  
  
1) 원래 색 그 자체는 linear로 표현 되어야 맞지만 예전 crt monitor에서는 gamma값을 낮추어 표현했었다. (SRGB)  

2) 그렇기에 디스플레이에서 보여줄 때 linear처럼 보여주기 위해 컴퓨터가 일부러 밝게 이미지를 저장하였고 모니터가 gamma값을 낮추어 표현하게 된다면 우리가 보게되는 색상이 linear로 보였다.  

3) 컴퓨터가 이미지를 저장할때 (jpg. png, gif, jpeg ..etc)포맷들은 감마보정으로 밝게 저장되지만(임의의 압축 및 변형) (raw, exr)같은 파일들은 감마보정이 없다.  

4) 그래서 exr이나 raw파일로 color grading을 해야 조금 더 자연스럽고 다양한 범위의 color manage가 가능하다.  

<img src="https://docs.unity3d.com/uploads/Main/LinearRendering-Infinite3DHeadScan.jpg" width="600" height="400"> 

위의 그림처럼 이미 감마 보정이 되어있는 이미지의 STOP(조명강도)을 차례대로 높히면 밝게 저장되어 있는 부분이 기하급수적으로 밝아져 표현가능한 WHITE가 뭉개져버린다. 이는 이미지의 손실을 야기하고 좋은 결과물을 낼 수 없다. 선형 랜더링의 경우 STOP이 높아져도 선형으로 유지된다. 이는 더 사실적인 음영 표현을 통해서 더 좋은 색 보정이 가능하다. 이렇기 때문에 **우리는 컬러그레이딩시 LINEAR WORKFLOW를 사용한다**  

(https://docs.unity3d.com/Manual/LinearRendering-LinearOrGammaWorkflow.html)  

***
## What is lut?  

> **A LUT, or Lookup Table, is an image file containing a mapping between colors in one color space to those in another.**  
   
 lut은 컬러 맵핑 이미지 파일이다.  
 영상 언어로 말하자면 텔레비전 카메라 또는 컴퓨터 그래픽 시스템의 비디오 디스플레이 설정을 말한다. 
 
 <img src= "https://s.studiobinder.com/wp-content/uploads/2019/02/What-is-LUT-LUT-Color-Grading-Ridley-Scott-Film-LUTs-Pack.jpg">

(https://filmlifestyle.com/what-is-a-lut/)

**lut color grading 1d, 3d**  
2d color grading은 평면 x,y로 이루어져 있고 3d는 color grading은 x,y,z로 깊이감이 있다. 
1D LUT은 입력값 X와 출력값 Y가 1:1로 매칭이 된다. 즉 10BIT의 뎁스는 2^10 1024개의 테이블 값을 가지게 된다.

> 1D LUTs rely on modifying levels, curves, tone mapping, and other basic adjustments in order to create an effect. These effects usually consist of saturation or hue changes as well as contrast changes in order to make colors pop out more prominently or appear differently than they would naturally on camera. 

1d LUT은 레벨, 곡선, 톤 매핑 및 기타 기본 조정 수정에 의존 -> 1d lut은 커브곡선이나 커브를 움직이는 보정값인 lift gamma gain contrast들과 1:1로 매치가 된다. 
그러나 hue나 saturation을 보정해보면 1d lut에서는 아무런 변화가 없다. 그래서 휘도곡선(gamma)을 보정할때 사용.

3d lut은 1d lut에서 표현하지 못하는 hue 와 saturation 값까지 담을 수 있다. 그 이유는 아래 그래프 처럼 z축의 공간 좌표가 생기기 때문이다.
1d lut과 달리 3d lut은 1:1 매치를 해버리면 많은 좌표값들이 필요하기에 일부 값만 표시하고 나머지는 컴퓨터가 보간해서 사잇 값을 구한다.
그렇기에 예를 10bit 값을 17 x 17 x 17로 표현

 <img src= "https://mixinglight.com/wp-content/uploads/2014/08/1D-vs-3D-Luts-The-Colorists%E2%80%99-Perspective-ML0210.jpg" >
(https://www.youtube.com/watch?v=xxlBTiNvYzE&t=315s)  


## Scene referred  
***  

DIgital 카메라와 Display들의 발달로 인해 다양한 포멧의 영상들을 편집하여 플레이 기기에 맞게끔 영상을 내보냈어야 했고 srgb color space 부터 rec2020까지 다양한 컬러 스페이스의 통합이 필요했음.
그래서 우리는 **unified color space wide hamut high dynamic range**를 만들었고 aka 통합 색공간은 동일한 범위, 화이트 포인트, 같은 전달 함수를 사용.
vfx 부서에서 acescg로 compositing을 하여 di 부서로 넘김 (디지털중간작업) di 부서에서는 최종적인 색보정을 표현 의도에 맞춰 작업하고 각종 디스플레이 장치에 맞춰 디스플레이 변환을 한다.    
원본 소스들은 aces 2065-1로 변환하여 아카이브한다.  

 <img src= "https://www.filmriot.com/wp-content/uploads/2020/12/Display-Referred-Workflow-Diagram.jpeg" width="600" height="600" >  
 <img src= "https://www.filmriot.com/wp-content/uploads/2020/12/Scene-Referred-Workflow-Diagram.webp" width="600" height="600" align="right" >  

















