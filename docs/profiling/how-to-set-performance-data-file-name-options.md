---
title: "Porady: Ustawianie opcji nazwy pliku danych wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 07aecd8c21c97fd84ea7c286abade06b3e9de84e
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-set-performance-data-file-name-options"></a>Porady: Ustawianie opcji nazwy pliku danych wydajności

Domyślnie zapiszesz plik danych (Vsp) profilowania przy użyciu następującej składni:

*Path\VSP-File\YYMMDD(N)* **.vsp**

Można zmienić żadnych nazw parametrów, na stronie Ogólne okno dialogowe właściwości sesji wydajności.

|||
|-|-|
|*Path*|Katalog, który zawiera raport. Domyślna lokalizacja to folder rozwiązania lub domyślna lokalizacja dla projektów i rozwiązań użytkownika.|
|*VSP-File*|Nazwa pliku danych profilowania. Domyślna nazwa jest nazwą rozwiązania lub pliku wykonywalnego który jest profilowane.|
|*YYMMDD*|Sygnatura daty, pokazujący rok, miesiąc i dzień, zebrane dane profilowania.|
|*(N)*|Jeśli istnieje więcej niż jeden plik danych profilowania, numer zwiększany jest dodawany do nazwy pliku w nawiasach.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Aby zmienić składnię nazewnictwa plików danych profilowania w sesji wydajności

1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij przycisk **właściwości**.

2. Kliknij przycisk **ogólne**.

3. W obszarze **raport**, zmienić dowolne z następujących ustawień:

    |||
    |-|-|
    |**Lokalizacja raportu**|Określ katalog do przechowywania plików danych profilowania.|
    |**Nazwa raportu**|Określ nazwę podstawową dla plików.|
    |**Automatycznie Dodaj nowe raporty do sesji**|Zaznacz pole wyboru, aby automatycznie dodać pliku danych do sesji wydajności.|
    |**Dodaj zwiększającą się liczbę do wygenerowanych raportów**|Zaznacz pole wyboru, aby dodać zwiększającą się liczbę do nazwy pliku, jeśli istnieje więcej niż jeden plik o tej samej nazwie. Wyczyść pole wyboru, aby zastąpić istniejący plik.|
    |**Użyj sygnatury czasowej dla liczby**|Zaznacz pole wyboru, aby dodać datestamp do nazwy pliku.|