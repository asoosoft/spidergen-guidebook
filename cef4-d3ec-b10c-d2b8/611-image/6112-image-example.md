# 6.11.2. Image Example

---

> Download : [http://manual.spidergen.org/example/SG003.zip](http://manual.spidergen.org/example/SG002.zip)

1. 이전에 작성한 프로젝트 SG003을 로드합니다.
   * 이전에 오픈했던 프로젝트는 File &gt; Recent projects  목록에서 프로젝트를 선택 할 수 있습니다.
2. M003 이름으로 뷰를 추가합니다.
3. SG003App.cls 파일을 오픈하고 네비게이터에 M003뷰를 추가합니다. 그리고 M003으로 이동하게 합니다.
   * > ```js
     > function SG003App:onReady()
     > {
     >     super.onReady();
     >
     >     var navigator = new ANavigator();
     >     navigator.registerPage('Source/M001.lay', 'M001');
     >     navigator.registerPage('Source/M002.lay', 'M002');
     >     navigator.registerPage('Source/M003.lay', 'M003');
     >     navigator.goPage('M003');
     >     
     > };
     > ```
4. M003.lay 파일을 오픈합니다. 아래 내용으로 레이아웃을 배치합니다.
   * | component | id | position | size |
     | :--- | :--- | :--- | :--- |
     | ASelectBox | select01 | left:20px, top:20px | width:260px, heigth:22px |
     | AImage | img01 | left:20px, top:60px | width:260px, height:260px |
   * ![](/assets/img-ex-002.png)
5. 윈도우 파일 탐색기를 오픈합니다. 사진폴더에 이미지를 복사 합니다. 
6. SG003 폴더 아래 Img 폴더를 생성하고 복사한 이미지를 붙여 넣기 합니다.
7. 스파이더젠 파일 탐색기에서 Assets 폴더 위에서 컨텍스트 메뉴를 오픈합니다.\(마우스 우측 버튼을 클릭\)

   * 컨텍스트 메뉴에서 Add existing files in directory... 메뉴를 클릭합니다. 해당 메뉴는 선택된 폴더내의 모든 파일을 프로젝트로 로드합니다.
   * 오픈된 폴더 찾기 다이얼로그에서 앞에서 생성한 SG003 &gt; Img 폴더를 선택합니다.  
     ![](/assets/img-ex-004.png)

8. M003.cls 파일을 오픈합니다. onInitDone\(\) 함수에 아래와 같이 내용을 수정합니다.

   * > ```js
     > function M003:onInitDone()
     > {
     >     
     >     this.select01.removeAll();
     >     
     >     this.select01.addItem('이미지를 선택하세요.', null);
     >     this.select01.addItem('꽃1', 'Chrysanthemum.jpg');
     >     this.select01.addItem('꽃2', 'Hydrangeas.jpg');
     >     this.select01.addItem('해파리', 'Jellyfish.jpg');
     >     this.select01.addItem('코알라', 'Koala.jpg');
     >     this.select01.addItem('집', 'Lighthouse.jpg');
     >     this.select01.addItem('팽귄', 'Penguins.jpg');
     >     this.select01.addItem('사막', 'sand.jpg');
     >     this.select01.addItem('튤립', 'Tulips.jpg');    
     >
     > };
     > ```

9. 셀렉트 박스에 Change 이벤트를 설정합니다. 설정 함수 내용은 아래와 같이 수정합니다.

   * > ```js
     > function M003:onSelect1Change(comp, info, e)
     > {
     >     
     >     this.img01.setImage('Assets/img/' + info);
     >
     > };
     > ```

10. F5 키로 빌드하고 실행합니다.

    * 셀렉트 박스를 선택합니다. 이미지가 변경되는 상황을 확인합니다.  
    * ![](/assets/img-ex-005.png)



