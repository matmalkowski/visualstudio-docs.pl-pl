---
title: CONNECTION_PROTOCOL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONNECTION_PROTOCOL
helpviewer_keywords: CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 498090c71abb41fa7b0837bd608715db30df5e86
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Określa protokół używany do komunikacji między serwerem debugowania i pakietu debugowania (DE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 CONNECTION_NONE  
 Połączenie nie zostało ustanowione na serwerze.  
  
 CONNECTION_UNKNOWN  
 Wprowadzono połączenie, ale jest nieznanego typu.  
  
 CONNECTION_LOCAL  
 Połączenie jest na serwerze lokalnym.  
  
 CONNECTION_PIPE  
 Połączenie jest użycie nazwanego potoku.  
  
 CONNECTION_TCPIP  
 Połączenie wykorzystuje protokół TCP/IP.  
  
 CONNECTION_HTTP  
 Połączenia z użyciem protokołu HTTP (przez serwer sieci Web).  
  
 CONNECTION_OTHER  
 Ustanowiono innego typu połączenia (Ta wartość nie jest obecnie używany).  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są zwracane z [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)