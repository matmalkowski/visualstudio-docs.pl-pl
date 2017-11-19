---
title: "Instrukcja ForEach&lt;T&gt; Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecfdc4d736f2be4ba4a8810b039ac11c88228160
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="foreachlttgt-activity-designer"></a>Instrukcja ForEach&lt;T&gt; Projektant działań
<xref:System.Activities.Statements.ForEach%601> Działania wykonuje działania zawarte w jego <xref:System.Activities.Statements.ForEach%601.Body%2A> dla każdego elementu w określonej <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekcji.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>Instrukcja ForEach < T\> właściwości w Projektancie przepływów pracy  
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.ForEach%601> właściwości działania i informacje dotyczące używania ich w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.ForEach%601> działania. Wartość domyślna to ForEach < Int32\>. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Wartość true|Kolekcja elementów w celu wykonania iteracji. Aby ustawić <xref:System.Activities.Statements.ForEach%601.Values%2A>, wpisz [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wyrażenie w **wartości** polu na **ForEach < T\>**  działania projektanta lub w siatce właściwości.|  
|*Elementu TypeArgument*|Wartość true|Typ elementów w <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekcji określonej przez parametr ogólny *T*. Domyślnie *elementu TypeArgument* ustawiono **Int32**. Aby zmienić typ, zmień wartość *elementu TypeArgument* pola kombi w siatce właściwości.|  
  
 Domyślnie, nosi nazwę sterująca pętli **elementu**. Można zmienić nazwę zmiennej iteracyjnej w <xref:System.Activities.Statements.ForEach%601> Projektant działań. Sterująca pętli można używać w wyrażeniach w elementów podrzędnych <xref:System.Activities.Statements.ForEach%601> działania.  
  
## <a name="see-also"></a>Zobacz też  
 [Działania ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)