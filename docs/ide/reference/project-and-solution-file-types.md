---
title: Typy plików projektu i rozwiązania
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- .sln files
- .suo files
- file types [Visual Studio]
- file extensions [Visual Studio]
- solution files [Visual Studio]
- sln files
- suo files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3786d6f38e4f87aa05a51b0a6112613bda65e56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="project-and-solution-file-types"></a>Typy plików projektu i rozwiązania

Program Visual Studio obsługuje wiele typów plików. W danej instalacji zainstalowanych składników określić typy plików są obsługiwane. Ten temat zawiera listę typów plików rozwiązań i projektów, które są obsługiwane w niektórych typowych instalacji.

## <a name="solution-files-sln-and-suo"></a>Pliki rozwiązania (sln i .suo)

Visual Studio wykorzystuje dwa typy plików (.sln i .suo) do przechowywania ustawień dla rozwiązania. Te pliki, nazywane pliki rozwiązania dostarczać informacje potrzebne do wyświetlenia interfejsem graficznym do zarządzania plikami Eksploratora rozwiązań.

|Rozszerzenia|Nazwa|Opis|
|---------------|----------|-----------------|
|.sln|Rozwiązanie programu Visual Studio|Organizuje projektów, elementy projektów i elementów rozwiązania w zakresie.|
|.suo|Opcje użytkownika rozwiązania|Przechowuje informacje o Dostosowywanie na poziomie użytkownika, wprowadzonych do programu Visual Studio, takich jak punkty przerwania.|

## <a name="project-files"></a>Pliki projektu

Projekty mogą zawierać wiele różnych typów plików. Na przykład mieć pliki kodu C# **.cs** rozszerzenie i plików C++ **.cpp** rozszerzenia. Zasoby są przechowywane w **.resx** plików i języka XAML w **.xaml** plików. [App.config](../../ide/managing-application-settings-dotnet.md) pliki zawierają informacje o aplikacji, które nie powinny znajdować się w kodzie aplikacji&mdash;na przykład parametry połączenia.

Aby uzyskać więcej informacji na temat typów plików w projektach C++, zobacz [pliku typy utworzone dla projektów Visual C++](/cpp/ide/file-types-created-for-visual-cpp-projects).

## <a name="see-also"></a>Zobacz także

- [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)