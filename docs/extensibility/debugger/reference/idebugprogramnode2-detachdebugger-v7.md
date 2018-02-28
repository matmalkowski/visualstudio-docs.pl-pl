---
title: IDebugProgramNode2::DetachDebugger_V7 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: af2f9e5851e53c86fb5466e7fc2cdfe515b5fb21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
PRZESTARZAŁE. NIE UŻYWAJ.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja zawsze powinna zwrócić `E_NOTIMPL`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!WARNING]
>  Począwszy od programu [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], ta metoda nie jest już używany i powinien zawsze zwracają `E_NOTIMPL`.  
  
 Ta metoda jest wywoływana, gdy debuger jest nieoczekiwanie zamykany. Gdy ta metoda jest wywoływana, DE powinien wznowić program tak, jakby użytkownik odłączyć od niego. Powinny być przesyłane bez więcej zdarzeń debugowania. Program powinien być w stanie, w których jest możliwe do dołączenia z innego wystąpienia debugera.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)