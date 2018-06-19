---
title: Określenie niestandardowych zdarzeń kompilacji w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c45f439a8bb1ae559e915769f8ea89ef7f4bf863
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945925"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Określenie niestandardowych zdarzeń kompilacji w programie Visual Studio

Określając zdarzeń niestandardowej kompilacji, możesz automatycznie uruchamiać polecenia przed rozpoczęciem kompilacji lub po jej zakończeniu. Na przykład można uruchomić *bat* pliku przed rozpoczęciem kompilacji lub skopiuj nowe pliki do folderu po zakończeniu kompilacji. Zdarzenia kompilacji uruchomić tylko wtedy, gdy kompilacja pomyślnie osiągnie tych punktów w procesie kompilacji.

 Aby uzyskać szczegółowe informacje o języku programowania, którego używasz zobacz następujące tematy:

-   Visual Basic —[porady: Określ zdarzenia (Visual Basic) kompilacji](../ide/how-to-specify-build-events-visual-basic.md).

-   C# i F # —[porady: Określ zdarzenia (C#) kompilacji](../ide/how-to-specify-build-events-csharp.md).

-   Visual C++ —[zdarzenia kompilacji określ](/cpp/ide/specifying-build-events).

## <a name="syntax"></a>Składnia

Zdarzenia kompilacji wykonaj takiej samej składni jak polecenia systemu DOS, ale makra umożliwia łatwiejsze tworzenie zdarzeń kompilacji. Aby uzyskać listę dostępnych makr, zobacz [okno dialogowe wiersza polecenia zdarzenia/po kompilacji — zdarzenia prekompilacyjnego](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Aby uzyskać najlepsze wyniki wykonaj następujące porady dotyczące formatowania:

-   Dodaj `call` instrukcji, aby wszystkie zdarzenia, które są uruchamiane kompilacji *bat* plików.

     Przykład: `call C:\MyFile.bat`

     Przykład: `call C:\MyFile.bat call C:\MyFile2.bat`

-   Ścieżki pliku należy ująć w cudzysłowy.

     Przykład (dla [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "% ProgramFiles (x86) %\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" — Jeśli "$(TargetPath)"

-   Rozdzielić wiele poleceń podziały wiersza.

-   Zawierać symboli wieloznacznych, zgodnie z potrzebami.

     Przykład: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

    > [!NOTE]
    >  `%I` Powyższy kod powinien być `%%I` w partii skryptów.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Okno dialogowe wiersza polecenia zdarzenia/po kompilacji — zdarzenia prekompilacyjnego](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Znaki specjalne MSBuild](../msbuild/msbuild-special-characters.md)
- [Wskazówki: Tworzenie aplikacji](../ide/walkthrough-building-an-application.md)
