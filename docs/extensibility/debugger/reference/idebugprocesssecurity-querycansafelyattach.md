---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe132ddbd154e04e3cef1a20e826c3634c65bdb2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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