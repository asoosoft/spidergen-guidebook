# 6.9.2. TextArea Example

---

> Download : [http://manual.spidergen.org/example/SG003.zip](http://manual.spidergen.org/example/SG003.zip)

1. 새 프로젝트 SG003을 생성합니다.
2. M001 이름의 뷰를 추가 합니다.
3. SG003App.cls 파일을 오픈하고 아래와 같이 수정합니다.
   > ```js
   > function SG003App:onReady()
   > {
   >     super.onReady();
   >
   >     var navigator = new ANavigator();
   >     navigator.registerPage('Source/M001.lay', 'M001');
   >     navigator.goPage('M001');
   >
   > };
   > ```
4. M001.lay 파일을 오픈하고 아래 내용으로 컴포넌트를 배치합니다.

| component | id | position | size | text | playcehold |
| :--- | :--- | :--- | :--- | :--- | :--- |
| ATextField | txt001 | left:20px, top:200px | width:240px, height:22px |  | 내용을 입력하세요. |
| ATextArea | txtArea001 | left:20px, top:20px | width:340px, height:160px |  | - |
| AButton | btnAdd | left:280px, top:200px | width:80px, height:22px | 추가 | - |

![](/assets/textarea-ex-004.png)

1. 버튼에 클릭 이벤트를 설정합니다. 이벤트 함수 내용은 아래와 같습니다.
   > ```js
   > function M001:onBtnAddClick(comp, info, e)
   > {
   >
   >     var txt = this.txt001.getText();
   >
   >     if(!txt || txt.length < 1){
   >         AToast.show('추가할 내용을 입력하세요.');        
   >         return;
   >     }
   >     
   >     //기존의 텍스트에 새 텍스트 추가
   >     this.txtArea001.setText(
   >         this.txtArea001.getText() + '\n' + this.txt001.getText()
   >     );
   >     
   >     //사용자 함수
   >     this.initText();
   >     
   >
   > };
   > ```
2. 사용자 함수 **initText\(\)** 함수를 추가합니다.  직접 문법 형식에 맞게 입력을 하거나 Ctrl + Alt + F 클릭하고 오픈된 다이얼 로그에 Function Name을 initText라고 입력하시면 코드뷰에 함수가 생성됩니다.
   * ![](/assets/textarea-ex-005.png)
   * > ```js
     > function M001:initText()
     > {
     >
     >     //입력 텍스트 초기화
     >     this.txt001.setText('');
     >
     > };
     > ```
3. F5 키를 이용해서 빌드하고 실행합니다.
   * 먼저 실행 화면에서 텍스트를 입력하지 않고 추가 버튼을 클릭해서 메시지 토스트를 확인합니다.
   * 두번째로 텍스트를 입력하고 추가 버튼을 클릭해 봅니다. TextArea 컴포넌트 영역에 입력하는 텍스트가 잘 추가되는지 확인합니다.
   * 마지막으로 지금까지 입력된 내용 다음에 TextArea에 직접 입력을 해봅니다.
   * ![](/assets/textarea-ex-006.png)



