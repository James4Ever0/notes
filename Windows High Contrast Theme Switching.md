---
title: Windows High Contrast Theme Switching
created: '2024-02-26T06:12:30.285Z'
modified: '2024-02-27T00:36:10.788Z'
---

# Windows High Contrast Theme Switching

Download [ThemeSwitcher](https://winaero.com/downloads/WinaeroThemeSwitcher.zip) after Windows 11 for switching themes.

Write the following content into `hctweak1.theme`:

```
; Copyright � Microsoft Corp.

[Theme]
; High Contrast Black - IDS_THEME_DISPLAYNAME_HCBLACK
DisplayName=@%SystemRoot%\System32\themeui.dll,-2103
SetLogonBackground=0

; Computer - SHIDI_SERVER
[CLSID\{20D04FE0-3AEA-1069-A2D8-08002B30309D}\DefaultIcon]
DefaultValue=%SystemRoot%\System32\imageres.dll,-109

; UsersFiles - SHIDI_USERFILES
[CLSID\{59031A47-3F72-44A7-89C5-5595FE6B30EE}\DefaultIcon]
DefaultValue=%SystemRoot%\System32\imageres.dll,-123

; Network - SHIDI_MYNETWORK
[CLSID\{F02C1A0D-BE21-4350-88B0-7367FC96EF3C}\DefaultIcon]
DefaultValue=%SystemRoot%\System32\imageres.dll,-25

; Recycle Bin - SHIDI_RECYCLERFULL SHIDI_RECYCLER
[CLSID\{645FF040-5081-101B-9F08-00AA002F954E}\DefaultIcon]
Full=%SystemRoot%\System32\imageres.dll,-54
Empty=%SystemRoot%\System32\imageres.dll,-55

[Control Panel\Colors]
ActiveTitle=0 0 0
Background=0 0 0
ButtonFace=0 0 0
ButtonText=255 255 255
GrayText=166 166 166
Hilight=142 227 240
HilightText=38 59 80
HotTrackingColor=117 233 252
InactiveTitle=0 0 0
InactiveTitleText=128 128 128
TitleText=255 255 255
Window=0 0 0
WindowText=255 255 255
Scrollbar=0 0 0
Menu=0 0 0
WindowFrame=255 255 255
MenuText=255 255 255
ActiveBorder=255 255 0
InactiveBorder=0 128 0
AppWorkspace=0 0 0
ButtonShadow=0 0 0
ButtonHilight=192 192 192
ButtonDkShadow=255 255 255
ButtonLight=255 255 255
InfoText=255 255 255
InfoWindow=0 0 0
ButtonAlternateFace=192 192 192
GradientActiveTitle=128 0 128
GradientInactiveTitle=0 128 0
MenuHilight=128 0 128
MenuBar=0 0 0

[Control Panel\Cursors]
Arrow=%SystemRoot%\cursors\aero_arrow.cur
Help=%SystemRoot%\cursors\aero_helpsel.cur
AppStarting=%SystemRoot%\cursors\aero_working.ani
Wait=%SystemRoot%\cursors\aero_busy.ani
NWPen=%SystemRoot%\cursors\aero_pen.cur
No=%SystemRoot%\cursors\aero_unavail.cur
SizeNS=%SystemRoot%\cursors\aero_ns.cur
SizeWE=%SystemRoot%\cursors\aero_ew.cur
Crosshair=
IBeam=
SizeNWSE=%SystemRoot%\cursors\aero_nwse.cur
SizeNESW=%SystemRoot%\cursors\aero_nesw.cur
SizeAll=%SystemRoot%\cursors\aero_move.cur
UpArrow=%SystemRoot%\cursors\aero_up.cur
DefaultValue=Windows Default
DefaultValue.MUI=@main.cpl,-1020
Hand=%SystemRoot%\cursors\aero_link.cur
Link=

[Control Panel\Desktop]
Wallpaper=
TileWallpaper=0
WallpaperStyle=10
Pattern=

[VisualStyles]
Path=%SystemRoot%\resources\themes\Aero\AeroLite.msstyles
ColorStyle=NormalColor
Size=NormalSize
HighContrast=3

[boot]
SCRNSAVE.EXE=

[MasterThemeSelector]
MTSM=RJSPBS

[Sounds]
; IDS_SCHEME_DEFAULT
SchemeName=@%SystemRoot%\System32\mmres.dll,-800

```

Use like `ThemeSwitcher.exe <absolute_path_to_theme_file>`

---

Activate Windows using [Microsoft-Activation-Scripts](https://github.com/massgravel/Microsoft-Activation-Scripts)
