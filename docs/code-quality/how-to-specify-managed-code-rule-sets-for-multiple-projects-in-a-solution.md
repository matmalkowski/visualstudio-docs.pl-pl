---
title: "Porady: określanie zestawów reguł zarządzanego kodu dla wielu projektów w rozwiązaniu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b1434e095fbf5c20286626cdc4cdc96716f2b9e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Porady: określanie zestawów reguł zarządzanego kodu dla wielu projektów w rozwiązaniu
Domyślnie wszystkie projekty zarządzanego rozwiązania są przypisane Microsoft minimalna zalecana reguł analizy kodu *zestaw reguł*. Można zmienić zestawów reguł, które są przypisane do projektów rozwiązania w oknie dialogowym właściwości dla rozwiązania.  
  
> [!NOTE]
>  Domyślnie analizy kodu projektu nie jest uruchamiane jako kroku kompilacji. Aby włączyć analizę kodu na potrzeby kompilacji, zobacz [porady: Konfigurowanie analizy kodu dla zarządzanego kodu projektu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Aby określić zestaw reguł dla wielu projektów w rozwiązaniu do kodu zarządzanego  
  
1.  W [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]. [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], lub [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] Otwórz rozwiązanie.  
  
2.  Na **Analizuj** menu, kliknij przycisk **Konfigurowanie analizy kodu dla rozwiązania**.  
  
3.  Jeśli to konieczne, rozwiń węzeł **wspólne właściwości**, a następnie kliknij przycisk **ustawienia analizy kodu**.  
  
4.  Można określić zestawu reguł dla jednego lub więcej projektów.  
  
    -   Aby określić zestaw reguł dla pojedynczego projektu, kliknij nazwę projektu.  
  
    -   Aby określić zestawu reguł dla wielu projektów, przytrzymaj klawisz CTRL i kliknij nazwę projektu.  
  
    -   Aby określić wszystkie projekty w rozwiązaniu, przytrzymaj naciśnięty klawisz SHIFT, a następnie kliknij pozycję na liście projektu.  
  
5.  Kliknij przycisk **zestawu reguł** pole projektu i następnie kliknij polecenie Ustaw nazwę reguły chcesz zastosować.