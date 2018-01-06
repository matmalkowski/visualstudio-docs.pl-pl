---
title: "Określenie niestandardowych zdarzeń kompilacji w Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8288ce8d049f949120c5631366dbaac2efc792b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Określenie niestandardowych zdarzeń kompilacji w programie Visual Studio
Określając zdarzeń niestandardowej kompilacji, możesz automatycznie uruchamiać polecenia przed rozpoczęciem kompilacji lub po jej zakończeniu. Na przykład możesz uruchomić plik .bat przed kompilacji uruchamia lub skopiuj nowe pliki do folderu po zakończeniu kompilacji. Zdarzenia kompilacji uruchomić tylko wtedy, gdy kompilacja pomyślnie osiągnie tych punktów w procesie kompilacji.  
  
 Aby uzyskać szczegółowe informacje o języku programowania, którego używasz zobacz następujące tematy:  
  
-   Visual Basic —[porady: Określanie zdarzeń kompilacji (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).  
  
-   Visual C# i F # —[porady: Określanie zdarzeń kompilacji (C#)](../ide/how-to-specify-build-events-csharp.md).  
  
-   Visual C++ —[Określanie zdarzenia kompilacji](/cpp/ide/specifying-build-events).  
  
## <a name="syntax"></a>Składnia  
 Zdarzenia kompilacji wykonaj takiej samej składni jak polecenia systemu DOS, ale makra umożliwia łatwiejsze tworzenie zdarzeń kompilacji. Aby uzyskać listę dostępnych makr, zobacz [prekompilacyjnego zdarzeń/po kompilacji — zdarzenie wiersza polecenia okno dialogowe](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
 Aby uzyskać najlepsze wyniki wykonaj następujące porady dotyczące formatowania:  
  
-   Dodaj `call` instrukcji, aby wszystkie zdarzenia kompilacji który uruchamiać pliki bat.  
  
     Przykład:`call C:\MyFile.bat`  
  
     Przykład:`call C:\MyFile.bat call C:\MyFile2.bat`  
  
-   Ścieżki pliku należy ująć w cudzysłowy.  
  
     Przykład (dla [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "% ProgramFiles (x86) %\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" — Jeśli "$(TargetPath)"  
  
-   Rozdzielić wiele poleceń podziały wiersza.  
  
-   Zawierać symboli wieloznacznych, zgodnie z potrzebami.  
  
     Przykład: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`  
  
    > [!NOTE]
    >  `%I`Powyższy kod powinien być `%%I` w partii skryptów.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie i tworzenia](../ide/compiling-and-building-in-visual-studio.md)   
 [Okno dialogowe wiersza polecenia zdarzenia/po kompilacji — zdarzenia prekompilacyjnego](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Znaki specjalne w programie MSBuild](../msbuild/msbuild-special-characters.md)   
 [Przewodnik: Kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)