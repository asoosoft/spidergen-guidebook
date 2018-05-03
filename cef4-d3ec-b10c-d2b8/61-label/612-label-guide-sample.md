# 6.1.2. ALabel Example

---

1. 새 프로젝트를 생성합니다.  
   1.1. File &gt; New Project 클릭합니다. 아래와 같은 프로젝트 생성 다이얼로그에서 Project Name은 SG001라 입력하고 Location은 프로젝트를 생성할 위치를 선택합니다. \(샘플에서는 C:\study 폴더를 선택했습니다.\)

   CreateFolder를 체크하면 Location에 선택하신 폴더 내에 입력한 프로젝트명 ST001 폴더가 생성되고 그 하위에 프로젝트가 생성됩니다.  
   ![](/assets/lable-ex001.png)

2. 프로젝트가 생성되면 메인뷰를 추가합니다.

   * 프로젝트 탐색기에서 Source 폴더 위에서 마우스 오른쪽 버튼 클릭합니다.  
   * 오픈된 메뉴에서 Add new &gt; Folder를 선택합니다.  
   * 오픈된 다이얼로그\(New Folder\)에서 폴더명을 Views로 입력합니다.  
     ![](/assets/leble-ex002.png)

3. 생성된 Views 폴더 위에서 마우스 오른쪽 버튼을 클릭합니다.

   * 오픈된 메뉴에서 Add New &gt; View를 선택합니다.  
   * 오픈된 다이얼로그\(New View\)에서 Name을 MainView라 입력하고 OK를 클릭합니다.  
     ![](/assets/label-ex003.png)

     다음과 같은 상태임을 확인합니다.![](/assets/lable-ex006.png)

4. 어플리케이션 파일\(SG001App.cls\)에 네비게이터를 생성합니다.

   * 프로젝트 트리 뷰에서 Source &gt; SG001App.cls 파일을 클릭해 파일을 오픈합니다.  
   * 파일 내용 중 onReady\(\) 함수의 내용을 아래와 같이 변경합니다.

   * > ```js
     > function SG001App:onReady()
     > {
     >     super.onReady();
     >     
     >     //네비게이터 생성
     >     var navigator = new ANavigator();
     >
     >     //네비게이터에 MainView 등록
     >     navigator.registerPage('Source/Views/MainView.lay', 'MainView');
     >
     >     //MainView로 이동
     >     navigator.goPage('MainView');
     >     
     >     //싱글뷰로 생성하는 방식.
     >
     >     //or
     >     //this.setMainContainer(new APage('main'));
     >     //this.mainContainer.open('Source/MainView.lay');
     >
     > };
     > ```

5. 메인뷰 추가 및 네비게이터 등록이 완료되면 메인뷰의 레이아웃에 라벨 컴포넌트를 추가합니다.

   * 프로젝트 트리뷰에서 Source &gt; Views &gt;MainView.lay 파일을 클릭합니다.  
   * MainView의 레이아웃 파일이 오픈되면 컴포넌트 리스트에서 Label 컴포넌트를 선택하고 드래그하여 아래와 같이 레이아웃에 배치합니다.  
   * Class Pane에서 ID를 lbl001로 입력합니다.![](/assets/lable-ex007.png)

   * Placement Pane에서 Position을 Left : 50px, Top : 50px으로  
     Size를 Width : 100px, height : 20px 으로 설정합니다.  
     ![](/assets/lable-ex008.png)

   * Appearance Pane 에서 Data 항목을 다음과 같이 설정 합니다.

     * Text : 라벨테스트  
     * Line Height : 20px \(세로 중간에 텍스트가 위치하게 합니다.\)  
       ![](/assets/lable-ex009.png)  

   * 레이아웃에 레이블의 Display를 확인합니다.  
     ![](/assets/lable-ex010.png)

6. 이번에는 소스 코딩을 이용하여 라벨에 텍스트를 설정합니다. 먼저 MainView.cls 파일을 오픈합니다.  
   상단의 파일탭에서 MainView.lay 탭을 더블 클릭하거나 우측의 프로젝트 트리에서 MainView.cls 파일을 더블 클릭합니다.

   * 모든 화면뷰는 **onInitDone\(\)** 함수가 존재하며 이 함수는 화면이 생성될 때 딱 한번 실행됩니다.   
     이** onInitDone\(\)** 함수에서 레이블의 텍스트 내용을 아래와 같이 코드를 입력합니다.
   * > ```js
     > function MainView:onInitDone()
     > {
     >     //라벨 컴포넌트에 ID가 부여되었으면 
     >     //this.컴포넌트아이디 형태로 바로 접근이 가능함.    
     >     this.lbl001.setText('라벨 초기화!!');    
     >
     > };
     > ```

7. F5를 누르거나 Build &gt; Run Project 를 클릭하여 프로젝트를 Run 합니다.  
   레이블의 텍스트가 바뀌어서 출력되는것을 확인 할 수 있습니다.  
   ![](/assets/lable-ex-011.png)

8. Download : [http://manual.spidergen.org/example/SG001.zip](http://manual.spidergen.org/example/SG001.zip)



