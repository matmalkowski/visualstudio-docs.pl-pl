---
title: Okno dialogowe wiersza polecenia zdarzenia prekompilacyjnego zdarzenia po kompilacji
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e27a7e624607009e986d301fa802fdbe1597a3c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Wiersz polecenia zdarzenia sprzed kompilacji/zdarzenia po kompilacji — Okno dialogowe
Możesz wpisać zdarzeń przed lub po kompilacji dla [kompilacji strona zdarzenia, Projektant projektu (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) bezpośrednio w edytowania pola, lub wybrać makra przed i po kompilacji z listy dostępnych makr.

> [!NOTE]
> Jeśli projekt jest aktualny i kompilacji nie zostanie wywołany, nie należy uruchamiać zdarzenia prekompilacyjnego.


## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika
 **Pole edycji wiersza polecenia**

 Zawiera zdarzenia, które należy uruchomić dla wstępnej kompilacji lub mające miejsce po kompilacji.

> [!NOTE]
> Dodaj `call` instrukcję przed wszystkie postkompilacyjnego polecenia, które uruchamiają pliki bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.


 **Makra**

 Rozwija pole edycji, aby wyświetlić listę makr do wstawienia w polu edycji wiersza polecenia.

 **Tabela — makro**

 Wyświetla listę dostępnych makr i jej wartość. Makra poniżej, zobacz opis każdego z nich. Można wybrać tylko jedno makro naraz można umieścić w polu edycji wiersza polecenia.

 **Wstaw**

 Pole po wybraniu makra w tabeli makro edycji wstawiania do wiersza polecenia.

### <a name="macros"></a>Makra
 Określ lokalizację plików lub pobrać rzeczywistą nazwą pliku wejściowego w przypadku zaznaczenia wielu można użyć dowolnej z tych makr. Tych makr nie jest rozróżniana.

|Macro|Opis|
|-----------|-----------------|
|`$(ConfigurationName)`|Nazwa w bieżącej konfiguracji projektu, na przykład "Debugowanie".|
|`$(OutDir)`|Ścieżka do katalogu wyjściowego pliku względem katalogu projektu. To jest rozpoznawany jako wartość właściwości katalogu wyjściowego. Zawiera ukośnik odwrotny na końcu "\\".|
|`$(DevEnvDir)`|Katalogu instalacyjnego programu Visual Studio (zdefiniowany o dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|
|`$(PlatformName)`|Nazwa platformy docelowej obecnie. Na przykład "AnyCPU".|
|`$(ProjectDir)`|W katalogu projektu (zdefiniowany o dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|
|`$(ProjectPath)`|Nazwa ścieżki bezwzględnej projektu (zdefiniowane z dysku, ścieżka, nazwa podstawowa i rozszerzenie pliku).|
|`$(ProjectName)`|Podstawowa nazwa projektu.|
|`$(ProjectFileName)`|Nazwa pliku projektu (zdefiniowane z podstawowej nazwy pliku rozszerzenie).|
|`$(ProjectExt)`|Rozszerzenie pliku projektu. Obejmuje on "." przed rozszerzeniem pliku.|
|`$(SolutionDir)`|Katalog rozwiązania (zdefiniowany o dysk i ścieżkę); zawiera ukośnik odwrotny na końcu "\\".|
|`$(SolutionPath)`|Nazwa ścieżki bezwzględnej rozwiązania (zdefiniowane z dysku, ścieżka, nazwa podstawowa i rozszerzenie pliku).|
|`$(SolutionName)`|Nazwa podstawowego rozwiązania.|
|`$(SolutionFileName)`|Nazwa pliku rozwiązania (zdefiniowane z podstawowej nazwy pliku rozszerzenie).|
|`$(SolutionExt)`|Rozszerzenie pliku rozwiązania. Obejmuje on "." przed rozszerzeniem pliku.|
|`$(TargetDir)`|Katalog podstawowego pliku wyjściowego dla kompilacji (zdefiniowany o dysk i ścieżkę). Zawiera ukośnik odwrotny na końcu "\\".|
|`$(TargetPath)`|Ścieżka bezwzględna Nazwa podstawowego pliku wyjściowego dla kompilacji (zdefiniowane z dysku, ścieżka, nazwa podstawowa i rozszerzenie pliku).|
|`$(TargetName)`|Podstawowa nazwa podstawowego pliku wyjściowego dla kompilacji.|
|`$(TargetFileName)`|Nazwa pliku podstawowego pliku wyjściowego dla kompilacji (zdefiniowany jako podstawowej nazwy pliku rozszerzenie).|
|`$(TargetExt)`|Rozszerzenie pliku podstawowego pliku wyjściowego dla kompilacji. Obejmuje on "." przed rozszerzeniem pliku.|

## <a name="see-also"></a>Zobacz też

- [Określanie niestandardowych zdarzeń kompilacji w programie Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)
- [Strona Zdarzenia kompilacji, Projektant projektu (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)
- [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Instrukcje: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)