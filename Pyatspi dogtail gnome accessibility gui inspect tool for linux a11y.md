---
tags: [accessibility, dogtail, GUI automation, GUI inspection, inspection, linux, pyatspi, RPA]
title: Pyatspi dogtail gnome accessibility gui inspect tool for linux a11y
created: '2022-07-15T05:07:25.612Z'
modified: '2022-08-18T16:18:38.085Z'
---

# Pyatspi dogtail gnome accessibility gui inspect tool for linux a11y

https://github.com/autopilot-rs/autopilot-rs

https://github.com/autopilot-rs/autopy

does appium have linux accessibility implementation?

windows a11y:
https://github.com/blackrosezy/gui-inspect-tool
pywinauto

bookmark_history_search sucks. it does not include webpage summaries, only title, which makes searching the history very hard. the solution is to use readbility.js to visit and summarize these pages, and update these documents in meilisearch.

a11y is the general term for accessibility, for web browsers like firefox. however, there's implementation for gnome internally.

linux a11y:
https://github.com/shubhamvasaikar/Auto-GUI-Testing
gnome accessibility toolkit(atk)

https://gitlab.gnome.org/GNOME/pyatspi2
https://gitlab.com/dogtail/dogtail
https://www.freedesktop.org/wiki/Accessibility/PyAtSpi2Example/

accessibility implementation in different toolkits:
https://github.com/GNOME/at-spi2-core/blob/e83d5558d2fbded5b345b0af254f26865e148e49/devel-docs/toolkits.md

Toolkits that use the DBus APIs directly
GTK4
Sources: gtk4/gtk/a11y

Qt5
Sources: qtbase/src/gui/accessible/linux

WebKit
Sources: WebKit/Source/WebCore/accessibility/atspi

Toolkits that use ATK
GTK3
Sources: gtk3/gtk/a11y

gnome-shell / St / via clutter's cally
Sources: mutter/clutter/clutter/cally

Mozilla Firefox
Sources: gecko-dev/accessible/atk

Chromium
Uses both ATK and libatspi?

Sources:

chromium/ui/accessibility/platform/*auralinux* (atk)
chromium/ui/accessibility/platform/inspect/*auralinux* (atspi)
chromium/content/browser/accessibility/*auralinux* (atspi and atk)
LibreOffice
Sources: LibreOffice/core/vcl/unx/gtk3/a11y

Java Swing - via java-atk-wrapper
Sources: java-atk-wrapper


