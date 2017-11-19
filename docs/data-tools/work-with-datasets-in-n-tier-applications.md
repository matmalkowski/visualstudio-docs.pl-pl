---
title: Praca z zestawami danych w aplikacjach warstwowych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 85062fe6ea82a73fbc2d64e1d1ce9136d16831cf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Praca z zestawami danych w aplikacjach warstwowych
*Aplikacje warstwowe —* są skoncentrowane na dane aplikacji, które są podzielone na kilka logicznych warstw (lub *warstw*). Innymi słowy aplikacji warstwowych jest aplikacja, która jest podzielony na wiele projektów z warstwą dostępu do danych, warstwy logiki biznesowej, a warstwą prezentacji każdego własnego projektu. Aby uzyskać więcej informacji, zobacz [N-warstwowa danych aplikacji — omówienie](../data-tools/n-tier-data-applications-overview.md).  
  
Typizowane zbiory danych zostały rozszerzone, aby klasy TableAdapters i danych mogą być generowane w projektach dyskretnych. Zapewnia możliwość szybkiego oddzielne warstwy aplikacji i generowanie aplikacji warstwowych.  
  
Obsługa N-warstwowa w typizowanych zbiorach danych umożliwia iteracyjne projektowanie architektura n warstwowa projektu. Eliminuje konieczność ręcznie podzielić kod na więcej niż jednym projekcie. Uruchamiane projektowania Warstwa danych przy użyciu **Projektant obiektów Dataset**. Jeśli wszystko jest gotowa do sporządzenia architektura projektowi wielowarstwowej, ustaw **projektu DataSet** właściwości zestawu danych do generowania klasy dataset w oddzielny projekt.  
  
## <a name="reference"></a>Tematy pomocy  
<xref:System.Data.DataSet>  
<xref:System.Data.TypedTableBase%601>  
  
## <a name="see-also"></a>Zobacz także
[Omówienie aplikacji warstwowych](../data-tools/n-tier-data-applications-overview.md)  
[Wskazówki: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
[Dodawanie kodu do TableAdapters w aplikacjach warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[Dodawanie kodu do zestawów danych w aplikacjach warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
[Dodawanie walidacji do warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md)  
[Oddzielne zestawy danych i TableAdapters do różnych projektów](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
[Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md)  
[Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
[Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
[Tworzenie i konfigurowanie TableAdapters](../data-tools/create-and-configure-tableadapters.md)  
[N-warstwowa oraz zdalnych aplikacji za pomocą LINQ do SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)