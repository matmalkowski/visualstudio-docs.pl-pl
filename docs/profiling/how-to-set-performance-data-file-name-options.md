---
title: 'Porady: Ustawianie opcji nazwy pliku danych wydajności | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0687b4f56906aeca0866f8d5d6ad7d329bb84df6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-set-performance-data-file-name-options"></a>Porady: Ustawianie opcji nazwy pliku danych wydajności

Domyślnie zapiszesz plik danych (Vsp) profilowania przy użyciu następującej składni:

*Path\VSP-File\YYMMDD(N)* **.vsp**

Można zmienić żadnych nazw parametrów, na stronie Ogólne okno dialogowe właściwości sesji wydajności.

|||
|-|-|
|*Path*|Katalog, który zawiera raport. Domyślna lokalizacja to folder rozwiązania lub domyślna lokalizacja dla projektów i rozwiązań użytkownika.|
|*Plik VSP*|Nazwa pliku danych profilowania. Domyślna nazwa jest nazwą rozwiązania lub pliku wykonywalnego który jest profilowane.|
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