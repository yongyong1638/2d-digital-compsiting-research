
# **What is the color?**  
* 색이란 반사되거나 방출되는 빛의 다른 품질로 인해 발생하는 사물의 측면이다.  
  * **색**을 보려면 **빛**이 필요하다.  
  * **빛**이 물체에 비치면 일부 색상은 물체에서 반사되고 다른 색상은 흡수된다. 우리는 반사된 그 색상을 보고 **색**이라 인지를 한다.  
  * **빛**은 다양한 파장의 전자기파의 모임이다.  인간의 눈은 그 전자기파들의 집합들 속에서 대략 **390**~**700 nm** 을 볼 수 있고 이를 **가시광선**이라고 한다.  

  <https://byjus.com/physics/visible-light/>
![빛의 스펙트럼](https://cdn1.byjus.com/wp-content/uploads/2018/11/visible-light-1.jpg)   
***
## **The three color of light?**  

*  **R. G. B** -> (**A.K.A**) **가산혼합**
* **그렇다면 왜 많고 많은 색들중 rgb인가?** 인간의 시각 세포에는 **명암과 물체의 형태를 인식하는 간상세포**와 **빨간색, 초록색, 파란색의 세 가지 세포로 인지하는 원추세포**가 있다.  
* **디지털 작업 및 모니터상**의 색 표현을 할때 쓰이는게 R G B 혼합법이다. **빛**의 혼합이며 합치면 합칠수록 색이 밝아지고 감도 조절을 통해 원하는 색을 만들어낸다.  

![rgb](https://blog.kakaocdn.net/dn/bTmR0u/btq9nhL30IO/lxffbH4GfFm2IhOzsf5kd0/img.jpg)  

<https://blog.kakaocdn.net/dn/bTmR0u/btq9nhL30IO/lxffbH4GfFm2IhOzsf5kd0/img.jpg>

*  **C. M. Y. K** -> (**A.K.A**) **감산혼합**
 * 디지털 작업을 하여 최종 **인쇄물**을 뽑을때 사용하는 혼합법이며 **잉크**로 이루어져 색을 섞으면 섞을수록 색이 어두워지며 잉크의 양을 조절해 색을 만들어낸다.

<img src="https://m.wowpress.co.kr/wow2.0/w_guide/assets/img/g2_2_02.jpg" width="300" height="300"/>  

<https://m.wowpress.co.kr/wow2.0/w_guide/assets/img/g2_2_02.jpg>

***

## **what is the alpha?**
~~내가 아는 alpha는 league of legend의 skill밖에 없다.~~ 

![masteryi](https://cdn.lolalytics.com/generated/champion280px/masteryi.jpg)

**그렇다면 알파의 정의는 무엇일까?**

> A in RGBA stands for the alpha channel, which is an additional channel that stores the information about the opacity/transparency of every pixel. The term was first proposed by Thomas Porter and Tom Duff way back in 1984.  
>> 불투명성 즉 opacity가 알파의 개념이다.
>>> A in RGBA stands for the alpha channel, which is an additional channel that stores the information about the opacity/transparency of every pixel. The term was first proposed by Thomas Porter and Tom Duff way back in 1984.
>>>> __RGB는 Red, Green, Blue의 약자이며 RGB를 사용하면 빨강, 녹색 및 파랑의 다른 양을 혼합하여 다양한 색상을 얻을 수 있는 가산 색상 모델이다.__ RGB 모델의 값 범위는 0에서 255 사이이며, 여기서 0은 믹스에서 색상 채널을 나타내지 않음을 나타내고 255는 색상 채널의 최대를 의미한다. 컴퓨터가 3가지의 색 채널 r g b를 지니고 있다면 **alpha** 역시 채널로써의 역할을 하며 bit의 심도 (8,10,12 ...) 에 따라 rgba의 표현 범위가 넓어진다.  
>> 
  *  **(255,0,0) -> 빨간색** 
  *  **(0,255,0) -> 녹색**
  *  **(0,0,255) -> 파란색**
  *  **(0,0,0) -> 검은색**
  *  **(255,255,255) -> 흰색**  
    
  -> Alpha channel의 관점에서 보았을 때에는 0에 해당하는 부분은 아무것도 없는 즉 opacity 0 불투명도0에 해당하고  
  1에 해당하는 부분은 불투명성 1 즉 전체 적용 범위를 나타낸다.
  
 <https://www.actionvfx.com/blog/what-is-an-alpha-channel>  
 
 <img src="https://w7.pngwing.com/pngs/800/635/png-transparent-rgba-color-space-alpha-channel-sql-logo-angle-text-logo.png" width="300" height="300"/>
 
 ***
 ## **what is the color space?**
 * **우리가 이 범위를 이해하기 위해서는 차원을 알아야한다.**  
 <img src= "https://www.scratchapixel.com/images/upload/color/xyzgraph.png" />  
 
우리가 볼 수 있는 스펙트럼의 범위인 380~ 700nm의 영역을 따라 점을 찍어 평면 좌표로 나타내면 위의 그림처럼 표현 할 수 있다.  

<img src= "https://www.lamptolaser.com/images/spectrum.jpg" />

**색도라고 불러왔던 색상의 강도를 gamut라고 하며 색상이 재현하는 범위 한계를 설정한다.** 

이렇게 **색도를 표현하기 위한 x, y값**, 그리고 **밝기를 표현하기 위한 Y값**을 사용하여 CIEXYZ 표색계를 3차원 공간 개념으로 표현한 것을 **CIExyY Color Space**이라고 한다.

그리고 CIExyY에서 색도를 나타내는 x, y값을 **직교좌표계**로 나타낸 것을 **색공간 색도도(CIE 1931 Color Space Chromaticity Diagram)** 이라 한다. **이런 색도도(chromaticity diagram)는 결국 3차원 색 공간을 색도를 기준으로 2차원으로 표현한 도표이다.** 

<img src= "https://www.scratchapixel.com/images/upload/color/rgbcube.png" />  

3d 큐브의 차원에서 보면 각 R. G . B의 꼭지점을 연결 시키면 보조 색인 C M Y 가 생성이 되는데 세가지의 색상을 다 합치면 (0, 0, 0) 은 BLACK (1,1,1) 은 WHITE로 표현가능.

<https://www.scratchapixel.com/lessons/digital-imaging/colors/color-space>  

**그렇다면 우리는 왜 이 color space 를 신경써야할까?**  

<img src= "https://blog.frame.io/wp-content/uploads/2020/02/Sample-Color-Managed-Grading-Workflow-800x709.jpg" /> 

**과거에는 35mm , 70mm 필름 카메라로 영상을 만들었다면 디지털의 발전으로 다양한 회사의 카메라가 발전하였고 각 회사의 기기들이 가지고 있는 고유의 색 표현 방식이 다르고 뿐만 아니라 다양한 장비들이 발달하였다.**  **-> IDT**  

**요즘에는 스크린뿐만 아니라 디스플레이들의 다양화 (ex, 스크린, 스마트폰 , 외부 디스플레이 etc..)로 인해 각 영상들의 최종물을 재생 시 정확한 색을 관객에게 전달하려면 색 보정 단계에서 gamut의 범위를 통합하는 것이 필요.** **->ODT**  
--> **ACES의 발달**  
*이 다음부터는 2주차로..*




