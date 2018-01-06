---
title: "Obiekty, są dodawane do projektanta używają innego połączenia danych, niż aktualnie używa projektanta | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 715bb696819af901c04fc0d95747b51186868003
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Obiekty, które są dodawane do projektanta, użyj innego połączenia danych niż aktualnie używa narzędzia Projektant
Obiekty, które są dodawane do projektanta Użyj innego połączenia danych niż aktualnie używa projektanta. Czy chcesz zastąpić połączenie używane przez projektanta?  
  
 Po dodaniu elementów do [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), wszystkie elementy korzystały z jednego połączenia danych udostępnionych. (Powierzchni projektowej reprezentuje <xref:System.Data.Linq.DataContext>, który używa pojedynczego połączenia dla wszystkich obiektów na powierzchni.) Jeśli obiekt zostanie dodany do projektanta, który korzysta z połączenia danych, która różni się od połączenia danych aktualnie używane przez projektanta, zostanie wyświetlony ten komunikat. Aby rozwiązać ten problem, można zachować istniejące połączenie. Jeśli ta opcja, nie można dodać wybranego obiektu. Alternatywnie można dodać obiektu i zresetuj <xref:System.Data.Linq.DataContext> połączenia do nowego połączenia.  
  
> [!NOTE]
>  Jeśli klikniesz przycisk **tak**, klas wszystkie jednostki na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] są mapowane na nowe połączenie.  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Aby zastąpić istniejące połączenie połączenie używane przez wybrany obiekt  
  
-   Kliknij przycisk **Tak**.  
  
     Wybrany obiekt jest dodawany do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], a DataContext.Connection jest ustawiona na nowe połączenie.  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Aby nadal korzystać z istniejącego połączenia i Anuluj dodawanie wybranego obiektu  
  
-   Kliknij przycisk **nr**.  
  
     Akcja została anulowana. Ustaw pozostaje DataContext.Connection do istniejącego połączenia.  
  
## <a name="see-also"></a>Zobacz także
[Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
 