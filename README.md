# Warning-QT_DEVICE_PIXEL_RATIO-is-deprecated.-Instead-use-QT_AUTO_SCREEN_SCALE_FACTOR-to-enable-
# [SOLVED] in this tutorial I will show you how to fix the QT_DEVICE_PIXEL_RATIO warning when compiling Qt Apps.

# ------------------------- TUTORIAL ---------------------------

# This annoying problem can be fixed by just adding the fallow line in your main() function:

# qputenv("QT_SCALE_FACTOR", QByteArray("1"));

# You shoul guarantee that <QByteArray> and <QtGlobal> headers have been included in your program. 

# It is worthwhile to mention that probably you won't need to explicitly
# include <QtGlobal> in your app since this header has been 
# implicitly included in  <QApplication>. 
# Below an example:

# Suppose that you've created a simple dialog using QCreator, your main() file should look something like this: 

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

