---
title: "Właściwość &lt;nazwa właściwości&gt; nie można usunąć | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5bba0739a35dbc90c0c9141619c54b93f653d482
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Właściwość &lt;nazwa właściwości&gt; nie można usunąć
Właściwość \<właściwość name > nie można usunąć, ponieważ jest ona ustawiona jako **właściwość rozróżniacza** dziedziczenia między \<Nazwa klasy > i \<Nazwa klasy >  
  
 Wybranej właściwości jest ustawiana jako **właściwość rozróżniacza** dziedziczenia między klasami wskazany w komunikacie o błędzie. Nie można usunąć właściwości, jeśli są elementami konfiguracji dziedziczenia między klasami danych.  
  
 Ustaw **właściwość rozróżniacza** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  W Projektancie obiektów relacyjnych wybierz linii dziedziczenia, który łączy klas danych wskazany w komunikacie o błędzie.  
  
2.  Ustaw **rozróżniacza** właściwości inną właściwość.  
  
3.  Spróbuj ponownie usunąć właściwości.  
  
## <a name="see-also"></a>Zobacz także
[Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)