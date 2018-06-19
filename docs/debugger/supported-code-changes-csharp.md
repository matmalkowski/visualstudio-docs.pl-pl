---
title: Obsługiwane zmiany kodu (C# i Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 855e8111721480b98c1395811090a54dd6e3ab2a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480537"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Obsługiwane zmiany kodu (C# i Visual Basic)
Edytuj i Kontynuuj obsługuje większość typów zmian kodu w treści metody. Większość zmian poza treść metody i kilka zmian w treści metody nie można zastosować podczas debugowania, jednak. Aby zastosować te zmiany nieobsługiwany, należy zatrzymać debugowanie i ponowne uruchomienie programu kodu.

## <a name="supported-changes-to-code"></a>Obsługiwane zmiany kodu

Poniższa tabela zawiera zmiany, które mogą być nawiązywane C# i Visual Basic kodu podczas sesji debugowania bez ponownego uruchomienia sesji.

|Funkcja element języka|Operacja edytowania obsługiwane|Ograniczenia|
|-|-|-|
|Types|Dodawanie metody, pola, konstruktorów, i inni|[Tak](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iteratory|Dodaje lub modyfikuje|Nie|
|wyrażenia asynchronicznej/await|Dodaje lub modyfikuje|[Tak](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Obiekty dynamiczne|Dodaje lub modyfikuje|Nie|
|wyrażenia lambda|Dodaje lub modyfikuje|[Tak](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Wyrażenia zapytań LINQ|Dodaje lub modyfikuje|[Sam, jak wyrażenia lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Nowszymi funkcjami języka, takie jak ciąg interpolacji i operatory warunkowe null są zazwyczaj obsługiwane przez Edytuj i Kontynuuj. Aby uzyskać najbardziej aktualne informacje, zobacz [Enc obsługiwane edytuje](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) strony.

## <a name="unsupported-changes-to-code"></a>Nieobsługiwane zmiany kodu
 Następujące zmiany nie można zastosować do kodu C# i Visual Basic podczas sesji debugowania:  
  
-   Zmiany bieżącej instrukcji lub aktywnej instrukcji.  
  
     Instrukcje aktywnej obejmują wszystkie instrukcje w funkcji w stosie wywołań, które zostały wywołane na uzyskanie dostępu do bieżącej instrukcji.  
  
     Bieżąca instrukcja charakteryzuje się żółty tła w oknie źródła. Inne instrukcje aktywnej są oznaczane przyciemnione tła i są tylko do odczytu. Kolory domyślne można zmienić w **opcje** okno dialogowe.

- W poniższej tabeli przedstawiono nieobsługiwane zmiany kodu w elemencie języka.

|Funkcja element języka|Operacja nieobsługiwanej edycji|
|-|-|
|Wszystkie elementy kodu|Zmiana nazwy|
|Namespaces|Dodaj|
|Przestrzenie nazw, typów, elementy członkowskie|Usuwanie|
|Typy ogólne|Dodaje lub modyfikuje|
|Interfejsy|Modyfikowanie|
|Types|Dodaj element członkowski abstrakcyjna lub wirtualna, Dodaj zastąpienie (zobacz [szczegóły](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Types|Dodaj — destruktor|
|Elementy członkowskie|Zmodyfikuj element członkowski odwołanie do osadzonego typu międzyoperacyjnego|
|Elementy członkowskie (Visual Basic)|Zmodyfikuj element członkowski z On Error lub Resume — instrukcja|
|Elementy członkowskie (Visual Basic)|Zmodyfikuj element członkowski zawierający agregacji, Group By, prostego, klauzuli Join lub LINQ Dołącz do grupy zapytań|
|Metody|Modyfikowanie podpisów|
|Metody|Wprowadź metody abstrakcyjnej stają się nieabstrakcyjnej przez dodanie treści metody|
|Metody|Usunięcie treści metody|
|Atrybuty|Dodaje lub modyfikuje|
|Właściwości lub zdarzenia|Zmodyfikuj parametr typu, typ podstawowy typ delegata lub typ zwracany |
|Operatory lub indeksatorów|Zmodyfikuj parametr typu, typ podstawowy typ delegata lub typ zwracany |
|bloki catch|Modyfikowanie, gdy zawiera aktywnej instrukcji|
|bloki try-catch-finally|Modyfikowanie, gdy zawiera aktywnej instrukcji|
|instrukcje using|Dodaj|
|metody asynchroniczne/wyrażeń lambda|Modyfikowanie asynchronicznej metody/lambda w projektach przeznaczonych dla platformy .NET Framework 4 i zmniejszyć (zobacz [szczegóły](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iteratory|Modyfikowanie iterację w projektach przeznaczonych dla platformy .NET Framework 4 i zmniejszyć (zobacz [szczegóły](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
  
## <a name="unsafe-code"></a>Kod niezabezpieczony  
 Zmiany niebezpieczny kod mają te same ograniczenia co zmiany kodu bezpieczne, z jednego ograniczenia dodatkowe: Edytuj i Kontynuuj nie obsługuje zmiany niebezpieczny kod, który kończy w obrębie metody, która zawiera `stackalloc` operatora.  

## <a name="unsupported-app-scenarios"></a>Scenariusze nieobsługiwane aplikacji

Nieobsługiwany aplikacji i platform obejmują ASP.NET 5, Silverlight 5 i Windows 8.1.

> [!NOTE]
> Aplikacje, które są obsługiwane obejmują platformy uniwersalnej systemu Windows w systemie Windows 10 i x86 i x64 aplikacji przeznaczonych dla platformy .NET Framework 4.6 pulpitu lub nowszej wersji (.NET Framework jest tylko wersja desktop).
  
## <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze  
 Edytuj i Kontynuuj nie jest dostępna w następujących scenariuszach debugowania:  
  
-   Debugowanie trybu mieszanego (natywną/zarządzaną).  
  
-   Debugowanie SQL.  
  
-   Debugowanie odzyskiwania po awarii. Watson zrzutu.  
  
-   Debugowanie aplikacji osadzonych środowiska wykonawczego.  
  
-   Debugowanie aplikacji przy użyciu dołączyć do procesu (**Debuguj > dołączyć do procesu**) zamiast uruchamiania aplikacji przez wybranie **Start** z **debugowania** menu.  
  
-   Debugowanie zoptymalizowanego kodu.  
  
-   Debugowanie starą wersję kodu po nowej wersji nie można skompilować z powodu błędów kompilacji.
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i Kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Instrukcje: używanie funkcji Edytuj i kontynuuj (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)