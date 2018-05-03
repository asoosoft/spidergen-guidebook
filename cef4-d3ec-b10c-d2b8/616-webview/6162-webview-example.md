# 6.16.2. WebView Example

---

> Download : [http://manual.spidergen.org/example/SG007.zip](http://manual.spidergen.org/example/SG007.zip)

1. 새프로젝트 SG007을 생성합니다.
2. SG007App.cls 파일을 오픈하고 내용을 다음과 같이 수정합니다. 네비게이
   * > ```js
     > function SG007App:onReady()
     > {
     >     super.onReady();
     >
     >     var navigator = new ANavigator();
     >     navigator.registerPage('Source/MainView.lay', 'MainView');
     >     navigator.goPage('MainView');
     >
     > };
     > ```
3. MainView를 추가하고 다음 내용을 참고해서 컴포넌트를 배치합니다.

| component | id | position | size | text | placeholder | etc |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ATextField | url | left:10px, top:10px | w-stretch:100px, height:22px |  | Url을 입력하세요. |  |
| AButton | btnSend | right:10px, top:10px | width:80px, height:22px | SEND |  |  |
| AWebView | webView | left:10px, top:42px | w-stretch:10px, h-stretch:10px |  |  | border:1px, border-color:rgb\(125,125,125\) |

![](/assets/webview-ex-002.png)

1. SEND 버튼에 Click 이벤트를 설정합니다. 설정함수는 다음과 같이 수정합니다.
   * > ```js
     > function MainView:onBtnSendClick(comp, info, e)
     > {
     >
     >     var sendUrl = this.url.getText();
     >     
     >     this.webView.setUrl(sendUrl);
     >     
     > };
     > ```
2. F5 키로 프로젝트를 빌드하고 실행합니다. 
   * url에 정보를 입력하고 SEND 버튼을 클릭합니다. 해당 URL의 내용이 로드 되는지 확인합니다.



