---
title: "Implementowanie obsługi polecenia zagnieżdżone projektów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4ed9efab34a51bdfaacea1773a33637437b2ced
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementowanie obsługi dla projektów zagnieżdżonego polecenia
IDE może przekazać poleceń, które są przekazywane za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsów zagnieżdżonych projektów lub projektów nadrzędnego mogą filtrować lub zastąpienie polecenia.  
  
> [!NOTE]
>  Można filtrować tylko polecenia zazwyczaj obsługiwane przez projekt nadrzędny. Polecenia takie jak **kompilacji** i **Wdróż** obsługi przez IDE nie mogą zostać odfiltrowane.  
  
 W poniższych krokach opisano proces wdrażania obsługi poleceń.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-implement-command-handling"></a>Aby zaimplementować obsługi polecenia  
  
1.  Gdy użytkownik wybierze projektu zagnieżdżonego lub węzła w projektu zagnieżdżonego:  
  
    1.  Wywołania IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody.  
  
     — lub —  
  
    1.  Jeśli polecenie pochodzi w oknie hierarchii, takie jak polecenie menu skrótów w Eksploratorze rozwiązań IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metody dla projektu nadrzędnego.  
  
2.  Projekt nadrzędny można sprawdzić parametry do przekazania do `QueryStatus`, takich jak `pguidCmdGroup` i `prgCmds`, aby ustalić, czy projekt nadrzędny powinny filtrowania poleceń. Jeśli projekt nadrzędny jest wdrażane do filtrowania poleceń, należy ustawić:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     Następnie projektu nadrzędnego powinien zwrócić `S_OK`.  
  
     Jeśli projekt nadrzędny filtra polecenia powinien on tylko zwrócić `S_OK`. W takim przypadku IDE automatycznie rozsyła polecenia do projektu podrzędnego.  
  
     Projekt nadrzędny nie ma do rozsyłania polecenia do projektu podrzędnego. IDE wykonuje to zadanie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Polecenia, menu i pasków narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Zagnieżdżanie projektów](../../extensibility/internals/nesting-projects.md)