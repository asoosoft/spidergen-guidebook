# 7.5. Window Show and Hide

---

> Download : [http://manual.spidergen.org/example/SG012.zip](http://manual.spidergen.org/example/SG002.zip)

스파이더젠에서 기본적으로 윈도우 Open은 호출 될때마다 새로운 객체의 윈도우를 생성합니다. 따라서 윈도우 객체를 Remove하지 않고 데이터 유지 및 재활용이 필요 할 경우 사용할 수 있는 메소드 입니다.

1. Views 폴더에 ShowHideWinView 뷰를 추가합니다.

2. 뷰의 배경색을 파란색으로 설정합니다.

3. 다음 내용을 참고해서 컴포넌트를 배치합니다.

   * | component | position | size | text |
     | :--- | :--- | :--- | :--- |
     | AButton | left:10px, top:10px | width:50px, height:50px | Hide |
     | AButton | right:10px, top:10px | width:50px, height:50px | Close |
   * ![](/assets/win-ex-015.png)

4. Hide 버튼에 Click 이벤트를 설정합니다. 설정 함수 내용은 다음과 같이 수정합니다.

   * > ```js
     > //Hide 버튼 클릭
     > function ShowHideWinView:onAButton1Click(comp, info, e)
     > {
     >
     >     this.getContainer().hide();
     >
     > };
     > ```

5. Close 버튼에 Click 이벤트를 설정하고 설정 함수 내용은 다음과 같이 수정합니다.

   * > ```js
     > //close 버튼 클릭
     > function ShowHideWinView:onAButton2Click(comp, info, e)
     > {
     >
     >     this.getContainer().close();
     >
     > };
     > ```

6. MainView에 Open 버튼에 Click 이벤트를 설정하고 설정 함수 내용을 다음과 같이 수정합니다.

   * > ```js
     > //Open 클릭
     > function MainView:onAButton7Click(comp, info, e)
     > {
     >     
     >     var wnd = AWindow.findWindow('winA');
     >     
     >     if(wnd){
     >         AToast.show('생성된 윈도우 WinA가 이미 존재합니다.');
     >         return;
     >     }
     >     
     >     var wnd = new AWindow('winA');
     >     
     >     //viewUrl, parent, width, height
     >     wnd.openCenter('Source/Views/ShowHideWinView.lay', this.getContainer(), 200, 200);
     >
     > };
     > ```

     * AWindow.findWindow\(\) 함수를 이용해서 현재 생성되어 있는 윈도우중 'winA' 윈도우가 존재하는지 확인합니다. 
     * 윈도우가 존재할경우 메시지를 출력하고 없으면 생성하는 방식입니다.

7. Hide  버튼에 Click 이벤트를 설정하고 설정 함수 내용을 다음과 같이 수정합니다.

   * > ```js
     > //Hide 클릭
     > function MainView:onAButton8Click(comp, info, e)
     > {
     >
     >     //현재 생성되어 있는 윈도우를 컨테이너 아이디로 찾습니다.
     >     var winA = AWindow.findWindow('winA');
     >     
     >     if(!winA)
     >     {
     >         AToast.show('윈도우 WinA가 존재하지 않습니다.');
     >         return;
     >     }
     >     
     >     //hide는 윈도우 객체를 보이지만 않게 한것입니다.
     >     winA.getContainer().hide();
     >
     > };
     > ```

8. Show 버튼에 Click 이벤트를 설정하고 설정 함수 내용을 다음과 같이 수정합니다.

   * > ```js
     > //Show 클릭
     > function MainView:onAButton9Click(comp, info, e)
     > {
     >
     >     //현재 생성되어 있는 윈도우를 컨테이너 아이디로 찾습니다.
     >     var winA = AWindow.findWindow('winA');
     >     
     >     if(!winA)
     >     {
     >         AToast.show('윈도우 WinA가 존재하지 않습니다.');
     >         return;
     >     }
     >     
     >     //hide는 윈도우 객체를 보이지만 않게 한것입니다.
     >     if(winA) winA.getContainer().show();
     >
     > };
     > ```

9. Close 버튼에 Click 이벤트를 설정하고 설정 함수 내용을 다음과 같이 수정합니다.

   * > ```js
     > //Close 클릭
     > function MainView:onAButton10Click(comp, info, e)
     > {
     > 	//현재 생성되어 있는 윈도우를 컨테이너 아이디로 찾습니다.
     > 	var winA = AWindow.findWindow('winA');
     > 	
     > 	//hide는 윈도우 객체를 보이지만 않게 한것입니다.
     > 	if(winA) winA.getContainer().close();
     >
     > };
     > ```

10. F5 키를 이용해서 프로젝트를 빌드후 실행합니다.

    * Open, Hide, Show, Close 버튼들과 오픈된 윈도우의 Hide, Close 버튼을 번갈아 클릭해보면서 윈도우가 존재하는지 Remove 되었는지 확인합니다.





