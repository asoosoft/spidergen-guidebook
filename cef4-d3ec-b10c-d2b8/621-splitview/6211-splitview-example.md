# 6.21.1. SplitView Example

---

> Download : [http://manual.spidergen.org/example/SG010.zip](http://manual.spidergen.org/example/SG010.zip)

1. 새 프로젝트 SG010을 생성합니다.
2. MainView를 추가하고  SG010App.cls를 오픈해서 다음 내용과 같이 싱글뷰로 어플리케이션을 생성합니다.
   * > ```js
     > function SG010App:onReady()
     > {
     >     super.onReady();
     >
     >     this.setMainContainer(new APage('main'));
     >     this.mainContainer.open('Source/MainView.lay');
     >
     > };
     > ```
3. Source 폴더 아래 Views 폴더를 생성합니다.
4. Views 폴더에 LeftView, RightView를 추가합니다.
5. MainView.cls를 오픈하고 다음과 같이 멤버변수를 추가합니다.
   * > ```js
     > class MainView()
     > {
     >     super();
     >
     >     this.leftView =  null;
     >     this.rightView = null;
     >
     > }
     > extends AView;
     > ```
6. MainView에 SplitView 다음 내용을 참고해서 컴포넌트를 배치합니다.

| component | id | position | size |
| :--- | :--- | :--- | :--- |
| ASplitView | splitView | left:0px, top:0px | width:100%, height:100px |

* MainView의 onInitDone\(\) 함수에서 다음 내용을 참고해서 스플릿을 생성합니다.

| view count | left view | right view | direction |
| :--- | :--- | :--- | :--- |
| 2 | width:300px | width:-1\(전체사이즈에서 300px를 뺀 나머지 사이즈\) | row |

* > ```js
  > function MainView:onInitDone()
  > {
  >
  >     //스플릿 생성
  >     this.splitView.createSplit(2, [200, -1], 'row');
  >     
  >     //스플릿에 뷰 설정 
  >     this.leftView = this.splitView.setSplitView(0, 'Source/Views/LeftView.lay');    
  >     this.rightView = this.splitView.setSplitView(1, 'Source/Views/RightView.lay');    
  >
  > };
  > ```
* LeftView.lay 파일을 오픈하고 아래 내용을 참고해서 컴포넌트를 배치합니다.

  * LeftView.lay 백그라운드 컬러를 \#acacac로 설정합니다.

| component | id | position | size | text | placeholder |
| :--- | :--- | :--- | :--- | :--- | :--- |
| ATextField | txtLeft | left:20px, top:50px | w-stretch:20px, height:22px |  | 우측에 보낼 내용을 입력하세요. |
| ALabel | lblLabel | left:20px, top:150px | w-stretch:20px, height:auto | 오른쪽에 내용을 읽어 옵니다. |  |
| AButton | btnSend | left:20px, top:80px | width:80px, height:22px | send |  |
| AButton | btnGet | left:20px, top:180px | width:80px, height:22px | get |  |

![](/assets/splitview-ex-001.png)

* RightView.lay 파일을 오픈하고 다음 내용을 참고해서 컴포넌트를 배치하세요.

| component | id | position | size | text | placeholder |
| :--- | :--- | :--- | :--- | :--- | :--- |
| ATextField | txtRight | left:50px, top:50px | width:300px, height:22px |  | 좌측에 보낼 내용을 입력하세요. |
| ALabel | lblRight | left:50px, top150px | width:300px, height:auto | 왼쪽에 내용을 읽어 옵니다. |  |
| AButton | btnSend | left:50px, top:80px | width:80px, height:22px | send |  |
| AButton | btnGet | left:50px, top:180px | width:80px, height:22px | get | - |

![](/assets/splitview-ex-002.png)

1. LeftView.cls 파일을 오픈하고 멤버변수를 다음과 같이 설정합니다.

   * > ```js
     > class LeftView()
     > {
     >     super();
     >
     >     this.mainView = null;    
     >     this.rightView = null;
     >
     > }
     > extends AView;
     > ```

2. LeftView.cls에 onInitDone\(\)에 다음과 같이 수정합니다.

   * > ```js
     > function LeftView:onInitDone()
     > {
     >     //메인뷰 설정
     >     this.mainView = this.getContainer().getView();    
     >     
     >     this.rightView = this.mainView.splitView.getSplitView(1);    
     >     
     > };
     > ```
   * getContainer\(\) 함수는 현재뷰의 최상위 컨테이너를 리턴해줍니다. 따라서 현재 프로젝트가 싱글뷰이므로  main 컨테이너가 리텁됩니다. getView\(\) 메서드는 해당 컨테이너의 뷰를 리턴합니다. 따라서 main 컨테이너의 뷰인 메인뷰가 리턴됩니다.
   * 멤버변수 rightView에는 MainView에 있는 splitView를 통해서 나누어진 뷰들 중 두번째 뷰를 얻어 저장합니다.

3. LeftView의 Send 버튼에 다음과 같이 클릭 이벤트를 설정해서 입력된 내용을 우측 레이블에 노출되게 합니다.

   * > ```js
     > function LeftView:onBtnSendClick(comp, info, e)
     > {
     >
     >     var sendTxt = this.txtLeft.getText();
     >     
     >     if(!sendTxt || sendTxt.length < 1){
     >         
     >         AToast.show('전송할 내용을 입력하세요.');
     >         return;
     >     }
     >
     >     this.rightView.lblRight.setText(sendTxt);
     >
     > };
     > ```

4. LeftView의 get 버튼에 다음과 같이 클릭 이벤트를 설정하고 우측의 텍스트에 입력된 내용을 가져와서 레이블에 출력되게 합니다.

   * > ```js
     > function LeftView:onBtnGetClick(comp, info, e)
     > {
     >
     >     var getTxt = this.rightView.txtRight.getText();
     >     
     >     if(!getTxt || getTxt.length < 1)
     >     {
     >         AToast.show('입력된 내용이 없습니다.');
     >         return;
     >     }
     >     
     >     this.lblLeft.setText(getTxt);
     >
     > };
     > ```

5. RightView 또한 위의 방법을 참고해서 아래 내용과 같이 .cls 파일을 수정합니다. 먼저 멤버변수를 추가합니다.

   * > ```js
     > class RightView()
     > {
     >     super();
     >
     >     this.mainView = null;    
     >
     > }
     > extends AView;
     > ```

6. RightView의 onInitDone\(\) 함수에서 MainView 를 설정합니다. 이미 앞에서 MainView에 SplitView를 통해 멤버변수 leftView, rightView를 각각 저장해 놓았습니다. 때문에 RightView에서는 이 MainView를 얻어 leftView에 접근하도록 합니다.

   * > ```js
     > function RightView:onInitDone()
     > {
     >
     >     this.mainView = this.getContainer().getView();    
     >
     > };
     > ```

7. RightView의 send 버튼에 클릭 이벤트를 설정하고 아래와 같이 내용을 추가합니다. LeftView의 send버튼 기능 구현과 RightView 기능 구현 차이를 확인하시기 바랍니다.

   * > ```js
     > function RightView:onBtnSendClick(comp, info, e)
     > {
     >
     >     var sendTxt = this.txtRight.getText();
     >     
     >     if(!sendTxt || sendTxt.length < 1){
     >         AToast.show('전송할 내용을 입력하세요.');
     >         return;
     >     }
     >     
     >     this.mainView.leftView.lblLeft.setText(sendTxt);
     >
     > };
     > ```

8. RightView의 get 버튼에 클릭 이벤트를 설정하고 아래와 같이 내용을 추가합니다.

   * > ```js
     > function RightView:onBtnGetClick(comp, info, e)
     > {
     >
     >     var getTxt = this.mainView.leftView.txtLeft.getText();
     >     
     >     if(!getTxt || getTxt.length < 1){
     >         AToast.show('입력된 내용이 없습니다.');
     >         return;
     >     }
     >     
     >     this.lblRight.setText(getTxt);
     > };
     > ```

9. F5 키로 프로젝트를 빌드하고 실행합니다.

   * 좌우측에 텍스트 필드에 각각 내용을 입력하고 send 버튼을 클릭해봅니다. 서로 상대편의 레이블에 내용이 잘 출력되는 확인합니다.
   * ![](/assets/splitview-ex-009.png)
   * 이번에는 각 뷰의 get 버튼을 클릭합니다. 서로 상대편의 텍스트 필드 내용을 잘 가져오는지 확인합니다.
   * ![](/assets/splitview-ex-006.png)



