---
title: Właściwość &lt;nazwa właściwości&gt; nie można usunąć, ponieważ uczestniczy w skojarzeniu &lt;Nazwa skojarzenia&gt; | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6983d52615219c386b049eea33f9f911956c6d59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682791"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Właściwość &lt;nazwa właściwości&gt; nie można usunąć, ponieważ uczestniczy w skojarzeniu &lt;Nazwa skojarzenia&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [właściwość &lt;nazwa właściwości&gt; nie można usunąć, ponieważ uczestniczy w skojarzeniu &lt;Nazwa skojarzenia&gt;](https://docs.microsoft.com/visualstudio/data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name).  
  
  
Wybrana właściwość jest ustawiona jako **właściwość skojarzenia** skojarzenia między klasami wskazanego w komunikacie o błędzie. Nie można usunąć właściwości, jeśli są one skojarzenia między klasami danych.  
  
 Ustaw **właściwość skojarzenia** różne właściwości klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Wybierz linię skojarzenia na O/R Designer, który nawiązuje połączenie klas danych wskazany w komunikacie o błędzie.  
  
2.  Kliknij dwukrotnie wiersz, aby otworzyć **Edytor skojarzeń** okno dialogowe.  
  
3.  Usuń właściwość z **właściwości skojarzenia**.  
  
4.  Ponownie spróbuj usunąć właściwość.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Porady: Tworzenie skojarzenia (Relacja) między LINQ to SQL klas (Projektant O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Wskazówki: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

