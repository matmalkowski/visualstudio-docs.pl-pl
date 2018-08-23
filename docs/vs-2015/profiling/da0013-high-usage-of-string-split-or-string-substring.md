---
title: 'Da0013: znaczące Wykorzystanie String.Split lub String.Substring | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8f835e120f730f9c223477959e9c93dfefa240
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42688654"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Znaczące wykorzystanie String.Split lub String.Substring
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [da0013 znaczące: wysokiego użycia funkcji String.Split i String.Substring](https://docs.microsoft.com/visualstudio/profiling/da0013-high-usage-of-string-split-or-string-substring).  
  
Identyfikator reguły | DA0013 ZNACZĄCE |  
| Kategoria |. Wskazówki dotyczące użycia NET Framework |  
| Profilowanie metody | Próbkowanie |  
| Komunikat | Rozważ ograniczenie użycia funkcji String.Split i String.Substring. |  
| Typ reguły | Ostrzeżenie |  
  
## <a name="cause"></a>Przyczyna  
 Wywołania metod System.String.Split lub System.String.Substring jest znaczna część danych profilowania. Należy rozważyć użycie System.String.IndexOf lub System.String.IndexOfAny, jeśli testujesz istnienie podciągów w ciągu.  
  
## <a name="rule-description"></a>Opis reguły  
 Metoda Podziel operuje na obiekt ciągu i zwraca nową tablicę ciągów, która zawiera podciągów z oryginalnego. Funkcja przydziela pamięć dla obiektu zwróconej tablicy i przydziela nowy obiekt ciągu dla każdego elementu tablicy, które znajdzie. Podobnie metoda Substr operuje na obiekt ciągu i zwraca nowy ciąg, który jest odpowiednikiem podciągu, który otrzymał żądanie.  
  
 Jeśli zarządzanie alokacji pamięci ma kluczowe znaczenie dla aplikacji, należy rozważyć użycie alternatywy dla funkcji String.Split i String.Substr metod. Na przykład służy metoda IndexOf albo IndexOfAny aby zlokalizować podciąg określonego w ciągu znaków ciągu bez tworzenia nowego wystąpienia klasy String.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widok szczegółów funkcji](../profiling/function-details-view.md) pobierania próbek danych jej profilu. Sprawdź wywołania funkcji można znaleźć w sekcjach program najczęściej wykorzystać System.String.Split lub System.String.Substr metod. Jeśli jest to możliwe, należy użyć metody IndexOf albo IndexOfAny aby zlokalizować podciąg określonego w ciągu znaków ciągu bez tworzenia nowego wystąpienia klasy String.



