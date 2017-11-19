---
title: "Porady: Tworzenie raportu porównania profilera z wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fe95412c11da05d409954762f40c46745b98940
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Porady: tworzenie raportu porównania profilera z wiersza polecenia
Możesz wygenerować [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania raport, który porównuje dane dotyczące wydajności dwóch danych profilowania (. VSP notebooka. Pliki VSPS). Raport przedstawia różnice, regresji wydajności i ulepszenia, które nastąpiły jednej sesji profilowania. Wartości w raporcie przedstawia zmian lub zmiany z linii bazowej pierwszego pliku, który określisz. Tej różnicowej jest obliczana przez określenie różnica między stara wartość jest wartością linii bazowej, i wartość wyniku z nowego analizy. Porównywanie danych profilera może bazować na funkcje w kodzie, modułów w aplikacji, wiersze, wskaźników instrukcji (IP) i typy.  
  
 Aby wyświetlić listę identyfikatorów porównania kategorii i pola, wpisz następujące polecenie w wierszu:  
  
 **VSPerfReport przełącznika/querydifftables***VspFileName1* *VspFileName2*   
  
 Aby utworzyć raport Porównanie, należy użyć następującej składni:  
  
 **VSPerfReport/diff** `VspFileName1` *VspFileName2* [**/**`Options`]    
  
 Można dodać opcji z poniższej tabeli, aby **VSPerfReport/diff** wiersza polecenia.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**DiffThreshold:**[*wartość*]|Różnica należy pominąć, jeśli jest poniżej tej wartości procentowej wartości progu. Ponadto nowe dane z wartościami, które znajdują się poniżej tego progu nie będą wyświetlane.|  
|**DiffTable:** *TableName*|Ta tabela służy do porównywania plików. Domyślnie jest używana w tabeli funkcji. Określ identyfikator, który znajduje się w **VSPerfReport przełącznika/querydifftables**.|  
|**DiffColumn:** *ColumnName*|Ta kolumna służy do porównywania wartości. Domyślnie jest używana kolumna procentową wyłącznych próbek. Określ identyfikator, który znajduje się w **VSPerfReport przełącznika/querydifftables**.|