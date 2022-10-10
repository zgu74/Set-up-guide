Zeyu Gu

zeyugu@seas.upenn.edu

Tested on: Lenovo XiaoXinPro 16ACH 2021 Windows 11 21H2

Guide:

1.  I use MinGW instead of NMake.
2.  Download and install:
    1.  PuTTY
    2.  Arm GNU Toolchain (add path to environment variable)
    3.  CMake (add CMake to the system PATH for all users)
    4.  MinGW (.exe file; in the folder “bin”, copying the file “mingw32-make” and renaming it to “make”)
    5.  Visual Studio 2022 (Desktop development with C++)
    6.  Visual Studio Code
    7.  Python 3.0 (install launcher for all users; add Python 3.10 to PATH; disable the MAX_PATH length limit)
    8.  Git (use Visual Studio Code as Git’s default editor; allow Git to be used from 3rd-party software; checkout as is, commit as-is; use Window’s default console window; enable experimental support for pseudo consoles)
3.  Create the folder “Pico” in C:\\Users\\gzyhk, and the folder “Downloads” in the folder “Pico”.
4.  In System Properties \> Environment Variables, edit Path (user variables for admin) and Path (system variables). Then add path:
    1.  C:\\MinGW\\bin
    2.  C:\\Program Files (x86)\\Arm GNU Toolchain arm-none-eabi\\12.2 mpacbti-bet1\\bin
    3.  C:\\Program Files\\CMake\\bin
5.  In the cmd, getting sdk and examples:
    1.  C:\\Users\\gzyhk\\Pico\\Downloads\> git clone -b master <https://github.com/raspberrypi/pico-sdk.git>
    2.  C:\\Users\\gzyhk\\Pico\\Downloads\> cd pico-sdk
    3.  C:\\Users\\gzyhk\\Pico\\Downloads\\pico-sdk\> git submodule update --init
    4.  C:\\Users\\gzyhk\\gzyhk\\Pico\\Downloads\\pico-sdk\> cd ..
    5.  C:\\Users\\gzyhk\\Pico\\Downloads\> git clone -b master <https://github.com/raspberrypi/pico-examples.git>
6.  Building “Hello World” from the cmd:
    1.  Open the Developer Command Prompt from VS Studio 2022. Then set the path: C:\\Users\\gzyhk\\Pico\\Downloads\> setx PICO_SDK_PATH "..\\..\\pico-sdk". Restart the command prompt window.
    2.  Build the “Hello World” example:
        1.  C:\\Users\\gzyhk\\Pico\\Downloads\> cd pico-examples
        2.  C:\\Users\\gzyhk\\Pico\\Downloads\\pico-examples\> mkdir build
        3.  C:\\Users\\gzyhk\\Pico\\Downloads\\pico-examples\> cd build
        4.  C:\\Users\\gzyhk\\Pico\\Downloads\\pico-examples\\build\> cmake -G "MinGW Makefiles" ..

            ![屏幕截图 2022-10-09 194000](https://user-images.githubusercontent.com/113784775/194967919-f02791f8-90cc-4b50-a2ba-0dd846e1c2e3.png)


        5.  C:\\Users\\gzyhk\\Pico\\Downloads\\pico-examples\\build\> MinGW
    3.  The file “hello_usb.uf2” is produced in the directory C:\\Users\\gzyhk\\Pico\\Downloads\\pico-examples\\build\\hello_world\\usb.
7.  Building “Hello World” from VS Code:
    1.  Open VS Code and install extensions: C/C++ and CMake Tools.
    2.  In CMake Tools’ extension settings \> Cmake: Configure Environment, add item ”Item: PICO_SDK_PATH; Value: C:\\Users\\gzyhk\\Pico\\Downloads\\pico-sdk”.
    3.  In CMake Tools’ extension settings \> Cmake: Generator, add “MinGW Makefiles”.
    4.  In CMake Tools’ extension settings \> Cmake: Mingw Search Dirs, add item “C:\\MinGW”.
    5.  In VS Code, open the folder “pico-examples”. Press Ctrl+Shift+P and select “CMake: Select a Kit”. Then select “GCC 12.2.0 arm-none-eabi”.
    6.  Open CMake in the left side menu. Click the top button “Configure All Projects”. Building all projects takes too long time. I can select the folder “hello_world” \> “usb” \> “hello_usb”. Click the button “Build” near the folder.

        
        ![屏幕截图 2022-10-09 194915](https://user-images.githubusercontent.com/113784775/194968015-8d4b02e4-a669-4ee0-955f-21c1059aa487.png)

    7.  The file “hello_usb.uf2” is produced in the directory C:\\Users\\gzyhk\\Pico\\Downloads\\pico-examples\\build\\hello_world\\usb.
8.  Connect RP 2040. hold down the “BOOT” button on the board while pressing “RESET” to re-enter programming mode. Drag and drop the file “hello_usb.uf2” into the drive.
9.  Open Device Manager. Click on Ports to check the number of COM\#.
10. Open PuTTY:
    1.  Connection type: Serial
    2.  Serial line: COM5
    3.  Speed: 115200
    4.  Save the session as “COM5”
11. Click open. Now “Hello, world!” is appearing on the window.

    ![屏幕截图 2022-10-09 194431](https://user-images.githubusercontent.com/113784775/194968072-45e80831-84e2-4755-a9df-1c438a477106.png)
