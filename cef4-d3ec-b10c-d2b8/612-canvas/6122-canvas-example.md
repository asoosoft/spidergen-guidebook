# 6.12.2. Canvas Example

---

> Download : [http://manual.spidergen.org/example/SG004.zip](http://manual.spidergen.org/example/SG002.zip)

1. 새 프로젝트를 생성합니다. 프로젝트명은 SG004 입니다.
2. 뷰를 하나 추가합니다. MainView 이름으로 메인뷰를 추가합니다.
3. SG004App.cls 파일을 오픈하고 다음과 같이 내용을 수정합니다. 이번에는 네비게이터가 아닌 싱글뷰로 작성하겠습니다.

   * > ```js
     > function SG004App:onReady()
     > {
     >     super.onReady();
     >
     >     this.setMainContainer(new APage('main'));
     >     this.mainContainer.open('Source/MainView.lay');
     >
     > };
     > ```

4. Source 폴더 밑에 Views라는 폴더를 생성합니다.

5. Views 폴더 내에 T001 이름으로 뷰를 생성합니다.

   * 레이아웃의 워크뷰에 FullView를 체크합니다.
   * 뷰의 배경색을 연두색으로 변경합니다.
   * ![](/assets/view-ex-002.png)
   * 버튼을 추가합니다. 버튼에 Click 이벤트를 설정합니다. 설정 함수 내용을 다음과 같이 수정합니다.
   * > ```js
     > function T001:onAButton1Click(comp, info, e)
     > {
     >
     >     AToast.show('T001뷰 입니다.');
     >
     > };
     > ```

6. Views 폴더 내에 T002 이름으로 뷰를 생성합니다. T002.lay 파일을 오픈하고 아래 내용으로 화면을 구성합니다.

   * T001과 동일하게 레이아웃 워크뷰에 FullView를 체크합니다. \(기본적으로 체크되어 있음.\)
   * 뷰의 배경색을 파란색으로 변경합니다.
   * ![](/assets/view-ex-006.png)
   * 버튼 컴포넌트를 추가합니다. 버튼의  Click 이벤트를 설정합니다. 설정 함수 내용을 다음과 같이 수정합니다.
   * > ```js
     > function T002:onAButton1Click(comp, info, e)
     > {
     >
     >     AToast.show('T002 뷰 입니다.');
     >
     > };
     > ```

7. 이번에는 MainView에 컴포넌트를 다음과 같이 배치합니다.

   * 메인뷰 안에 컴포넌트뷰 view01, view02를 추가합니다. 이뷰들은 각각 서브뷰 T001, T002를 로드하여 보여주는 역할을 합니다.
   * | component | id | position | size | text |
     | :--- | :--- | :--- | :--- | :--- |
     | AButton | btnLoad | right:20px, top:10px | width:80px, height:20px | load view |
     | AView | view01 | left:20px, top:50px | width:400px, height:200px |  |
     | AView | view02 | left:20px, top:270px | width:400px, height:200px |  |
   * ![](/assets/view-ex-009.png)

8. 버튼에 Click 이벤트를 설정 합니다. 설정 함수는 다음과 같은 내용으로 수정합니다.

   * > ```js
     > function MainView:onBtnLoadClick(comp, info, e)
     > {
     >     //뷰를 로드 합니다.
     >     this.view01.loadView('Source/Views/T001.lay');
     >     
     >     this.view02.loadView('Source/Views/T002.lay');
     >     
     > };
     > ```

9. 프로젝트를 빌드하고 실행합니다.

   * Load View 버튼을 클릭합니다. MainView에 뷰 T001, T002가 로드 되는걸 확인합니다.
   * 로드된 각 T001, T002뷰에 버튼을 클릭해서 출력되는 메시지를 확인합니다.
   * ![](/assets/view-ex-005.png)





