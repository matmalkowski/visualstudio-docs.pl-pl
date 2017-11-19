---
title: "Porady: tłumienie ostrzeżeń przy użyciu elementu Menu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a197170285a8f8a9d3f0cc01638557f30fd1f126
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Porady: tłumienie ostrzeżeń przy użyciu elementu menu
> [!NOTE]
>  W źródle pomijania nie jest obsługiwane dla projektów witryny sieci web.  
  
 Okno Analiza kodu pomijanie ostrzeżeń analizy kodu. Pomijanie ostrzeżenie nie jest taka sama jak wyłączenie go. Ostrzeżenie można pominąć, zastosowanie tylko do konkretnego wystąpienia naruszenia. Inne naruszeń tej samej ostrzeżenie nadal będą raportowane w oknie Lista błędów.  
  
 Po uruchomieniu analizy kodu może określić, że co najmniej jeden ostrzeżenia analizy kodu, które są wyświetlane w oknie analizy kodu nie mają zastosowania do aplikacji. Na przykład określić, że kod jest prawidłowe, ponieważ jest. Lub może to oznaczać, że niektóre naruszeń są o niskim priorytecie, a nie zostanie rozwiązany w bieżącym cyklu tworzenia. Niezależnie od przyczyny warto często oznaczać, że nie dotyczy aby umożliwić członkom zespołu dowiedzieć się, że zostało sprawdzone kod i ustalenie, czy można pominąć to ostrzeżenie jest ostrzeżenie. W źródle pomijania jest przydatne, ponieważ pozwala umieścić pominięcie bliski gdzie to ostrzeżenie jest generowany.  
  
 Można wybrać, czy pomijanie pojawi się w kodzie źródłowym lub w pliku pominięć globalnych. Niektóre pominięć muszą znajdować się w pliku pominięć globalnych. Jeśli tak, jest **źródła w** opcja zostanie wyłączona.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Aby pominąć ostrzeżenie przy użyciu elementu menu  
  
1.  Na **Analizuj** menu, wybierz **Windows** , a następnie wybierz **analizy kodu**.  
  
2.  W **analizy kodu** okna, wybierz opcję Pomiń ostrzeżenie.  
  
3.  Wybierz akcje, a następnie wybierz **Pomiń komunikaty**i wybrać opcję **źródła w** lub **w pliku pominięć projektu**.  
  
     Określone ostrzeżenia jest pomijane, a ostrzeżenie jest wyświetlane w oknie analizy kodu jako przekreślona.  
  
> [!NOTE]
>  Ograniczeń, które nie mają obiektu docelowego pojawiają się w pliku pominięć globalnych.