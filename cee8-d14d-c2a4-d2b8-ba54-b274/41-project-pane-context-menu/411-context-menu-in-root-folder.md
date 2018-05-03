# 4.1.1. Context Menu on Root folder

---

![](/assets/context-rootnode-01.png)

프로젝트 트리 루트 폴더\(Root folder\)의 컨텍스트 메뉴 입니다.

* **Add existing files...** :  프로젝트 폴더내 물리적으로 존재하는 파일을 프로젝트에 로드하고 오픈하기 위한 기능입니다.
* **Add existing files in directory...** :  물리적으로 존재하는 폴더내의 모든 파일을 프로젝트에 로드하고 오픈하는 기능입니다.
* **Add new** : 새로운 파일을 생성하는 기능입니다.

  * **Folder **: 새 폴더를 생성하는 기능 입니다.

  * **View** : 새 화면 파일\(.cls, .lay\)을 생성하는 기능입니다.

  * **Layout **: 새 레이아웃 파일\(.lay\)을 생성하는 기능입니다.

  * **Class **:  새 클래스 파일\(.cls\)을 생성하는 기능입니다.  
    ![](/assets/cotext-rootnode-addnew.png)

* **Save Project** : 현재의 프로젝트를 저장하는 기능 입니다.  File &gt; Save Project 메뉴와 동일합니다.

* **Close Project** : 현재의 프로젝트를 닫는 기능 입니다. File &gt; Close Project 메뉴와 동일합니다.

* **Reload Project** : 현재의 프로젝트를 새로 로드하는 기능입니다. File &gt; Reload Project 메뉴와 동일합니다.

* **Open folder** : 현재 프로젝트 위치의 폴더를 오픈 해주는 기능입니다.

* **Properties...** : 프로젝트 및 스파이더젠의 옵션을 설정할 수 있는 다이얼로그를 오픈하는 기능입니다.

* **Web Server Deployment** :  프로젝트의 결과물을 배포하기 위한 다이얼로그를 오픈하는 기능입니다.

  * **Upload-Url** : 배포할 Url을 선택 합니다. 해당 Url은 Properties 다이얼로그에서 설정 할 수 있습니다. 
    ![](/assets/context-rootnode-deployment.png)  

* **Source Control **:  
  ![](/assets/context-sourcecontrol.png)  
  현재 프로젝트가 형상관리 모드일 경우 노출 되며 형상관리 주요 기능을 실행 할 수 있습니다.

* * **Refresh** :  현재 형상관리 상태를 새로고침 하는 기능입니다.
  * **Update **:  현재 프로젝트에서 Update가 필요한 모든 파일을 일괄 Update 받게 해주는 기능입니다. update를 실행하면 프로젝트를 다시 로그할지 문의하는 다이얼로그가 실행됩니다.  
    ![](/assets/dialog-svn-update.png)

  * **Commit **:  형상관리 되고 있는 현재 프로젝트에서 Commit이 필요한 모든 파일을 일괄 Commit 하게 해주는 기능입니다. Commit을 실행하면 코멘트를 등록 할 수 있는 다이얼로그가 실행됩니다.  
    ![](/assets/dialog-svn-commit.png)

  * **Show log** :  형상관리 로그를 확인 할 수 있는 다이얼로를 실행하는 기능입니다.  
    ![](/assets/pop-svn-showlog.png)
* **Project Save Server** : 형상관리 충돌방지모드일 경우 노출되는 메뉴 입니다. 실행하면 프로젝트파일\(.prj\)에 대한 권한을 얻고 성공하게 되면 수정된 프로젝트파일\(.prj\)을 저장소에 저장합니다.  
  ![](/assets/dialog-svn-saveserver.png)



