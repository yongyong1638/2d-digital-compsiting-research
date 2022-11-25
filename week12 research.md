# 3d object compositing
3d 오브젝트들에 여러 map들이 있는데 aov를 활용하면 좋다.
id 맵과 normal을 활용하면 랜더하고 후에 합성할때 용이하다.
3d object의 합성 전 jpg-> unpremult-> (color grade color correct등 색에 대한 보정을 하고)-> premult 해주어야 오브젝트의 배경에 자연스럽게 붙는다.
unpremult는 이미지의 외곽을 조금 더 늘려 랜더링 해주는 것이다.
그러면 이미지 외곽에 검은색 윤곽이 생기는데 이를 color grading을 통하여 값을 맞춰준 뒤 premult해서 끊어내야 깨끗하게 오브젝트가 배경과 붙는다.
