# BmpView
CLI 24-bit BMP Viewer for DOS and Win32
Copyright Mr.Madguy, 2023

**License:** Engine can be used for free for personal non-commercial purpose only. Any purpose, that involves explicit or implicit revenue, including indirect one (in case of budget or government organizations, educational purposes, etc.) - is allowed only after buying commercial license.

**License philosophy:** Programmers should be professionals, not just enthusiasts, who have to provide unrelated services in order to earn money. If one uses my work to earn money - then he should share part of his revenue with me. If you earn money via clogging nails, then why do you think hammer should be free for you? Buy it! I've put my effort into making tool for you to earn money. And it's like law of energy conservation. Every drop of sweat should pay off.

**Usage:** BmpView.exe BmpFile [Lum [Red [Green [Blue [VideoDriver [Width [Height [KeyboardDriver]]]]]]]]

  BmpFile - path to 24-bit BMP file
  
  Lum - number of luminosity shades in palette (0 is default)
  
  Red - number of red shades in palette (8 is default)
  
  Green - number of green shades in palette (8 is default)
  
  Blue - number of blue shades in palette (4 is default)
  
**Note!:** Total number of colors, i.e. Lum*Red*Green*Blue, must not exceed 256. All colors exceeding this limit will be truncated. Negative value disables dithering for this channel. 1 and 0 are special values. 0 means that this color is unused and brightness will be set to 0 in palette. 1 means the same, but bringhtness for this color will be set to maximum value in palette. -1 or any incorrect value forces program to use default value. 332 bits (i.e. 8*8*4=256 colors) is default palette.

  VideoDriver - path to video driver (Vga.drv is default for DOS and Windows.drv - for Windows).
  
  Width - demanded horizonal resolution (-1 or any incorrect value means default).
  
  Height - demanded vertical resolution (-1 or any incorrect value means default).
  
  KeyboardDriver - path to keyboard driver (Console.drv is default for DOS and Windows.drv - for Windows).
  
**Note!:** BmpView2.exe is linked as Windows GUI application, so Win32s is supported

**Controls:**

  Arrows - scroll
  
  Any other key - quit
  
**Features:**

  1) View 24-bit BMP file on 8-bit 256 colors display.
  2) Fast templated dithering.
  3) Rich palette control features.
  4) Complete abstraction from destination environment using OS-like API and driver model.
  5) Same program can run both under DOS and Windows (Win32s is supported).
  6) BitBlt with full clipping and scrolling support.
     
**Programming features:**
  1) Dynamic external declaration macro, which declares API externals only if they are really needed. Allows you to declare externals by simply including one large .inc file with all declarations inside without any risk of having all of this mess included into your exe's export table then.
Program does not support any error messages. If program just closes silently then one of the following cases occured:
  1) BmpFile not found.
  2) BmpFile has wrong format.
  3) VideoDriver not found.
  4) Your hardware is not supported by VideoDriver.
  5) Demanded resolution is not supported by your hardware.
  6) KeyboardDriver not found.
  7) Your hardware is not supported by KeyboardDriver.
  8) You are trying to use one of the drivers in wrong environment.
It is recommended to try default values first and then adjust options one-by-one until you'll find a problem.
**Files:**
  BmpView.exe - main program.
  HDpmi32.exe - HX DPMI32 host.
  DpmiLD32.exe - HX PE loader.
  DKrnl32.dll - HX Kernel32.dll emulation runtime.
  Graph32.dll - video API library.
  Keyb32.dll - keyboard API library.
  Vga.drv - VGA video driver. 320x200 is default resolution.
  VgaX.drv - VGA mode X driver. 320x240 is default resolution. Supports Width = 160, 180, 320, 360 and Height = 87, 100, 116, 120, 133, 160, 175, 200, 240, 350, 400, 480.
  Svga.drv - driver for VGA or SVGA with VBE 1.0 support or better. 640x480 is default resolution.
  SvgaLfb.drv - driver for SVGA with VBE 2.0 support or better. 640x480 is default resolution.
  Console.drv - keyboard driver for console environment.
  Windows.drv - video and keyboard wrapper driver for Windows environment. 640x480 is default resolution.
  Test.bat - test program with default drivers and 6*6*6=216 colors palette.
  TestLum.bat - test with default drivers and grayscale palette
  Test1bpp.bat - test with default drivers and monochrome palette (MDA)
  Test3bpp.bat - test with default drivers and 8 color palette
  test4bpp.bat - test with default drivers and 16 color palette (EGA)
  TestVga.bat - test Vga.drv driver.
  TestVgaX.bat - test VgaX.drv driver.
  TestSvga.bat - test Svga.drv driver.
  TestLfb.bat - test SvgaLfb.drv driver.
  TestWin.bat - test Windows.drv driver.
  ReadMe.txt - this file.
