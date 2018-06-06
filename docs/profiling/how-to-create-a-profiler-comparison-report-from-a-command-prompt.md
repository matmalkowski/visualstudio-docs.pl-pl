---
title: 'Porady: Tworzenie raportu porównania profilera z wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 88fac8339491acbe73a4a446cde8afb54fa63143
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814654"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Porady: Tworzenie raportu porównania profilera z wiersza polecenia
Możesz wygenerować [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania raport, który porównuje dane dotyczące wydajności dwóch danych profilowania (. *Vsp* notebooka. *vsps*) plików. Raport przedstawia różnice, regresji wydajności i ulepszenia, które nastąpiły jednej sesji profilowania. Wartości w raporcie przedstawia zmian lub zmiany z linii bazowej pierwszego pliku, który określisz. Tej różnicowej jest obliczana przez określenie różnica między stara wartość jest wartością linii bazowej, i wartość wyniku z nowego analizy. Porównywanie danych profilera może bazować na funkcje w kodzie, modułów w aplikacji, wiersze, wskaźników instrukcji (IP) i typy.  
  
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