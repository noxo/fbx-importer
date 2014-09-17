FBX Importer
==============

An FBX importer and viewer for JavaFX 8.

## Build Instructions

The FBX importer makes use of Autodesk's FBX SDK. There are both C++ and Java components to build.

### Windows

First ensure the following are installed

1. JDK 1.8 b132+
2. Cygwin or MinGW
3. Visual Studio 10+
4. Autodesk FBX SDK (www.autodesk.com/developfbx)
5. Windows SDK
6. Gradle

Set the following environment variables

1. JAVA_HOME    (e.g. C:/Program Files/Java/jdk_1.8.0/)
2. VSINSTALLDIR (e.g. C:/Program Files (x86)/Microsoft Visual Studio 11.0/)
3. FBX_SDK_HOME (e.g. C:/Program Files/Autodesk/FBX/FBX SDK/2014.1/)
4. WIN_SDK_HOME (e.g. C:/Program Files/Microsoft SDKs/Windows/v7.1/)

Open a terminal and run 'gradle' from the project root directory.

### Mac

First ensure the following are installed

1. JDK 1.8 b132+
2. XCode
3. Autodesk FBX SDK (www.autodesk.com/developfbx)

Manual building steps

1. Create new C++ library (name="jbxlib", type="dynamic")
  * Change "Executable extension" to jnilib
  * Add to "Header Search Paths"
    * "/Applications/Autodesk/FBX SDK/"2015.1/include
    * /Library/Java/JavaVirtualMachines/jdk1.8.0_20.jdk/Contents/Home/include
2. Add JFbxLib.cpp and JFbxLib.h to project
3. Add Autodesk SDK library to project
  * Build phases -> Link with library = libfbxsdk.a (from Autodesk SDK)
4. Create JNI header file (de_tesis_dynaware_javafx_graphics_importers_fbx_JFbxLib.h)
  * javah -cp . de.tesis.dynaware.javafx.graphics.importers.fbx.JFbxLib
  * Add file to XCode project 
5. Build project and copy produced libjbxlib.jnilib file to Java project
6. Copy libfbxsdk.dylib from Autodesk SDK to /usr/lib

## Linux

Not yet supported. Contributions are welcome.

## Sample FBX files

The sample file 'Zombie.fbx' is provided courtesy of Autodesk.

More samples are included with Autodesk's free FBX Converter (www.autodesk.com/products/fbx/overview).
