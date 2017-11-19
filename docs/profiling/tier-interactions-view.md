---
title: Widok interakcji warstwy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.tierinteraction
helpviewer_keywords: Tier Interactions view
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9aac5f9ac8886bef61d700209f77b4b1852fe2bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="tier-interactions-view"></a>Widok interakcji warstwowych
Profilowanie interakcji między warstwami udostępnia dodatkowe informacje o czasu wykonywania w funkcji aplikacji rozwiązania, które komunikują się z bazami danych za pośrednictwem [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]. Dane są zbierane tylko dla wywołań synchronicznych funkcji.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]  
  
 Widok interakcji przedstawia warstwy danych o interakcji między dwa okienka:  
  
-   W okienku głównym jest hierarchiczne drzewo. Zagregowane dane dotyczące połączeń bazy danych zawiera wiersza najwyższego poziomu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] strony lub procesu. Węzły podrzędne zawierają zagregowane dane dotyczące połączenia z bazą danych elementu nadrzędnego.  
  
-   Po kliknięciu węzła wywołania bazy danych, w okienku głównym dane wystąpienia wywołania bazy danych są wyświetlane w okienku szczegółów.  
  
 Czas jest wyświetlany jako liczbę milisekund lub liczba Takty zegara procesora CPU. Aby zmienić jednostkę czasu wyświetlany, kliknij przycisk **narzędzia** menu, kliknij przycisk **opcje**, a następnie wybierz jedną z **Pokaż czas wartości jako** opcje.  
  
## <a name="master-pane"></a>W okienku głównym  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|— Dla wiersza najwyższego poziomu, nazwa PROFILOWANEGO procesu lub strony sieci Web.<br />— Dla wiersza połączenia bazy danych, nazwę serwera, który jest hostem bazy danych.|  
|**Bazy danych**|Nazwa bazy danych (tylko wiersze połączenia bazy danych).|  
|**Liczba**|Całkowita liczba żądań, które są generowane przez proces, strony sieci Web lub połączenia z bazą danych.|  
|**Całkowity czas**|Łączny czas, który jest podczas wykonywania żadnych jedno żądanie z procesu, strony sieci Web lub połączenia z bazą danych.|  
|**Maksymalny czas, który upłynął**|Maksymalny czas wykonywania żadnych jedno żądanie z procesu, strony sieci Web lub połączenia z bazą danych.|  
|**Minimalny czas, który upłynął**|Minimalny czas, który jest podczas wykonywania żadnych jedno żądanie z procesu, strony sieci Web lub połączenia z bazą danych.|  
|**Średni czas, który upłynął**|Średni czas, który jest podczas wykonywania żądania z procesu, strony sieci Web lub połączenia z bazą danych.|  
  
## <a name="database-connection-details-pane"></a>W okienku szczegółów połączenia bazy danych  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Tekst polecenia**|Zapytanie SQL żądania.|  
|**Liczba zapytań**|Liczba razy uruchomienia zapytania.|  
|**Całkowity czas**|Łączny czas, który jest podczas wykonywania wystąpień zapytania.|  
|**Maksymalny czas, który upłynął**|Maksymalny czas jest poświęcony na wykonywanie żadnych jedno wystąpienie zapytania.|  
|**Minimalny czas, który upłynął**|Minimalny czas, który jest podczas wykonywania żadnych jedno wystąpienie zapytania.|  
|**Średni czas, który upłynął**|Średni czas, który jest podczas wykonywania wystąpienia zapytania.|