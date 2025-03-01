---
title: Icons
description: >
  Deliver your application with icons.
group: features
weight: 2
aliases:
  - /docs/plasma-integration/icons/
---

When you create your own KDE application you will probably want to have icons in it respecting your user's icon theme. 

This is possible with the help of [QIcon::fromTheme](https://doc.qt.io/qt-5/qicon.html#fromTheme) for QtWidgets applications or [Kirigami's Icon](docs:kirigami2;Icon) for QtQuick applications. Both take the name of the icon in the icon theme as an argument.

Plasma and all the other major Linux deskops follow the Freedesktop [icon specification](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html) and [naming specification](http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html). A fallback mechanism is also present so that if the `document-open-recent` icon is not present, the `document-open` icon will be displayed instead, and if the `document-open` icon is also not present the `document` icon will be displayed.

## Finding the right icons

KDE provides an application to search for icons, Cuttlefish. It is generally available in the `plasma-sdk` package available through your package manager on Linux.

![Screenshot of cuttlefish](cuttlefish.png)

Cuttlefish allows you to search for icons by name and by category. You can inspect the different color schemes of an icon as well as view a selected icon in other themes.

## Example

In a traditional QtWidgets application:

{{< highlight cpp >}}
QIcon undoicon = QIcon::fromTheme("edit-undo");
{{< /highlight >}}

In a QtQuick application:

{{< highlight qml >}}
import org.kde.kirigami 2.14 as Kirigami

Kirigami.Icon {
    source: "edit-undo"
} 
{{< /highlight >}}

## Other platforms than Linux

On other platforms, the icon theme is not available.

### Android

On Android, you can use the [kirigami_package_breeze_icons()](https://invent.kde.org/frameworks/kirigami/-/blob/master/KF5Kirigami2Macros.cmake#L5) CMake function to package the Breeze icons you are using.

{{< highlight cmake >}}
if(ANDROID)
    kirigami_package_breeze_icons(ICONS
        edit-undo
        edit-redo
    )
endif()
{{< /highlight >}}
