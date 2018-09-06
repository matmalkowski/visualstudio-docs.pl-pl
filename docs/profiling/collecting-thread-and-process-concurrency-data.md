---
title: Zbieranie danych współbieżności procesu i wątku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8ce2c1d7a28eff441cbf3a95e8f9df644789e70
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775558"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Zbieranie danych współbieżności dla wątku i procesu

Metoda profilowania współbieżności Visual Studio Profiling Tools umożliwia zbieranie danych rywalizacji zasobów, który zawiera informacje na temat każdego zdarzenia synchronizacji, który powoduje, że funkcji w profilowanej aplikacji, aby czekać na dostęp do zasobu.

Można określić współbieżności, metoda profilowania przy użyciu jednej z następujących procedur:

- Na pierwszej stronie kreatora profilowania, kliknij przycisk **współbieżności**
- Na **ogólne** strony okna dialogowego właściwości sesji wydajności, kliknij przycisk **współbieżności**.
- Na **Eksplorator wydajności** narzędzi w **metoda** kliknij **współbieżności**.

## <a name="common-tasks"></a>Wspólne zadania

Można określić dodatkowe opcje w _sesji wydajności_**stron właściwości** okna dialogowego sesji wydajności. Aby otworzyć to okno dialogowe:

- W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij **właściwości**.

Zadania przedstawione w poniższej tabeli opisano opcje, które można określić w _sesji wydajności_**stron właściwości** okno dialogowe podczas profilowania za pomocą metody współbieżności.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na **ogólne** Określ szczegóły nazewnictwa dla wygenerowanego pliku danych (Vsp) profilowania.|- [Porady: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na **Uruchom** Określ aplikację do uruchomienia, jeśli masz wiele projektów .exe w rozwiązaniu kodu.|- [Porady: Określanie plików binarnych do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|
|Na **funkcję Tier Interaction** strony, należy dodać danych połączeń ADO.NET do uruchomienia profilowania.|- [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|
|Na **liczniki Windows** stronie Określ co najmniej jeden licznik wydajności systemu operacyjnego można dodać do danych profilowania jako znaki.|- [Porady: zbieranie danych licznika Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na **zaawansowane** Określ wersję środowiska wykonawczego .NET Framework do profilowania, jeśli moduły aplikacji używać wielu wersji. Domyślnie jest profilowane pierwszej wersji załadowane.|- [Porady: Określanie środowiska uruchomieniowego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|