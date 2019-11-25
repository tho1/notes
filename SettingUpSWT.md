Setting up an application using JFaces and SWT libraries.

Premise: I had some eclipse SWT applications, and there are certain libraries required in order to make it work.

In windows environment, one needs to include the dll and several referenced libraries in order for the application to work. 

Here are the list.

All the dll and jar libraries should be placed in the project's home directories.

* swt-win32-4880.dll
* swt-gdip-win32-4880.dll
* swt-win.jar
* swt.jar
* jfxrt.jar
* org.eclipse.core.commands_3.9.100.v20180404-1234.jar
* org.eclipse.equinox.common_3.10.0.v20180412-1130.jar
* org.eclipse.jface.databinding_1.8.200.v20180403-0945.jar
* org.eclipse.jface.text_3.13.0.v20180527-1819.jar
* org.eclipse.jface_3.14.0.v20180423-0714.jar
* org.eclipse.osgi_3.13.0.v20180409-1500.jar
* org.eclipse.ui.workbench_3.111.0.v20180524-1156.jar
* org.eclipse.wst.command.env.core_1.0.300.v201802222200.jar

I am using the Eclipse Photon version 4.8.0, and the libraries can be found in eclipse/plugins directory.

TODO: Add a sample SWT application to include to showcase the change.
TODO: Add support for doing it in Mac and Linux system. 
