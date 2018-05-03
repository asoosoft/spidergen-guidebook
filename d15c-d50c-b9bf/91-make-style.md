# 9.1. Make Style

---

> Download : [http://manual.spidergen.org/example/SG014.zip](http://manual.spidergen.org/example/SG014.zip)

1. 새 프로젝트 SG014를 생성합니다.
2. MainView를 추가하고 SG014App.cls 파일을 아래와 같이 수정합니다.
   * > ```js
     > function SG014App:onReady()
     > {
     >     super.onReady();
     >
     >     var navigator = new ANavigator();
     >     navigator.registerPage('Source/MainView.lay', 'MainView');
     >     navigator.goPage('MainView');
     >
     > };
     > ```
3. MainView.lay를 오픈하고 다음 내용을 참고해서 컴포넌트를 배치 합니다.

| component | id | position | size |
| :--- | :--- | :--- | :--- |
| AButton | btnTest | left:50px, top:50px | width:120px, height:25px |

![](/assets/style-ex-001.png)

1. Project Pane에 트리뷰의 Template  폴더 위에서 마우스 우측 버튼을 클릭해서 컨텍스트 메뉴를 오픈합니다.
   * ![](/assets/style-ex-002.png)
2. 오픈된 컨텍스트 메뉴에서 New Template를 선택합니다.

   * 오픈된 New Template 다이얼로그에서 Name에 "common" 으로 입력합니다
   * ![](/assets/style-ex-004.png)
   * 생성후 Template 폴더내 common.tpl, common.stl, common.tlay 파일이 생긴걸 확인합니다.
     * .tpl : 스타일 Item 편집기 입니다.
     * .stl: 스타일 Item에 의해 생성된 CSS 입니다.
     * .tlay: 서식 복사를 할 수 있는 스타일 템플릿 객체 그룹입니다.
     * ![](/assets/style-ex-006.png)

3. 먼저 common.tpl 파일을 오픈 합니다.

4. 레이아웃 트리 또는 레이아웃 화면에서 마우스 우측 버튼 클릭으로 컨텍스트 메뉴를 오픈합니다.![](/assets/style-ex-005.png)

5. 오픈된 컨텍스트 메뉴에서 Add Item 메뉴를 선택합니다. 레이아웃 뷰에 아이템이 추가되는걸 확인합니다. 총 3개의 스타일 아이템을 생성합니다.  
   ![](/assets/style-ex-007.png)

6. 추가된 아이템을 다음 내용을 참고해서 속성을 수정합니다.

| pane | property | value |
| :--- | :--- | :--- |
| class | ID | btn\_normal |
| Appearance | Text | btn\_normal |
|  | Background &gt; color | rgb\(224, 224, 224\) |
|  | Border &gt; left, top, Right, Bottom | 2px solid rgb\(125, 125, 125\) |
|  | Border &gt; Round | 5px |

| pane | property | value |
| :--- | :--- | :--- |
| class | ID | btn\_over |
| Appearance | Text | btn\_over |
|  | Font &gt; color | rgb\(0, 0, 0\) |
|  | Background &gt; color | rgb\(245, 245, 245\) |
|  | Border &gt; left, top, Right, Bottom | 2px solid rgb\(125, 125, 125\) |
|  | Border &gt; Round | 5px |

| pane | property | value |
| :--- | :--- | :--- |
| class | ID | btn\_down |
| Appearance | Text | btn\_down |
|  | Font &gt; color | rgb\(255, 255, 255\) |
|  | Background &gt; color | rgb\(125, 125, 125\) |
|  | Border &gt; Left, Top, Right, bottom | 2px solid rgb\(51, 51, 51\) |
|  | Border &gt; Round | 5px |

![](/assets/style-ex-010.png)

1. 스타일 아이템에 속성 설정이 다 되고 나면 레이아웃 트리의 맨 상단 노드에서 컨텍스트 메뉴를 오픈 하고 Make All Styles 메뉴를 선택합니다.

   * ![](/assets/style-ex-011.png)

2. Make All Styles 메뉴를 실행하면 .stl 파일에 스타일 CSS가 생성됩니다.

   * ![](/assets/style-ex-009.png)

3. tpl 화면에서도 아이템을 선택하면 CSS뷰에 해당 아이템에 대한 CSS 가 생성된것을 확인합니다.

   * ![](/assets/style-ex-013.png)

4. common.tlay 파일을 오픈합니다. 버튼 컨트롤을 추가합니다.

   * 추가된 버튼을 선택하고 Appearance &gt; Display &gt; Default Style을 선택합니다. 
   * 오픈된 Style Picker 윈도우에 "common \_ _btn \_ normal\_"을 선택합니다. 버튼에 해당  css가 적용 되는걸 확인합니다.
     * ![](/assets/style-ex-020.png)
     * ![](/assets/style-ex-021.png)
   * 앞과 동일한 방법으로 버튼에 Appearance &gt; Style &gt; Over 항목에 "common \_ btn \_ over" 스타일을 적용합니다.
   * 동일한 방법으로 버튼에 Appearance &gt; Style &gt; Over 항목에 "common _ \_\_ btn _ \_\_ down" 스타일을 적용합니다.

   * 모든 스타일이 적용되고 나면 서식 복사를 합니다. 서식 복사란 컴포넌트의 스타일 속성만 복사하여 기존에 작성된 컴포넌트에 적용할 수 있는 기능입니다.

     * .tlay 화면에서 스타일이 적용된 버튼을 선택하고 Ctrl + d 버튼을 선택해서 서식을 캐시에 복사합니다.
     * MainView.lay 화면을 오픈합니다. 화면내에 버튼 컴포넌트를 선택합니다.
     * ![](/assets/style-ex-024.png)
     * Ctrl + v 버튼을 클릭해서 복사된 서식을 선택 컴포넌트에 적용하게 합니다. Appearance &gt; Style 과 Appearance &gt;Display &gt; Default Style 내용을 서식 적용 전과 후의 변화를 확인 합니다.
     * ![](/assets/style-ex-025.png)

5. F5 키를 이용해서 프로젝트를 빌드하고 실행합니다.

   * 버튼에 마우스를 올려보고 클릭해보면서 생성한 스타일 템플릿이 잘 적용되었는지 확인 합니다.



