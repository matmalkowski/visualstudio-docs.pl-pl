---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ad6b7ffde868bf6b9dc4f9ef3bab9d9094ab765
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Ta metoda umożliwia dostawcy portu można wyświetlić ostrzeżenie przed użytkownika dołącza do procesu niebezpieczne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartości zwracane są następujące:  
  
-   `S_OK`: Dołączanie do procesu jest bezpieczne i nie okno dialogowe ostrzeżenia jest wyświetlany.  
  
-   `S_FALSE`: Dołączanie może być problem z zabezpieczeniami i jest wyświetlane okno dialogowe z ostrzeżeniem.  
  
-   `FAILURE`: Dołączanie do procesu nie powiodło się.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)