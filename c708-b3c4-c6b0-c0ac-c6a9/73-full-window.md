# 7.3. Full Window

---

> Download1 : [http://manual.spidergen.org/example/SG012.zip](http://manual.spidergen.org/example/SG012.zip)
>
> Download2 :[ http://manual.spidergen.org/example/WindowSample.zip](http://manual.spidergen.org/example/WindowSample.zip)

윈도우를 화면에 풀 사이즈로 오픈 하는 방법은 일반적인 윈도우 오픈 방식과 동일합니다. 단지 윈도우 사이즈를 % 형식으로 설정해서 오픈합니다.

1. MainView에서 "Full Size Window" 버튼에 Click 이벤트를 설정하고 설정 함수는 다음과 같이 수정합니다.
   * > ```js
     > //Full Window Open
     > function MainView:onAButton5Click(comp, info, e)
     > {
     >
     >     var wnd = new AWindow('full-window');
     >     
     >     wnd.open('Source/Views/WinView.lay', this.getContainer(), 0, 0, '100%', '100%');
     >
     > };
     > ```
2. F5 키로 프로젝트를 빌드하고 실행합니다.
   * "Full Size Window" 버튼을 클릭합니다. 그리고 화면 가득 윈도우가 오픈되는것을 확인합니다.
   * ![](/assets/win-ex-011.png)
   * ![](/assets/win-ex-012.png)



