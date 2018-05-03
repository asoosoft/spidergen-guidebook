# 6.18.2. Slider Example

---

> Download : [http://manual.spidergen.org/example/SG008.zip](http://manual.spidergen.org/example/SG008.zip)

1. 새 프로젝트를 SG008을 생성합니다.
2. Source 폴더 내 MainView를 생성합니다.
3. SG008App.cls 파일을 오픈하고 내용을 다음과 같이 수정합니다. 네비게이터를 생성하고 MainView를 추가합니다.
   * > ```js
     > function SG008App:onReady()
     > {
     >     super.onReady();
     >
     >     var navigator = new ANavigator();
     >     navigator.registerPage('Source/MainView.lay', 'MainView');
     >     navigator.goPage('MainView');
     >
     > };
     > ```
4. MainView.lay 파일을 오픈하고 다음 내용을 참고해서 컴포넌트를 배치합니다.

| component | id | position | size | text | etc | value |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| AProgress | prog | left:50px, top:50px | width:200px, height:20px |  | background-color:\#acacac |  |
| ASlider | slider | left:50px, top:100px | width:200px, height:20px |  |  | value:25, min:0, max:100, step:5 |
| ALabel | lbl001 | left:60px, top:30px | width:auto, height:auto | 현재값 | - | - |

![](/assets/slider-ex-002.png)

1. 슬라이더에 설정된 값을 표현하기 위한 사용자 함수 doSetValue\(val\)를 다음과 같이 추가합니다.

   * > ```js
     > function MainView:doSetValue(val)
     > {        
     >     this.lbl001.setText(val);
     >     this.prog.setValue(val);
     > };
     > ```

2. 슬라이더에 Change 이벤트를 설정합니다. 설정 함수는 내용은 다음과 같이 수정합니다.

   * > ```js
     > function MainView:onSliderChange(comp, info, e)
     > {
     >     //사용자 함수 호출
     >     this.doSetValue(comp.getValue());    
     >
     > };
     > ```

3. 마지막으로 메인뷰 onInitDone\(\) 에 슬라이더 컴포넌트의 기본값을 설정합니다.

   * > ```js
     > function MainView:onInitDone()
     > {
     >
     >     this.doSetValue(this.slider.getValue());
     >
     > };
     > ```

4. F5 키로 프로젝트를 빌드하고 실행합니다.

   * 슬라이더에 바를 움직여 값을 조정해 봅니다. 조정된 값에 따라 프로그래스바가 변경된는걸 확인합니다.  
   * ![](/assets/slider-ex-007.png)



