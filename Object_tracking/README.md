# 목표
환경 : 윈도우, 로지텍 카메라
1. 객체 크기 인식하기 (나)
2. 일정 거리 기준 멀어지면 멀어졌다고 문자열 출력 
>
# 과정
>
거리 정보를 추정시 활용할 수 있는 정보들
1) 물체의 크기가 멀어질수록 작아진다.  
2) 물체의 색상이 멀어질수록 흐려진다. or 진해진다.  

# 문제점
카메라와 가까우면 초록색으로 보이고  
멀어지면 빛 때문에 검은색으로 보인다.   
=> 색상에 따른 차이를 활용하여 거리 정보를 추정할 수 있음.  
이미지에서 색상 정보를 추출하는 처리 필요  

HSV 이용  
색상(Hue), 채도(Saturation), 명도(Value)  
명도 : 빛의 세기  

원래) 물체와 카메라 사이의 거리가 멀어질수록 명도 값 작아짐 (낮으면 어둡다.)  
>
1. 명도 값이 일정 이하면 물체와의 거리가 멀어졌다고 가정 가능.  
코드 구성도  
명도 값만 추출하여 평균 값을 계산한다.  
명도 임계값보다 작으면 거리 정보를 출력함.  
ex) 명도 값 255이면 0cm  
  명도 값 0일 때 거리 무한대  

논리는 맞음..  

★ roi 안에 있는 객체의 크기가 작아지면 = 거리 멀어짐
1. 처음 인식된 객체의 크기(네모)를 기준으로 작아지면 거리 멀어졌다고 판단.
-> 테스트 해보며 객체의 크기, 객체의 거리 다 체크 -> 코드 노가다
2. 처음 인식된 객체의 명도 값 평균을 측정, 평균값보다 낮아지면 거리 멀어짐. 평균값보다 높으면 거리 가까워짐

