# 6.4.2. CheckBox Example

---

> Download : [http://manual.spidergen.org/example/SG001.zip](http://manual.spidergen.org/example/SG001.zip)
>
> youtube : [https://youtu.be/pZX0j-n8FQg](https://youtu.be/pZX0j-n8FQg)

1. File &gt; Open Project 클릭
   * 오픈된 탐색기에서 프로젝트 폴더를 선택하시고 SG001.prj 파일을 클릭합니다.
2. MainView.lay 파일을 오픈합니다.

3. MainView에 다음 내용을 참고해서 컴포넌트를 배치합니다.

| component | id | group | position | size | text | value |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ALabel | lbl001 |  | left:50px, top:50px | widht:auto, height:20px | 체크값 |  |
| AButton | btn001 |  | right:50px, top:50px | width:80px, height:22px | 확인 |  |
| ACheckBox |  | checks | left:50px, top:100px | width:80px, height:20px | 사과 | 100 |
| ACheckBox |  | checks | left:180px, top:100px | width:80px, 20px | 포도 | 200 |
| ACheckBox |  | checks | left:300px, top:100px | width:80px, height:20px | 오렌지 | 300 |

![](/assets/chk-ex-004.png)

1. 스파이더젠에서 컴포넌트 객체에 접근하는 방법으로는 컴포넌트의 ID를 이용하는 방법과  Group을 이용하는 방법이 있습니다.

   * **ID를 이용하는 방법** : \*.cls 파일에서 this.컴포넌트ID 형태로 접근하거나 **findCompById\('컴포넌트ID'\) **함수를 이용해서 레이아웃의 컴포넌트 객체에 접근 할 수 있습니다.

   * **Group 이용하는 방법** : Class Pane &gt; Identity &gt; Group에 동일한 그룹명을 입력하고 **findCompByGroup\('그룹명'\)** 함수를 이용하면 컴포넌트 객체들에 접근 할 수 있는 배열객체를 리턴받아 접근 할 수 있습니다. 배열의 인덱스 순서는 레이아웃의 객체 순서와 동일 합니다.

2. MainView.cls 클래스 파일을 오픈하고 다음과 같이 소스 내용을 수정합니다.

   * MainView\(\) 클래스 함수에 멤버 변수를 추가 합니다.  
   * > ```js
     > class MainView()
     > {
     >     super();
     >
     >     this.chks = null; //체크박스 배열 변수
     >
     > }
     > extends AView;
     > ```
   * Init 이벤트 메소드에 체크박스에  접근하기 위한 배열을 위한 멤버변수를 등록합니다.

   * > ```js
     > function MainView:init(context, evtListener)
     > {
     >     super.init(context, evtListener);
     >     
     >     /*그룹명을 이용해서 체크박스를 배열로 얻기*/
     >     this.chks = this.findCompByGroup('checks');    
     >     
     > };
     > ```
   * 버튼 컴포넌트에 클릭 이벤트를 다시 설정 합니다. Class Pane &gt; Event &gt; Click 우측 영역을 더블클릭하고 이벤트 메소드 함수명은 기본으로 등록합니다. 해당 이벤트 메소드의 내용은 다음과 같이 수정합니다.

   * > ```js
     > function MainView:onBtn001Click(comp, info, e)
     > {
     >     
     >     var chkValue = '';
     >     
     >     for(var chk in this.chks)
     >     {
     >         var currChk = this.chks[chk];
     >         
     >         //체크된 체크박스일 경우
     >         if(currChk.isChecked){
     >             chkValue += currChk.getValue() + ' ';
     >         }
     >     }
     >     
     >     this.lbl001.setText(chkValue); //레이블에 출력
     >     
     >     
     > };
     > ```

3. F5 키를 누르거나 Build &gt; Run Project를 실행합니다.

   * 실행된 화면에서 체크박스를 선택하고 확인버튼을 클릭합니다.  
   * 레이블에 선택된 체크박스의 Value 값을 출력하는걸 확인합니다.
   * ![](/assets/checkbox-ex-005.png)



