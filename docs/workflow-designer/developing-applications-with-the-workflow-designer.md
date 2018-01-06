---
title: "Tworzenie aplikacji za pomocą projektanta przepływów pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: "17"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 61d58b172c185a908a6314664ccd4cfe2172dc8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="developing-applications-with-the-workflow-designer"></a>Tworzenie aplikacji za pomocą projektanta przepływów pracy
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] Jest widoczny Projektant wizualny oraz debugera dla konstrukcji graficznego i debugowanie [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacji w [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] jest hostowana w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] Środowisko deweloperskie. Umożliwia utworzenie aplikacji złożonych przepływu pracy, biblioteka działań lub [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usługi przy użyciu szablonów i projektantów działań. [!INCLUDE[crabout](../test/includes/crabout_md.md)]przepływy pracy, zobacz [Windows Workflow Foundation &#91;. NET Framework 4 &#93; ](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
 Poniżej przedstawiono kilka nowych funkcji projektowania, które ustawić tej nowej wersji [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] oprócz starsze wersje [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]:  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Jest utworzony przy użyciu [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]. Podnosi poziom obsługi projektanta działania i zwiększa wydajność w przypadku dużych i złożonych przepływów pracy.  
  
-   Działania niestandardowe są wyposażone [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], przy użyciu języka XAML i modelu programowania do tworzenia projektantów działań zostały uproszczone.  
  
-   Działanie flowchart został zaimplementowany, więc można zwizualizować przepływem programu przy użyciu znanych schemat blokowy modelowania stylu.  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Ma nowej zmiennej projektanta umożliwiający deklarowanie i zakres zmiennych w ramach przepływów pracy, powiązanie ich działania.  
  
-   W [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] zapewnia pełne możliwości funkcji IntelliSense, podczas tworzenia wyrażenia języka Visual Basic w ramach Twojej [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] przepływów pracy.  
  
-   Działanie debugowania została rozszerzona w języku XAML, dzięki czemu można ustawić punktów przerwania w definicji przepływu pracy XAML i Wkrocz do kodu XAML w czasie wykonywania, która zapewnia środowisko, podobnie jak w kodzie zarządzanym.  
  
-   Rehosting [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] została uproszczona znacznie w porównaniu z poprzednimi wersjami, teraz wymagające tylko kilka wierszy kodu.  
  
-   Nowy <xref:System.Activities.Statements.Flowchart> działanie i jego [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) pozwala na wizualizowanie z przepływem programu przy użyciu znanych schemat blokowy modelowania stylu.  
  
-   Zostały rozszerzone działania obsługi wiadomości, co umożliwia zapis w pełni deklaracyjnego (Brak kodu) [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usług.  
  
-   **Dodać odwołania do usługi...**  funkcjonalność umożliwia generowanie działania automatycznie uzyskiwać dostęp do usług sieci Web.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie projektanta przepływu pracy](../workflow-designer/using-the-workflow-designer.md)  
 Przedstawia sposób tworzenia nowych działań i projektów przepływu pracy przy użyciu wbudowanych projektantów i obsługę argumenty, zmienne wyrażeń, importowania i nadrzędnych przy użyciu innych narzędzi dostarczonych przez projektanta.  
  
 [Używanie projektantów działań](../workflow-designer/using-the-activity-designers.md)  
 Opis kategorii działań i szablonów ich projektantów, które są dostarczane przez system.  
  
 [Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Opisano sposób wykonywania tradycyjnych debugowanie procedur, a także debugowanie XAML i wyrażenia.  
  
 [Pomoc interfejsu użytkownika Projektanta przepływu pracy](../workflow-designer/workflow-designer-ui-help.md)  
 Zawiera tematy pomocy kontekstowej dla okien dialogowych udostępniane przez [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], oraz wskazówki dotyczące funkcji powłoki projektanta, skróty klawiaturowe i komunikaty o błędach.  
  
 [Opracowywanie aplikacji przepływu pracy przeznaczonych dla platformy .NET 3.0 lub .NET 3.5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Zawiera wskazówki dotyczące przy użyciu narzędzia Projektant starszej wersji, którego celem jest [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [Projektant ReHosting &#91; WF — przykłady &#93;](http://msdn.microsoft.com/Library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 W tym przykładzie przedstawiono sposób tworzenia układu WPF zawiera projektanta.  
  
 [Projektanci działań niestandardowych](/dotnet/framework/windows-workflow-foundation/samples/custom-activity-designers)  
 Ta sekcja zawiera przykłady działania, które Użyj niestandardowych projektantów do wyświetlenia w Projektancie przepływów pracy.