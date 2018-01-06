---
title: "Ostrzeżenia przenośności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: efd2d56700c70b27771623e618f61675b174da01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="portability-warnings"></a>Ostrzeżenia przenośności
Ostrzeżenia przenośności obsługuje przenośność w różnych systemach operacyjnych.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Reguła|Opis|  
|----------|-----------------|  
|[CA1900: Pola typu wartości powinny być przenośne](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Ta reguła sprawdza, czy struktur, które są zadeklarowane za pomocą atrybutu układ jawny są wyrównane prawidłowo po przekazywane do kodu niezarządzanego na 64-bitowych systemach operacyjnych.|  
|[CA1901: Deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Ta zasada oblicza rozmiar każdego parametru i wartość zwracaną P/Invoke i weryfikuje, czy ich rozmiar jest prawidłowa, gdy są przekazywane do kodu niezarządzanego w 32-bitowych i 64-bitowych systemach operacyjnych.|  
|[CA1903: Używaj tylko interfejsu API platformy docelowej](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Element członkowski lub typ używa elementu członkowskiego lub typu wprowadzonego w dodatku Service Pack, który nie został uwzględniony razem ze wskazanym środowiskiem docelowym projektu.|