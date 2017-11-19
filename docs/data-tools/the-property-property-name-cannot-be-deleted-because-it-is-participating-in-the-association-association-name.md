---
title: "Właściwość &lt;nazwa właściwości&gt; nie można usunąć, ponieważ uczestniczy ona w skojarzeniu &lt;Nazwa skojarzenia&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 150d176c105e8368fc97f36a19774824dcb91c3e
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
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
[Komunikaty Projektanta obiektów relacyjnych](../data-tools/o-r-designer-messages.md)  
[LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)