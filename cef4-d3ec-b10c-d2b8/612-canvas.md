# 6.12. View

---

뷰 컴포넌트 입니다.

![](/assets/view-comp-00.png)



```js

/**
Constructor
Do not call Function in Constructor.
*/
class SG009App()
{
	super();

	//TODO:edit here

}
extends AApplication;


function SG009App:onReady()
{
	super.onReady();

	var navigator = new ANavigator();
	navigator.registerPage('Source/MainView.lay', 'MainView');
	navigator.goPage('MainView');

};

function SG009App:unitTest(unitUrl)
{
	//TODO:edit here

	super.unitTest(unitUrl);
};

```



