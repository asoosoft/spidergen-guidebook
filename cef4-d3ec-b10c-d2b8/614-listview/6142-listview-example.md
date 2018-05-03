# 6.14.2. Listview Example

---

> Download1 : [http://manual.spidergen.org/example/SG005.zip](http://manual.spidergen.org/example/SG005.zip)
>
> Download2 : [http://manual.spidergen.org/example/ListViewSample.zip](http://manual.spidergen.org/example/ListViewSample.zip)

1. 새 프로젝트 SG005를 생성합니다.
2. Source  폴더에 MainView를 생성합니다.
3. SG005App.cls 파일을 오픈하고 다음과 같이 내용을 수정합니다. 네비게이터를 생성하고 MainView를 등록합니다.
   * > ```js
     > function SG005App:onReady()
     > {
     >     super.onReady();
     >
     >     var navigator = new ANavigator();
     >     navigator.registerPage('Source/MainView.lay', 'MainView');
     >     navigator.goPage('MainView');
     >
     > };
     > ```
4. MainView.lay 파일을 오픈하고 아래 내용을 참고해서 컴포넌트를 배치합니다.

| component | id | position | size | text | etc |
| :--- | :--- | :--- | :--- | :--- | :--- |
| ALabel | lbl001 | left:10px, top:20px | w-stretch:10px, height:20px | 선택내용 | line height:20px |
| AListView | listView | left:10px, top:60px | w-stretch:10px, height:300px |  | border : 1px |
| AButton | btnAdd | right:50px, top:380px | width:100px, height:30px | Add | right margin:10px |
| AButton | btnDel | left:50%, top:380px | width:100px, height:30px | Delete | left margine:10px |

![](/assets/listview-ex-002.png)

1. Source 폴더 안에 Items 폴더를 생성합니다.
2. 생성한 Items 폴더 내에 ItemView 이름의 뷰를 추가하고 아래 내용을 참고해서 컴포넌트를 배치합니다.

| component | id | position | size | text | etc |
| :--- | :--- | :--- | :--- | :--- | :--- |
| ItemView |  |  | width:100%, height:50px |  | background : transparent |
| AImage | img001 | left:5px, top:5px | width:40px, height:40px |  |  |
| ALabel | lbl001 | left:50px, top:5px | w-stretch:90px, height:40px |  | background:transparent |
| AButton | btn001 | right:5px, top5px | width:80px, height:40px | Delete | - |

![](/assets/listview-ex-003.png)

1. 먼저 리스트뷰에 추가할 데이터를 만들고 아이템뷰를 리스트합니다.
   * MainView.cls 파일을 오픈하고 다음과 같이 클래스에 멤버변수를 만들고 데이터를 설정합니다.
   * > ```js
     > class MainView()
     > {
     >     super();
     >
     >     //리스트 데이터 배열 입니다.    
     >     this.listData = [
     >         {
     >             img : 'Assets/img/door.png', 
     >             title : 'List Content Title 1'
     >         },
     >         {    img : 'Assets/img/page_white_add.png', 
     >             title : 'List Content Title 2'
     >         },
     >         {    img : 'Assets/img/page_white_copy.png', 
     >             title : 'List Content Title 3'
     >         },
     >         {    img : 'Assets/img/page_white_delete.png', 
     >             title : 'List Content Title 4'
     >         },
     >         {    img : 'Assets/img/page_white_edit.png', 
     >             title : 'List Content Title 5'
     >         },
     >         {    
     >             img : 'Assets/img/page_white_paste.png', 
     >             title : 'List Content Title 6'
     >         }
     >     ];
     >
     > }
     > extends AView;
     > ```
2. 위 샘플 다운로드 링크에서 받은 샘플소스내 img 폴더를 복사해서 현재 프로젝트에 붙어넣습니다.
3. 프로젝트 트리의 Assets 폴더 위에서 컨텍스트 메뉴를 오픈합니다. 
   * Add existing files in directory... 메뉴를 선택하고 현재 프로젝트 내에 복사한 img 폴더를 로드합니다.
   * ![](/assets/listview-ex-006.png)
4. onInitDone\(\) 이벤트에서 listView의 발생 이벤트를 MainView에서 전달 받을 수 있게 Delegator를 설정합니다.

   * listView에 Delegator가 설정되지 않으면 아이템이 추가될때 추가되는 아이템에 setData\(data\) 함수가 호출 됩니다. 따라서 아이템에 setData\(data\) 메소드가 구현되어 있어야 합니다.
   * listView에 Delegator가 설정되면 아이템이 추가 될때 Delegator 객체에 bindData\(item, data, alistview\) 함수가 호출 됩니다. 따라서 Delegator 객체에 bindData\(item, data, alistview\) 메소드가 구현되어 있어야 합니다.

   * > ```js
     > function MainView:onInitDone()
     > {    
     >     // 리스트뷰에 델리게이터를 연결한다.
     >     this.listView.setDelegator(this);
     >
     > };
     > ```

5. onInitDone\(\) 이벤트에서 listView에 Delegator가 설정 되어었으므로 MainView에 bindData 메소드를 다음과 같이 추가합니다.

   * > ```js
     > function MainView:bindData(item, data, alistview){
     >
     >     //item : 리스트되는 현재 n번째 아이템
     >     //data : 현재 item에 바인딩되는 n번째 데이터
     >     //alistview : item을 리스트로 하는 리스트뷰 객체
     >     
     >     //현재 아이템의 뷰에 setData 함수가 있을 경우 실행    
     >     if(item.view.setData) item.view.setData(data);
     >     
     > };
     > ```

6. MainView 활성화가 완료 될 때 발생하는 onActiveDone 이벤트에서 리스트뷰에 데이터를 바인딩 합니다.

   * > ```js
     > function MainView:onActiveDone(isFirst)
     > {    
     >     super.onActiveDone(isFirst);
     >     
     >     // 리스트뷰에 데이터만큼의 아이템뷰를 추가한다.    
     >     this.listView.addItem('Source/Items/ItemView.lay', this.listData);
     >     
     > };
     > ```

7. F5 키를 이용해서 프로젝트를 빌드후 실행해 봅니다.

   * ![](/assets/listview-ex-007.png)

8. 이번에는 리스트 되는 ItemView를 수정해서 위에 실행화면에서 보이지 않는 이미지와 레이블 내용을 추가하겠습니다.

   * ItemView.cls 파일을 오픈하고 클래스에 설정되는 데이터를 저장하기 위한 멤버 변수를 추가합니다.  
   * > ```js
     > class ItemView()
     > {
     >     super();
     >
     >     this.data = null;
     >
     > }
     > extends AView;
     > ```

9. 다음은 데이터가 바인딩 될때 호출되는 setData 메소드를 추가하고 내용을 다음과 같이 수정합니다.

   * ItemView의 setData 메소드 호출은 MainView.cls에 오버라이드된 bindData 메소드 내에서 호출합니다. 참고하세요.  
   * > ```js
     > function ItemView:setData(data)
     > {    
     >     this.data = data;
     >     
     >     this.img001.setImage(this.data.img);
     >     this.lbl001.setText(this.data.title);
     > };
     > ```

10. 프로젝트를 빌드하고 실행합니다. 이미지와 레이블에 데이터 내용이 설정된걸 확인합니다.

    * ![](/assets/listview-ex-009.png)

11. MainView에 Add 버튼에 Click 이벤트를 추가합니다. 설정한 이벤트 함수는 아래와 같이 수정합니다.

    * > ```js
      > function MainView:onBtnAddClick(comp, info, e)
      > {
      >
      >     //리스트 데이터는 배열로 들어가야 함.
      >     //데이터의 첫번째 데이터를 배열에 넣어서 추가함.
      >     this.listView.addItem('Source/Items/ItemView.lay', [this.listData[0]]);
      >     
      >     //리스트뷰 스크롤을 맨 아래로 이동
      >     this.listView.scrollToBottom();
      >
      > };
      > ```

12. 프로젝트를 빌드하고 실행한후 Add 버튼을 클릭해 봅니다. 리스트에 아이템이 추가되면서 스크롤이 아래로 내려오는걸 확인 할수있습니다.

13. 이번에는 listView에 아이템이 선택 되었을때 스타일을 적용해 보겠습니다.

    * 프로젝트 트리 Template 폴더에 컨텍스트 메뉴를 오픈합니다. 메뉴에서 New Template 를 클릭합니다.  
    * 그러면 style.tpl, style.tlay, style.stl 파일이 생성됩니다.  
    * style.tpl 파일을 오픈합니다. 그리고 스타일 트리에서 컨텍스트 메뉴를 오픈합니다.  
    * 오픈된 컨텍스트 메뉴중에 맨 마지막 Add Item을 클릭합니다.

      * ![](/assets/listview-ex-010.png)
      * 추가된 스타일 아이템의 Class Pane에서 ID를 selected\_item 이라 설정합니다.
      * Appearance Pane에 background &gt; Image 클릭 오픈된 그라이데이션 다이얼로그에서   밝은 부분rgb\(239, 239, 239\), 어두운 부분 rgb\(128, 128, 128\) 설정합니다.
      * 스타일 아이템 트리에서 컨텍스트 메뉴를 오픈하고 Make All Style을 실행합니다. 아이템을 선택하고 스타일이 적용되는걸 확인합니다.  
        ![](/assets/listview-ex-011.png)

      * 

    * MainView에 listView Appearance &gt; Item &gt; Selected Style 속성을  style\_selcted\_item 으로 설정합니다.

    * F5 키로 프로젝트를 빌드하고 실행합니다.

    * 실행된 화면에서 리스트의 아이템을 선택하고 스타일이 적용되는걸 확인합니다.

    * ![](/assets/listview-ex-012import.png)

14. 이번에는 리스트 아이템을 선택하고 삭제하는 사용자 함수를 다음과 같이 추가합니다.

    * 함수명은 doDeleteItem 이라 하고 파라미터는 item으로 합니다.  
    * > ```js
      >  //사용자 함수
      > function MainView:doDeleteItem(item)
      > {    
      >     //리스트뷰에 아이템 삭제
      >     this.listView.removeItem(item);
      >     
      > };
      > ```
    * ItemView.lay에서 아이템에 있는  Delete 버튼에 Click 이벤트를 설정합니다. 설정 함수 내용은 다음과 같이 수정합니다.  
    * > ```js
      > function ItemView:onBnt001Click(comp, info, e)
      > {
      >     //아이템의 상위객체 리스트뷰에 정의 함수 호출
      >     this.owner.removeItem(this.item);
      >
      > };
      > ```
    * 프로젝트를 빌드하고 실행한 후 리스트 아이템에 있는 Delete 버튼을 클릭합니다. 클릭한 아이템이 삭제 되는것을 확인합니다.

15. 마지막으로 MainView의 Delete 버튼에 Click 이벤트를 설정하고 모든 아이템을 삭제하는 기능을 추가합니다.

    * Delete 버튼에 Click 이벤트를 설정하고 설정 함수는 다음과 같이 수정합니다.   
    * 모든 아이템을 삭제하기 전에 AMesageBox를 이용해서 삭제 확인을 승인받고 삭제하는 기능을 추가합니다.  
    * > ```js
      > function MainView:onBtnDelClick(comp, info, e)
      > {
      >     var thisObj = this;
      >     
      >     AfcMessageBox('확인', '정말로 아이템을 모두 삭제하시겠습니까?', AMessageBox.YES_NO, function(result){
      >         if(result == 0)
      >         {
      >             thisObj.listView.removeAllItems();            
      >             return;
      >         }
      >             
      >         //NO
      >         if(result == 1)
      >         {
      >             return;
      >         }    
      >     });
      >     
      > };
      > ```

16. 프로젝트를 빌드하고 최종 기능을 모두 확인합니다.

    * ![](/assets/listview-ex-012.png)



