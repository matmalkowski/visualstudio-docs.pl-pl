---
title: Właściwość &lt;nazwa właściwości&gt; nie można usunąć, ponieważ uczestniczy ona w skojarzeniu &lt;Nazwa skojarzenia&gt; | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5121d79e6db6bdef1deb0ee04540295b2a109f72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Właściwość &lt;nazwa właściwości&gt; nie można usunąć, ponieważ uczestniczy ona w skojarzeniu &lt;Nazwa skojarzenia&gt;
Wybranej właściwości jest ustawiana jako **właściwości skojarzenia** dla skojarzenia między klasami wskazany w komunikacie o błędzie. Nie można usunąć właściwości, jeśli są elementami skojarzenie między klasami danych.  
  
 Ustaw **właściwości skojarzenia** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Wybierz wiersz skojarzenia w Projektancie obiektów relacyjnych łączącego klas danych wskazany w komunikacie o błędzie.  
  
2.  Kliknij dwukrotnie linię, aby otworzyć **Edytor skojarzenia** okno dialogowe.  
  
3.  Usuń właściwość z **właściwości skojarzenia**.  
  
4.  Spróbuj ponownie usunąć właściwości.  
  
## <a name="see-also"></a>Zobacz także
[Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)