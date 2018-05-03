# 8.1. AMessageBox

---

> Download : [http://manual.spidergen.org/example/SG013.zip](http://manual.spidergen.org/example/SG013.zip)

1. 새 프로젝트 SG013을 생성합니다.
2. MainView를 추가하고 SG013App.cls를 아래와 같이 수정합니다.

   * > ```js
     > function SG013App:onReady()
     > {
     >     super.onReady();
     >
     >     var navigator = new ANavigator();
     >     navigator.registerPage('Source/MainView.lay', 'MainView');
     >     navigator.goPage('MainView');
     >
     > };
     > ```

3. MainView.lay를 오픈하고 5개의 버튼을 추가 합니다.

| component | position | size | text |
| :--- | :--- | :--- | :--- |
| AButton | left:20px, top:20px | w-stretch:20px, height:22px | Empty |
| AButton | left:20px, top:50px | w-stretch:20px, height:22px | OK |
| AButton | left:20px, top:80px | w-stretch:20px, height:22px | OK CANCEL |
| AButton | left:20px, top:110px | w-stretch:20px, height:22px | YES NO |
| AButton | left:20px, top:140px | w-stretch:20px, height:22px | YES NO CANCEL |

1. 각 버튼에 다음과 같이 Click 이벤트를 설정합니다.  
   * Empty 버튼에 Click 이벤트를 설정 합니다. 설정 함수는 다음과 같이 수정합니다.
     * > ```js
       > //EMPTY
       > function MainView:onAButton2Click(comp, info, e)
       > {
       >     //title, message, buttonType
       >     AfcMessageBox('message', '버튼이 없이 메시지만 노출됩니다.', AMessageBox.EMPTY);
       >
       > };
       > ```
     * F5 키로 프로젝트를 빌드하고 실행합니다. Empty 버튼을 클릭합니다.
     * ![](/assets/msg-ex-001.png)
   * OK 버튼에 Click 이벤트를 설정 합니다. 설정 함수는 다음과 같이 수정합니다.
     * > ```js
       > //OK
       > function MainView:onAButton3Click(comp, info, e)
       > {
       >     //title, message, buttonType, callback
       >     AfcMessageBox('message', 'OK버튼과 메시지가 노출됩니다.', AMessageBox.OK, 
       >     function(result, data){
       >         if(result==0){
       >             AToast.show('OK');
       >         }
       >     });
       >
       > };
       > ```
     * AfcMessageBox\(\) 의  callback 함수는 result, data 를 파라미터로 넘겨 받습니다. result에는 클릭된 버튼의 상수값을 전달합니다.  
     * ![](/assets/msg-ex-002.png)
   * OK CANCEL 버튼에 Click 이벤트를 설정합니다. 설정 함수는 다음과 같이 수정합니다.
     * > ```js
       > function MainView:onAButton4Click(comp, info, e)
       > {
       >     //title, message, buttonType, callback
       >     AfcMessageBox('message', 'OK, CANCEL 버튼과 메시지가 노출됩니다.', AMessageBox.OK_CANCEL, 
       >     function(result, data){
       >     
       >         if(result == 0)
       >         {
       >             AToast.show('OK');
       >         }
       >         else if(result == 1)
       >         {
       >             AToast.show('CANCEL');
       >         }
       >         
       >     });
       >
       > };
       > ```
     * 버튼 타입이 AMessageBox.OK\_CANCEL 이므로  callback 함수의 파라미터 result에 0과 1이 전달 됩니다. 
     * F5 키로 프로젝트를 빌드하고 실행합니다.
     * ![](/assets/msg-ex-005.png)
     * Cancel 버튼을 클릭하고 출력되는 메시지를 확인합니다.
     * ![](/assets/msg-ex-006.png)
   * YES NO 버튼에 Click 이벤트를 설정합니다. 설정 함수는 다음과 같이 수정합니다.
     * > ```js
       > //YES NO
       > function MainView:onAButton5Click(comp, info, e)
       > {
       >     //title, message, buttonType, callback
       >     AfcMessageBox('message', 'YES, NO 버튼과 메시지가 노출됩니다.', AMessageBox.YES_NO, 
       >     function(result, data){
       >     
       >         if(result==0)
       >         {
       >             AToast.show('YES');
       >         }
       >         else if(result==1)
       >         {
       >             AToast.show('NO');
       >         }
       >         
       >     });
       >
       > };
       > ```
     * F5 키로 프로젝트를 빌드하고 실행합니다.
     * 오픈된 메시지박스에서 이번에는 YES 버튼을 클릭해보고 출력되는 메시지를 확인합니다.
     * ![](/assets/msg-ex-007.png)
     * ![](/assets/msg-ex-009.png)
   * YES NO CANCEL 버튼에 Click 이벤트를 설정합니다. 설정 함수는 다음과 같이 수정합니다.
     * > ```js
       > function MainView:onAButton6Click(comp, info, e)
       > {
       >     //title, message, buttonType, callback
       >     AfcMessageBox('message', 'YES, NO, CANCEL 버튼과 메시지가 노출됩니다.', AMessageBox.YES_NO_CANCEL, 
       >     function(result, data){
       >     
       >         if(result==0)
       >         {
       >             AToast.show('YES');
       >         }
       >         else if(result==1)
       >         {
       >             AToast.show('NO');
       >         }
       >         else if(result==2)
       >         {
       >             AToast.show('CANCEL');
       >         }
       >         
       >     });
       >
       > };
       > ```
     * AMessageBox.YES\_NO\_CANCEL 버튼 타입은 버튼 순서대로 클릭시 0, 1, 2 값이 전달됩니다.
     * F5키를 이용해서 프로젝트를 빌드하고 실행합니다.
     * 각 버튼들을 클릭해보고 출력되는 메시지를 확인합니다. 
     * ![](/assets/msg-ex-010.png)



