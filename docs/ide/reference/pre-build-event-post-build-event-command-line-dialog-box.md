---
title: "Przed kompilacją okno dialogowe wiersza polecenia zdarzenia po kompilacji zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7d2ec0c94de336adf2c8fd10946466aafcecc72a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Wiersz polecenia zdarzenia sprzed kompilacji/zdarzenia po kompilacji — Okno dialogowe
Możesz wpisać zdarzeń przed lub po kompilacji dla [kompilacji strona zdarzenia, Projektant projektu (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) bezpośrednio w edytowania pola, lub wybrać makra przed i po kompilacji z listy dostępnych makr.  
  
> [!NOTE]
>  Jeśli projekt jest aktualny i kompilacji nie zostanie wywołany, nie należy uruchamiać zdarzenia prekompilacyjnego.  
  
## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika  
 **Pole edycji wiersza polecenia**  
 Zawiera zdarzenia, które należy uruchomić dla wstępnej kompilacji lub mające miejsce po kompilacji.  
  
> [!NOTE]
>  Dodaj `call` instrukcję przed wszystkie postkompilacyjnego polecenia, które uruchamiają pliki bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Makra**  
 Rozwija pole edycji, aby wyświetlić listę makr do wstawienia w polu edycji wiersza polecenia.  
  
 **Tabela — makro**  
 Wyświetla listę dostępnych makr i jej wartość. Makra poniżej, zobacz opis każdego z nich. Można wybrać tylko jedno makro naraz można umieścić w polu edycji wiersza polecenia.  
  
 **Wstaw**  
 Pole po wybraniu makra w tabeli makro edycji wstawiania do wiersza polecenia.  
  
### <a name="macros"></a>Makra  
 Określ lokalizację plików lub pobrać rzeczywistą nazwą pliku wejściowego w przypadku zaznaczenia wielu można użyć dowolnej z tych makr. Tych makr nie jest rozróżniana.  
  
|Makra|Opis|  
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
 [Określenie niestandardowych zdarzeń kompilacji w programie Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)   
 [Strona zdarzenia kompilacji, Projektant projektu (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)   
 [Porady: Określanie zdarzeń kompilacji (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Porady: Określanie zdarzeń kompilacji (C#)](../../ide/how-to-specify-build-events-csharp.md)