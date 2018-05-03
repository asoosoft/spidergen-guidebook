# 6.22.1. FlexView Example

---

> Download : [http://manual.spidergen.org/example/SG011.zip](http://manual.spidergen.org/example/SG002.zip)

1. 새 프로젝트 SG011을 생성합니다.
2. Source  폴더 아래 MainView를 추가합니다.
3. 이번에도 싱글뷰 형식으로 어플리케이션 파일을 수정 합니다. SG011App.cls를 아래와 같이 수정합니다.
   * > ```js
     > function SG011App:onReady()
     > {
     >     super.onReady();
     >     
     >     this.setMainContainer(new APage('main'));
     >     this.mainContainer.open('Source/MainView.lay');
     >
     > };
     > ```
4. MainView.lay를 다음 내용을 참고해서 컴포넌트를 배치합니다.
   * | component | id | position | size | text | etc |
     | :--- | :--- | :--- | :--- | :--- | :--- |
     | AFlexView | flexView | left:20px, top:60px | w-stretch:20px, h-stretch:60px |  |  |
     | AButton | btnAddView | right:20px, top:10px | width:80px, height:40px | Add |  |
     | ALabel | lblViewCnt | left:20px, top:30px | width:auto, height:auto | views: |  |
     | ATextField | txtViewIndex | left:20px, bottom:30px | width:40px, height:20px |  | Appearance &gt; Data &gt; data type : number |
     | AButton | btnGet | left:70px, bottom:30px | width:50px, height:20px | Get |  |
     | ALabel | lblInfo | left:140px, bottom:20px | w-stretch:20px, height:20px |  | Appearance &gt; Data &gt; Line Height : 20px |
   * ![](/assets/flexview-ex-001.png)
5. Source 폴더 아래 Views 폴더를 생성합니다. 
6. Views 폴더 내에 InnerView0, InnerView1, InnerView2 뷰를 각각 추가합니다.
   * | view | background | lable id | text |
     | :--- | :--- | :--- | :--- |
     | InnerView0 | yellow | lbl001 | 첫번째 뷰 입니다. |
     | InnerView1 | blue | lbl001 | 두번째 뷰 입니다. |
     | InnerView2 | green | lbl001 | 세번재 뷰 입니다. |
   * ![](/assets/flexview-ex-010.png)
   * ![](/assets/flexview-ex-011.png)
   * ![](/assets/flexview-ex-012.png)
7. InnerView의 버튼에 Click 이벤트를 다음과 같이 수정합니다.
   * > ```js
     > function InnerView2:onAButton1Click(comp, info, e)
     > {
     >
     >     AToast.show(this.lbl001.getText());
     > };
     > ```
   * 나머지 InnerView도 위 내용을 참고해서 추가합니다.
8. MainView.cls 파일을 오픈합니다.
   * cnt 멤버변수를 추가합니다. 이 변수는 현재 추가되는 뷰의 카운트를 저장하는 변수입니다.
     * > ```js
       > class MainView()
       > {
       >     super();
       >
       >     this.cnt = 0; //이너뷰 카운트
       >
       > }
       > extends AView;
       > ```
   * Add 버튼에 Click 이벤트를 설정합니다. 버튼이 클릭되면 카운트 멤버변수를 이용해서 InnerView를 Insert 합니다.
     * > ```js
       > function MainView:onBtnAddViewClick(comp, info, e)
       > {
       >
       >     if(this.cnt >= 3){
       >         AToast.show('더이상 뷰를 추가 할 수 없습니다.');
       >         return;
       >     }
       >     
       >     this.flexView.insertView('Source/Views/InnerView' + this.cnt + '.lay');
       >     
       >     this.cnt = this.flexView.views.length;
       >     
       >     //현재 insert된 뷰의 수
       >     this.lblViewCnt.setText('Views : ' + this.cnt);
       >
       > };
       > ```
9. F5로 프로젝트를 빌드후 실행합니다.
   * Add 버튼을 클릭해서 뷰를 Insert 합니다.
   * 뷰가 다 Insert되면 텍스트 필드에 원하는 인덱스 번호를 넣고 Get버튼을 클릭해서 내용이 출력되는걸 확인합니다.
   * ![](/assets/flexview-ex-013.png)





