---
title: 'Porady: Tworzenie skojarzenia (Relacja) między LINQ to SQL klas (Projektant O-R) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14b60094150467aeda7641d018e06db15e7bda03
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42627959"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Porady: Tworzenie skojarzenia (Relacja) między LINQ to SQL klas (Projektant O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Tworzenie skojarzenia (Relacja) między LINQ to SQL klas (Projektant O-R)](https://docs.microsoft.com/visualstudio/data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer).  
  
  
Skojarzenia między klasami jednostki w [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] są analogiczne do relacji między tabelami w bazie danych. Można utworzyć skojarzenia między klasami jednostki przy użyciu **Edytor skojarzeń** okno dialogowe.  
  
 Gdy używasz należy wybrać klasy nadrzędnej i podrzędnej klasy **Edytor skojarzeń** okno dialogowe, aby utworzyć skojarzenie. Klasa nadrzędna jest klasa jednostki, który zawiera klucz podstawowy; Klasa potomna jest klasa jednostki, która zawiera klucz obcy. Na przykład jeśli klas jednostek zostały utworzone mapowane na tabele Northwind Customers i Orders, klasa klienta będzie klasy nadrzędnej i klasa kolejności będą klasy podrzędnej.  
  
> [!NOTE]
>  Podczas przeciągania tabel z **Eksploratora serwera**/**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), skojarzenia są automatycznie tworzone w oparciu o istniejące relacje klucza obcego w bazie danych.  
  
 Po utworzeniu skojarzenia, po wybraniu skojarzenie O/R Designer, istnieje kilka właściwości możliwych do skonfigurowania w **właściwości** okna. (Skojarzenie jest wiersz między powiązanymi klasami). Poniższa tabela zawiera opis właściwości skojarzenia.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Kardynalność**|Określa, czy skojarzenie jest jeden do wielu lub jeden do jednego.|  
|**Właściwości elementu podrzędnego**|Określa, czy ma być utworzona właściwość kolekcji lub odwołanie do rekordów podrzędnych po stronie klucza obcego skojarzenia obiektu nadrzędnego. Na przykład w przypadku skojarzenia między klienta i zamówienia Jeśli **właściwości elementu podrzędnego** ustawiono **True**, właściwość o nazwie zamówienia jest tworzona w klasie nadrzędnej.|  
|**Właściwość nadrzędna**|Właściwość klasy podrzędnej, przywołującej skojarzoną klasę nadrzędną. Na przykład do skojarzenia między klienta i zamówienia właściwość o nazwie klienta, który odwołuje się do skojarzonych klientów dla zamówienia jest tworzony w klasie kolejności.|  
|**Właściwości uczestniczące**|Wyświetla właściwości skojarzenia oraz **wielokropka** przycisku (...), który otwiera ponownie **Edytor skojarzeń** okno dialogowe.|  
|**unikatowe**|Określa, czy obce kolumny docelowe mają ograniczenie unikatowości.|  
  
### <a name="to-create-an-association-between-entity-classes"></a>Aby utworzyć skojarzenie między klasami jednostki  
  
1.  Kliknij prawym przyciskiem myszy klasę jednostki, która reprezentuje klasa nadrzędna do skojarzenia, wskaż opcję **Dodaj**, a następnie kliknij przycisk **skojarzenie**.  
  
2.  Sprawdź, czy poprawny **klasy nadrzędnej** wybrano **Edytor skojarzeń** okno dialogowe.  
  
3.  Wybierz **klasy podrzędnej** w polu kombi.  
  
4.  Wybierz **właściwości skojarzenia** powiązanych klas. Zwykle to mapuje relacji klucza obcego w bazie danych. Na przykład w powiązaniu klienci i zamówienia **właściwości skojarzenia** są CustomerID dla każdej klasy.  
  
5.  Kliknij przycisk **OK** utworzyć skojarzenie.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Wskazówki: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Instrukcje: Reprezentacja kluczy podstawowych](http://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)

