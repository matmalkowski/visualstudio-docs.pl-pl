---
title: 'Porady: Wkrocz do usługi WCF | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c526490ec9a4b6fa76d485aa86e53b78efcead1e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472617"
---
# <a name="how-to-step-into-wcf-services"></a>Porady: usługi WCF krok po kroku
W [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], można przejść do usługi WCF. Jeśli usługa WCF jest w tej samej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania jako klient, naciśnij klawisz punktów przerwania wewnątrz usługi WCF.  
  
 Wykonywanie krok po kroku, aby pracować, mają debugowanie włączone w pliku Web.config lub app.config. Aby uzyskać informacje o tym, jak włączyć debugowanie i ograniczeń dotyczących Wkraczanie do usługi WCF, zobacz [ograniczenia debugowania WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Aby wkraczać do usługi WCF  
  
1.  Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania, które zawiera klienta WCF i projektów usług WCF.  
  
2.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt klienta WCF, a następnie kliknij przycisk **Ustaw jako projekt startowy**.  
  
3.  Włącz debugowanie w pliku app.config lub web.config. Aby uzyskać więcej informacji, zobacz [ograniczenia debugowania WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Ustaw punkt przerwania w lokalizacji w projektu klienta, w którym ma się rozpocząć wykonywanie krok po kroku. Zazwyczaj są to bezpośrednio przed wywołaniem usługi WCF.  
  
5.  Uruchom do punktu przerwania, a następnie rozpocznij wykonywanie krok po kroku. Debuger będzie automatycznie kroku w usłudze.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)   
 [Ograniczenia debugowania WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Porady: debugowanie hostowania samoobsługowego WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)