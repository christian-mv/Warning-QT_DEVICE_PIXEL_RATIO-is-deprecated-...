# [SOLVED] ```Warning-QT_DEVICE_PIXEL_RATIO-is-deprecated ...```

In this tutorial I will show you how to fix the ```QT_DEVICE_PIXEL_RATIO``` warning when compiling Qt Apps.
 
## TUTORIAL ##

 This annoying warning can be fixed by just adding the follow line to your ```main()``` function:
```
 qputenv("QT_SCALE_FACTOR", QByteArray("1"));
```
 You should guarantee that ```<QByteArray>``` and ```<QtGlobal>``` headers have been included in your program. 

 It is worthwhile to mention that probably you won't need to explicitly include ```<QtGlobal>``` in your app since this header has been  implicitly included in  ```<QApplication>```. 

Now suppose that you've created a simple dialog using QCreator, your ```main()``` file should look something like this: 

```
#include "dialog.h"
#include <QApplication>
#include <QByteArray> //ADD THIS 

int main(int argc, char *argv[])
{
    qputenv("QT_SCALE_FACTOR", QByteArray("1")); //ADD THIS
    QApplication a(argc, argv);
    Dialog w;
    w.show();
    return a.exec();
}
```
