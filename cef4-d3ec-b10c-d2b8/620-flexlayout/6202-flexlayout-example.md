# 6.20.2. FlexLayout Example

---

> Download : [http://manual.spidergen.org/example/SG009.zip](http://manual.spidergen.org/example/SG009.zip)

1. 기존의 SG009 프로젝트를 오픈합니다.
2. 새 뷰  SubView를 추가합니다.
3. SG009App.cls 파일을 오픈하고 아래와 같이 registerPage를 추가합니다.
   * > ```js
     > function SG009App:onReady()
     > {
     >     super.onReady();
     >
     >     var navigator = new ANavigator();
     >     navigator.registerPage('Source/MainView.lay', 'MainView');
     >     navigator.registerPage('Source/SubView.lay', 'SubView');
     >     navigator.goPage('SubView');
     >
     > };
     > ```
4. SubView.lay 파일을 오픈하고 다음 내용을 참고해서 컴포넌트를 배치합니다.

| component | position | size | margin | etc |
| :--- | :--- | :--- | :--- | :--- |
| AFlexLayout | left:20px, top:20px | w-stretch:20px, height:50px |  | Direction:row, Wrap:wrap, H-Align:center, V-Align:center, Arrange Line:from top |
| ALabel | left:0px, top:0px | width:auto, height:auto | left:10px |  |
| ATextField | left:0px, top:0px | width:200px, height:22px | left:10px | Placeholder:검색어를 입력하세요. Data Type : text, Align:left |
| AButton | left:0px, top:0px | width:80px, height:22px | left:10px | - |

* ALabel, ATextField, AButton 을 FlexLayout의 자속 요소로 추가 합니다.
* ![](/assets/flexlayout-ex-005.png)

* F5 키를 이용해서 프로젝트를 빌드하고 실행합니다.

  * 창의 높이를 늘렸다가 줄여봅니다. 컴포넌트들이 높이의 중앙에 위치하는걸 확인합니다.
    * ![](/assets/flexlayout-ex-008.png)



