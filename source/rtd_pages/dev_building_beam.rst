.. _dev_building_beam:

Building Ontology
=============


The following document decribes how to build Ontology binaries from sources located at: https://github.com/ontio/ontology


Windows
-------


1. Install Visual Studio >= 2017 with CMake support.

2. Download and install Boost prebuilt binaries https://sourceforge.net/projects/boost/files/
boost-binaries/1.68.0/boost_1_68_0-msvc-14.1-64.exe, also add BOOST_ROOT to the Environment Variables.

3. Download and install OpenSSL prebuilt binaries https://slproweb.com/products/Win32OpenSSL.html (Win64 OpenSSL v1.1.0h for example) and add OPENSSL_ROOT_DIR to the Environment Variables.

4. Download and install QT 5.11 https://download.qt.io/official_releases/qt/5.11/5.11.0/qt-opensource-windows-x86-5.11.0.exe.mirrorlist and add QT5_ROOT_DIR to the Environment Variables (usually it looks like .../5.11.0/msvc2017_64), also add QML_IMPORT_PATH (it should look like %QT5_ROOT_DIR%\qml). BTW disabling system antivirus on Windows makes QT installing process much faster.

5. Add .../qt511/5.11.1/msvc2017_64/bin and .../boost_1_68_0/lib64-msvc-14.1 to the System Path.

6. Open project folder in Visual Studio, select your target (Release-x64 for example, if you downloaded 64bit Boost and OpenSSL) and select CMake -> Build All.

7. Go to CMake -> Cache -> Open Cache Folder -> beam (you'll find beam.exe in the beam subfolder, beam-wallet.exe in ui subfolder).


Linux 
-------------------------------

1. Create work directory and Get from source code

::

  mkdir -p $GOPATH/src/github.com/ontio
  
  cd $GOPATH/src/github.com/ontio
  
  git clone https://github.com/ontio/ontology.git
  
  or
  
  go get github.com/ontio/ontology


2. Fetch the dependent third party packages with glide.

::

  $ cd $GOPATH/src/github.com/ontio/ontology
  $ glide install

3. Go to the project folder and call.

::

  make all

4. You'll find two executable programs: "ontology" binary and "tools/sigsvr" in your project folder.

Mac
---

1. Install Brew Package Manager.

2. Install necessary packages using `brew install openssl boost cmake qt5` command.

3. Add `export OPENSSL_ROOT_DIR="/usr/local/opt/openssl"` and `export PATH=/usr/local/opt/qt/bin:$PATH` to the *Environment Variables*.

4. Go to Beam project folder and call `cmake -DCMAKE_BUILD_TYPE=Release . && make -j4`.

5. You'll find *Beam* binary in `bin` folder, `beam-wallet` in `ui` subfolder.

.. note:: If you don't want to build UI don't install QT5 and add `-DBEAM_NO_QT_UI_WALLET=On` command line parameter when you are calling `cmake`.




