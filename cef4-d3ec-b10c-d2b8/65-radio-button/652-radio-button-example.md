# 6.5.2. Radio Button Example

---

> Download : [http://manual.spidergen.org/example/SG002.zip](http://manual.spidergen.org/example/SG002.zip)
>
> youtube : https://www.youtube.com

1. 새 프로젝트를 생성합니다. 이전의 6.4. CheckBox 의 1~3번 내용을 참고하세요.
   * 프로젝트명을 **SG002**로 생성합니다.
2. ID : V001인 화면 View를 추가 합니다.
   * Source &gt; Views 폴더를 생성합니다.
   * Views 폴더에 V001 뷰를 추가합니다.
3. SG002App.cls 파일을 다음과 같이 수정합니다.
   * > ```js
     > function SG002App:onReady()
     > {
     >     super.onReady();
     >
     >     var navigator = new ANavigator();
     >     navigator.registerPage('Source/Views/V001.lay', 'V001');
     >     navigator.goPage('V001');   
     >
     > };
     > ```
4. V001.lay 파일을 오픈하고 아래 정보를 참고해서 레이아웃을 작업합니다.
   * | component | ID | Group | Position | Size | Text | value |
     | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
     | ARadioGroup | rdoGroup01 |  | left:20px, top:80px | width:360px, height:80px |  |  |
     | ARadioButton |  | Rdos | left:20px, top:30px | width:80px, height:20px | 사과 | 100 |
     | ARadioButton |  | Rdos | left:120px, top:30px | width:80px, height:20px | 포도 | 200 |
     | ARadioButton |  | Rdos | left:220px, top:30px | width:80px, height:20px | 오렌지 | 300 |
     | ALabel | lbl001 |  | left:20px, top:20px | width:auto, height:auto | 선택내용 |  |
   * ![](/assets/rdo-ex-002.png)
   * 위 그림에서 보듯이  라디오버튼을 라디오그룹 내에 배치합니다. 라디오그룹 컴포넌트는 그룹내에서 1개의 라디오버튼만 선택될 수 있게하는 매니저 기능을 합니다.
5. 라디오 버튼에 클릭 이벤트를 설정합니다.
   * 3개의 라디오 버튼의 클릭 이벤트에 동일한 이벤트 함수를 매핑 합니다. 함수명을 onARadioButtonsClick 로 합니다.
   * 다수의 컴포넌트에 동일한 이벤트 함수를 매핑 할 경우 함수의 파라미터로 이벤트 발생 객체를 구분 할 수 있습니다.
   * 이벤트 함수는 내용은 다음과 같이 작성합니다.
   * > ```js
     > function V001:onARadioButtonsClick(comp, info, e)
     > {
     >     /**
     >         comp : 클릭 이벤트가 발생한 객체
     >         info : 컴포넌트 마다 다른 정보가 전달됨. 컴포넌트 api 참조
     >         e : 오리지널 이벤트 객체
     >     */
     >     
     >     //선택되었을 경우
     >     if(comp.getSelect())
     >     {
     >         this.lbl001.setText(comp.getText() + ':' + comp.getValue());    
     >     }    
     >
     > };
     > ```
6. 프로젝트를 빌드 후 실행합니다. 
   ![](/assets/rdo-ex-004)



