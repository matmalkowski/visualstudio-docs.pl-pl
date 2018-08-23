---
title: Praca z zestawami danych w aplikacjach n warstwowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61f3686488a460ef4c7091521c2165f575e76fa6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676858"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Praca z zestawami danych w aplikacjach n-warstwowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Praca z zestawami danych w aplikacjach n warstwowych](https://docs.microsoft.com/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
  
Aplikacje warstwowe — * są aplikacji biznesowych przetwarzających dane, które są rozdzielone na wiele warstw logiczne (lub *warstwy*). Innymi słowy aplikacja n warstwowa danych jest aplikacja, która jest dzielony na wiele projektów z warstwy dostępu do danych, warstwy logiki biznesowej i warstwy prezentacji każdego we własnym projekcie. Aby uzyskać więcej informacji, zobacz [N-warstwowa danych aplikacji — omówienie](../data-tools/n-tier-data-applications-overview.md).  
  
 Tak, aby klas TableAdapters i zestawu danych mogą być generowane w dyskretne projekty zostały rozszerzone typizowanych zestawów danych. Zapewnia to możliwość szybkiego oddzielnymi warstwami aplikacji i generowania aplikacji n warstwowa danych.  
  
 Obsługa N-warstwowej w typizowanych zbiorach danych umożliwia iteracyjne projektowanie architektury aplikacji n warstwowa projektowi. Usuwa wymaganie, aby ręcznie odseparowania kodu do więcej niż jeden projekt. Rozpocząć projektowanie warstwę danych przy użyciu [tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md). Gdy wszystko będzie gotowe, umożliwiające architektura n warstwowa projektu, należy ustawić **projektu DataSet** właściwości zestawu danych, aby wygenerować klasę zestawu danych do oddzielnego projektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 W tym artykule opisano sposób przenoszenia wygenerowaną klasę zestawu danych z projektu, który zawiera wygenerowane klasy TableAdapter z do nowego projektu.  
  
 [Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 W tym artykule opisano sposób generowania klasy częściowej, w którym można dodać kod TableAdapter n warstwowej.  
  
 [Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 W tym artykule opisano sposób generowania klasy częściowej, w którym można dodać kodu dla zestawu danych n warstwowej.  
  
 [Dodawanie walidacji do n-warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 W tym artykule opisano gdzie dodać kod do wykonywania sprawdzania poprawności od zmieniających się danych.  
  
 [Przewodnik: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Instrukcje krok po kroku dotyczące tworzenia typizowany zestaw danych i oddzielenie kodu TableAdapter i zestaw danych do wielu projektów.  
  
 [Wskazówki: Dodawanie walidacji do aplikacji warstwowych](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 Instrukcje krok po kroku do dodawania sprawdzania poprawności do aplikacji, który został utworzony w Przewodnik po aplikacji n warstwowa danych.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie aplikacji N-warstwowa danych](../data-tools/n-tier-data-applications-overview.md)  
  
 [Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md)  
  
 [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)  
  
 [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

