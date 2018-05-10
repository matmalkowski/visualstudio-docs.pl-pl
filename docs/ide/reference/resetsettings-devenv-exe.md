---
title: -ResetSettings (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c3d3a6ef558b510cfde716716daf97a549fbba4
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Przywraca ustawienia domyślne programu Visual Studio i powoduje automatyczne uruchomienie programu Visual Studio IDE. Opcjonalnie resetuje ustawienia do określonej *vssettings* pliku.

Ustawienia domyślne są określane przez profil, który został wybrany, gdy najpierw została uruchomiona Visual Studio.

## <a name="syntax"></a>Składnia

```cmd
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Argumenty

`SettingsFile`

Pełna ścieżka i nazwa *vssettings* pliku w celu zastosowania do programu Visual Studio.

Aby przywrócić profilu ogólne ustawienia środowiska deweloperskiego, należy użyć `General`.

## <a name="remarks"></a>Uwagi

Jeśli nie `SettingsFile` jest określona, zostanie wyświetlony monit o wybierz domyślną kolekcję ustawień przy następnym uruchomieniu programu Visual Studio.

## <a name="example"></a>Przykład

Następujące polecenie w wierszu stosuje ustawienia przechowywane w pliku `MySettings.vssettings`.

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Zobacz też

- [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)