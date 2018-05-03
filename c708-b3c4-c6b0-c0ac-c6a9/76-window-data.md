# 7.6. Window setResultCallback

---

> Download : [http://manual.spidergen.org/example/SG012.zip](http://manual.spidergen.org/example/SG002.zip)

1. Views 폴더에 DataWindow 뷰를 추가합니다. 다음 내용을 참고해서 컴포넌트를 배치합니다.
   * | component | id | position | size | text | etc |
     | :--- | :--- | :--- | :--- | :--- | :--- |
     | AButton |  | right:20px, top:20px | width:20px, height:20px | X | background-color : red |
     | ATextArea | txtData | left:20px, top:50px | w-stretch:20px, h-stretch:80px |  |  |
     | AButton |  | left:20px, bottom:20px | w-stretch:20px, height:50px | 내용추가 |  |
   * ![](/assets/win-ex-020.png)
2. DataWindow.cls 파일을 오픈하고 다음과 같이 멤버변수를 추가합니다.
   * > ```js
     > class DataWindow()
     > {
     >     super();
     >
     >     this.data = null;
     >
     > }
     > extends AView;
     > ```
3. "X" 버튼에 Click 이벤트를 설정하고 설정 함수를 다음과 같이 수정합니다.
   * > ```js
     > function DataWindow:onAButton1Click(comp, info, e)
     > {
     >     this.getContainer().close(1, this.data);
     > };
     > ```
4. "내용추가" 버튼에 Click 이벤트를 설정하고 설정 함수를 다음과 같이 수정합니다.

   * > ```js
     > function DataWindow:onAButton2Click(comp, info, e)
     > {
     >
     >     this.data = this.txtData.getText();
     >
     > };
     > ```

5. DataWindow.cls에 윈도우가 활성화 될때마다 전달된 데이터를 txtData에 추가 하도록 다음과 같이 onActiveDone 이벤트에 내용을 수정합니다.

   * > ```js
     > function DataWindow:onActiveDone(isFirst)
     > {
     >     super.onActiveDone(isFirst );
     >
     >     this.txtData.setText(this.data);
     >
     > };
     > ```

6. MainView의 "setResultCallback" 버튼에 Click 이벤트를 설정하고 설정 함수를 다음과 같이 수정합니다.

   * > ```js
     > //setResultCallback 버튼
     > function MainView:onAButton11Click(comp, info, e)
     > {
     >
     >     var wnd = new AWindow('callback-window');
     >     
     >     // url, parent, width, height
     >     wnd.openAsDialog('Source/Views/DataWindow.lay', this.getContainer(), 400, 400);
     >     
     >     //윈도우에 데이터를 전송(설정)
     >     wnd.setData('MainView에서 DataWindow에 텍스트를 전달합니다.');    
     >     
     >     //윈도우가 Close 될때 자동 호출되는 메소드
     >     wnd.setResultCallback(function(result, data)
     >     {
     >         AfcMessageBox('CallBack Data', data);
     >         
     >     });
     >
     > };
     > ```
   * setData\(\) 메소드를 통해서 윈도우에 데이터를 설정 할 수 있습니다.
   * 윈도우가 Close 될때 자동으로 호출되는 setResultCallback\(\) 함수를 재정의 합니다.

7. F5키로 프로젝트를 빌드하고 실행합니다.

   * "setResultCallback" 버튼을 클릭합니다.  텍스트 내용을 입력 할 수 있는 "DataWindow" 윈도우가 오픈되는걸 확인합니다.
   * 텍스트 입력창에 "내용을 추가합니다 ^^!!" 라고 추가 입력하고 "내용추가" 버튼을 클릭합니다.


   * ![](/assets/win-ex-021.png)
   * "X" 버튼을 클릭해 윈도우를 닫습니다.

   * 윈도우가 닫히고 메시지 박스에 텍스트 입력창 내용이 출력되는걸 확인합니다.
   * ![](/assets/win-ex-025.png)



