---
title: "Obsługa usługi języka dla debugowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 955c8fd4e9499fbacfc0f97ba6112803ef1e6d4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="language-service-support-for-debugging"></a>Obsługa usługi języka do debugowania
Usługa języka zapewniają funkcje, które obsługują debugera za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfejsu. Te funkcje obejmują sprawdzanie poprawności punktów przerwania i dostarczenie lista wyrażeń w celu **automatycznych** okna.  
  
 Jednak należy mieć ewaluatora wyrażeń debugowania języka. Ewaluator wyrażeń jest odpowiedzialny za obliczenia wyrażenia w celu utworzenia wartości podczas debugowania. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR zobacz:  
  
-   [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Przykładowe ewaluatora wyrażenia zarządzanych](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Dane wyjściowe kompilatora  
 Typ kompilatora Określa, co należy zrobić, aby zaimplementować debugowania dla danego języka. Jeśli Twoje kompilatora jest przeznaczony dla systemu operacyjnego Windows i zapisuje plik PDB można debugować programy z kodu natywnego, debugowania aparatem, który jest zintegrowany z programu Visual Studio. Jeśli Twoje kompilatora języka pośredniego firmy Microsoft (MSIL), można debugować programy z zarządzanym kodem debugowania aparat, który również jest zintegrowany z programu Visual Studio. Jeśli kompilujący celem własny system operacyjny lub innego środowiska, należy napisać aparat debugowania.  
  
 Aby uzyskać więcej informacji dotyczących wdrażania debugowania dla danego języka, zobacz [wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) w Visual Studio SDK debugowania.