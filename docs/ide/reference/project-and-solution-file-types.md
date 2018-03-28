---
title: Typy plików projektu i rozwiązania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d239a5e129f12c4521ba190674d84430f8f2e646
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="project-and-solution-file-types"></a>Typy plików projektu i rozwiązania

Program Visual Studio obsługuje wiele typów plików. W danej instalacji zainstalowanych składników określić typy plików są obsługiwane. Ten temat zawiera listę typów plików rozwiązań i projektów, które są obsługiwane w niektórych typowych instalacji.

## <a name="solution-files-sln-and-suo"></a>Pliki rozwiązania (sln i .suo)

Visual Studio wykorzystuje dwa typy plików (.sln i .suo) do przechowywania ustawień dla rozwiązania. Te pliki, nazywane pliki rozwiązania dostarczać informacje potrzebne do wyświetlenia interfejsem graficznym do zarządzania plikami Eksploratora rozwiązań.

|Rozszerzenia|Nazwa|Opis|
|---------------|----------|-----------------|
|.sln|Visual Studio Solution|Organizuje projektów, elementy projektów i elementów rozwiązania w zakresie.|
|.suo|Opcje użytkownika rozwiązania|Przechowuje informacje o Dostosowywanie na poziomie użytkownika, wprowadzonych do programu Visual Studio, takich jak punkty przerwania.|

## <a name="project-files"></a>Pliki projektu

Projekty mogą zawierać wiele różnych typów plików. Na przykład mieć pliki kodu C# **.cs** rozszerzenie i plików C++ **.cpp** rozszerzenia. Zasoby są przechowywane w **.resx** plików i języka XAML w **.xaml** plików. [App.config](../../ide/managing-application-settings-dotnet.md) pliki zawierają informacje o aplikacji, które nie powinny znajdować się w kodzie aplikacji&mdash;na przykład parametry połączenia.

Aby uzyskać więcej informacji na temat typów plików w projektach C++, zobacz [pliku typy utworzone dla projektów Visual C++](/cpp/ide/file-types-created-for-visual-cpp-projects).

## <a name="see-also"></a>Zobacz także

[Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)