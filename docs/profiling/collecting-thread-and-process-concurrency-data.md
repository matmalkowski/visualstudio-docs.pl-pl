---
title: Zbieranie danych współbieżności procesu i wątku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7e5c0ad896a19c19dc5913fd47f0fdb49a9ef01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Zbieranie danych współbieżności dla wątku i procesu

Metoda profilowania współbieżności Visual Studio Profiling Tools umożliwia zbieranie danych kontencji zasobów, który zawiera informacje o zdarzeniu co synchronizacji, który powoduje, że funkcja w profilowanych aplikacji oczekiwania na dostęp do zasobu.

Można określić współbieżności, metoda profilowania za pomocą jednej z następujących procedur:

- Na pierwszej stronie kreatora profilowania, kliknij przycisk **współbieżności**
- Na **ogólne** strony okna dialogowego właściwości sesji wydajności, kliknij przycisk **współbieżności**.
- Na **Eksplorator wydajności** paska narzędzi w **metody** kliknij **współbieżności**.

## <a name="common-tasks"></a>Typowe zadania

Możesz określić dodatkowe opcje w *sesji wydajności *** strony właściwości** okno dialogowe sesji wydajności. Aby otworzyć okno dialogowe:

- W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij przycisk **właściwości**.

Zadania w poniższej tabeli opisano opcje, które można określić w *sesji wydajności *** strony właściwości** okno dialogowe, gdy profilu przy użyciu metody współbieżności.

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|Na **ogólne** Określ szczegóły nazewnictwa dla profilowania wygenerowany plik danych (Vsp).|- [Porady: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na **uruchamianie** Określ aplikację do uruchomienia, jeśli masz wiele projektów .exe w rozwiązaniu kodu.|- [Porady: Określanie plików binarnych do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|
|Na **interakcja warstwowa** Dodaj ADO.NET data wywołania do uruchomienia profilowania.|- [Zbieranie danych o interakcji między warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na **liczników systemu Windows** strony, określ co najmniej jeden liczników wydajności systemu operacyjnego można dodać do danych profilowania jako znaczniki.|- [Porady: zbieranie danych liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na **zaawansowane** strony, określ wersję środowiska wykonawczego .NET Framework do profilowania, jeśli moduły aplikacji używać wielu wersji. Domyślnie jest profilowane pierwszej wersji załadowane.|- [Porady: Określanie środowiska wykonawczego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|