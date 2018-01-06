---
title: Aparat debugowania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 70e572b73f8474f77a17989c790f2e7336f9d7a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debug-engine"></a>Aparat debugowania
Aparat debugowania (DE) współpracuje z interpreter lub systemu operacyjnego w celu zapewnienia usług debugowania, takich jak wykonanie oceny kontroli, punkty przerwania i wyrażenia. Niemcy jest odpowiedzialny za monitorowanie stanu debugowany program. Aby to zrobić, DE używa, niezależnie od metody są dostępne w środowisku wykonawczym obsługiwanych, czy z Procesora lub interfejsów API dostarczonych przez środowisko uruchomieniowe.  
  
 Na przykład środowisko uruchomieniowe języka wspólnego (CLR) udostępnia mechanizmów monitorowania za pomocą interfejsów ICorDebugXXX uruchomiony program. Niemcy, która obsługuje środowisko CLR używa odpowiednich interfejsów ICorDebugXXX do śledzenia debugowany program kodu zarządzanego. Następnie komunikuje się zmiany stanu Menedżerowi sesji debugowania (SDM), która przekazuje takie informacje do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
> [!NOTE]
>  Aparat debugowania jest przeznaczony dla określonego środowiska uruchomieniowego, oznacza to, w którym program debugowany działa system. Środowisko CLR jest środowiska uruchomieniowego dla kodu zarządzanego i środowiska uruchomieniowego Win32 jest dla natywnych aplikacji systemu Windows. Jeśli jeden z tych dwóch środowisk uruchomieniowych celem może być język tworzenia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostarcza już aparatami debugowania konieczne. Musisz zaimplementować będzie ewaluatora wyrażeń.  
  
## <a name="debug-engine-operation"></a>Operacja aparat debugowania  
 Monitorowania usługi są implementowane za pośrednictwem interfejsów DE i może spowodować pakietu debugowania do przejścia między różne tryby operacyjne. Aby uzyskać więcej informacji, zobacz [tryby operacyjne](../../extensibility/debugger/operational-modes.md). Zazwyczaj jest tylko jedna implementacja DE na środowisko wykonawcze.  
  
> [!NOTE]
>  Gdy istnieją oddzielne implementacje DE języka Transact-SQL i [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript i [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] DE jednego udziału.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debugowanie umożliwia debugowanie aparaty na jeden z dwóch sposobów: w tym samym procesie co [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoki lub w tym samym procesie programu docelowego debugowania. Ostatni formularz zwykle występuje, gdy debugowany proces jest rzeczywiście interpreter do uruchamiania skryptu aparatu debugowania muszą znać jednorodnej interpretera aby skrypt monitorowania. Należy pamiętać, że w takim przypadku interpretera faktycznie runtime; aparaty debugowania są dla określonego środowiska uruchomieniowego implementacji. Ponadto implementacji pojedynczego DE może zostać podzielony przez granice procesu i komputera (na przykład debugowania zdalnego).  
  
 Ujawnia DE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania interfejsów. Cała komunikacja odbywa się za pośrednictwem modelu COM. Czy DE jest ładowany poza procesem lub na innym komputerze, nie dotyczy komunikacji.  
  
 DE współpracuje ze składnikiem ewaluatora wyrażenia umożliwiające DE dla tego konkretnego wykonywania zrozumienie składni wyrażeń. Niemcy współdziała również z symbol składnika obsługi dostępu do informacji debugowania symboliczne generowane przez kompilator języka. Aby uzyskać więcej informacji, zobacz [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md) i [dostawcy Symbol](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)   
 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md)   
 [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)