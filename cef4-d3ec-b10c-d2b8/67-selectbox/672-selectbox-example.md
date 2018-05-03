# 6.7.2. SelectBox Example

---

> Download : [http://manual.spidergen.org/example/SG002.zip](http://manual.spidergen.org/example/SG002.zip)

1. SG002 프로젝트를 오픈합니다.
2. V003 이름으로 뷰를 추가합니다.
3. 어플리케이션 파일 SG002App.cls을 오픈하고 V003 화면을 아래와 같이 네비게이터에 추가합니다.
   * > ```js
     > function SG002App:onReady()
     > {
     >     super.onReady();
     >
     >     //네비게이터 생성
     >     var navigator = new ANavigator();
     >     
     >     //페이지 등록
     >     navigator.registerPage('Source/Views/V001.lay', 'V001');
     >     navigator.registerPage('Source/Views/V002.lay', 'V002');
     >     navigator.registerPage('Source/Views/V003.lay', 'V003');
     >     
     >     //페이지 이동
     >     navigator.goPage('V003');
     >
     > };
     > ```
4. V003.lay 파일을 오픈하고 다음과 같이 컴포넌트를 배치합니다.
   * | component | id | position | size | text |
     | :--- | :--- | :--- | :--- | :--- |
     | ALabel | lbl001 | left:50px, top:30px | width:auto, height:20px | 체크값 |
     | ASelectBox | select1 | left:50px, top : 60px | width:140px, height:20px |  |
     | ASelectBox | select2 | left:50px, top:90px | width:140px, height:22px |  |
   * ![](/assets/selectbox-ex-003.png)
5. V003.cls 파일을 오픈하고 내용을 아래와 같이 수정합니다.

   * V003  클래스 함수에 멤버변수 data를 생성합니다.
   * > ```js
     > class V003()
     > {
     >     super();
     >
     >     //데이터 변수 설정
     >     this.data = [
     >         {text : '사과' , items : ['서울', '경기', '강원']},
     >         {text : '포도' , items : ['경북', '경남', '충북', '충남']},
     >         {text : '오렌지', items : ['전남', '전북', '제주']}
     >     ];    
     >
     > }
     > ```
   * onInitDone\(\) 함수에서 컴포넌트들의 초기화를 하고 첫번째 셀렉트박스 \(select1\)에 아이템 데이터를 추가합니다.
   * > ```js
     > function V003:onInitDone()
     > {
     >
     >     //레이블 초기화
     >     this.lbl001.setText('선택내용');
     >     
     >     //셀렉트박스 초기화(아이템 모두 삭제)
     >     this.select1.removeAll();    
     >         
     >     //첫번째 셀렉트박스 데이터 초기화    
     >     var i=0, imax = this.data.length;
     >     for(i=0; i < imax; i++){
     >         //addItem(text, value, data)    
     >         this.select1.addItem(this.data[i].text, i, this.data[i].items);
     >     }
     >
     > };
     > ```
   * 첫번째 셀렉트박스 \(select1\)에 change 이벤트를 설정하고 설정 함수를 아래와 같이 추가합니다.  
     첫번째 셀렉트박스 \(select1\)이 선택되면 두번째 셀렉트박스 \(select2\)에 아이템 데이터를 동적으로 추가합니다.

   * > ```js
     > function V003:onSelect1Change(comp, info, e)
     > {
     >
     >     //현재 셀렉트된 아이템의 data
     >     var selItemData = comp.getSelectedItemData();
     >     
     >     
     >     //두번째 셀렉트박스 아이템 초기화(모두 삭제)
     >     this.select2.removeAll(); 
     >     
     >         
     >     //선택아이템
     >     this.select2.addItem('지역선택', '');
     >         
     >     var i=0, imax = selItemData.length, 
     >         selitem = null;
     >     
     >     for(i=0; i < imax; i++)
     >     {
     >         selitem = selItemData[i];
     >         this.select2.addItem(selitem, selitem);
     >     }
     >
     > };
     > ```
   * 두번째 셀렉트박스\(select2\) 에 change 이벤트를 설정하고 설정 함수를 아래와 같이 수정합니다.

   * > ```js
     > function V003:onSelect2Change(comp, info, e)
     > {
     >
     >     //지역선택 아이템을 선택했을 경우 토스트 알림
     >     if(!info)
     >     {
     >         AToast.show('지역을 선택하세요.');
     >         return;
     >     }
     >     
     >     //배열의 join 기능을 이용한 텍스트 결합
     >     this.lbl001.setText([
     >         this.select1.getSelectedItem().text,
     >         ' > ',
     >         this.select2.getSelectedItem().text
     >     ].join(''));
     >     
     >
     > };
     > ```
   * 마지막으로 onActiveDone  이벤트에 컴포넌트 초기값 설정을 아래 내용과 같이 수정합니다.  
     화면이 활성화 완료설정값을 초기화 하도록 합니다. 될때마다

   * > ```js
     > //화면 활성화가 완료될때마다
     > function V003:onActiveDone(isFirst)
     > {
     >
     >     super.onActiveDone(isFirst);
     >     
     >     //value가 0인 아이템을 기본 셀렉트 되게
     >     this.select1.selectItem(this.select1.indexOfValue('0'));    
     >     
     >     //선택되어서 변경된 이벤트 발생시키기
     >     this.select1.reportEvent('change');
     >     
     > };
     > ```

6. F5 키를 이용해서 프로젝트를 빌드하고 실행합니다.  
   ![](/assets/selectbox-ex-005.png)





