# 7.4. Frame Window

---

> Download1 : h[ttp://manual.spidergen.org/example/SG012.zip](http://manual.spidergen.org/example/SG012.zip)
>
> Download2 :[ http://manual.spidergen.org/example/WindowSample.zip](http://manual.spidergen.org/example/WindowSample.zip)

프레임 윈도우 사용 방법은 앞에서 설명한 윈도우 사용방법과 동일하며 단지 생성하는 방법에서만 차이점이 있습니다.

1. MainView에서 "Frame Window" 버튼에 Click 이벤트를 설정하고 설정 함수는 다음과 같이 수정합니다.
   * > ```js
     > //프레임 윈도우 
     > function MainView:onAButton6Click(comp, info, e)
     > {
     >     var wnd = new AFrameWnd('frame-window');    
     >     wnd.open('Source/Views/WinView.lay', this.getContainer(), 0, 0, 400, 300);
     >     wnd.setTitleText('Frame Window');
     >
     > };
     > ```
2. F5 키로 프로젝트를 빌드하고 실행합니다.
   * "Frame Window" 버튼을 클릭합니다. 윈도우 상단에 프레임이 존재하고 타이틀이 Frame Window 라고 되어 있는걸 확인합니다.
   * 상단의 프레임 부분을 마우스 우측 버튼을 누른 상태에서 이동해 봅니다. 윈도우가 움직임에 따라 이동하는걸 확인합니다.
   * 또 프레임 우측에 최소, 최대, 닫기 버튼을 클릭해 각각의 기능을 확인합니다.
   * ![](/assets/win-ex-014.png)



