---
title: IDebugPortRequest2::GetPortName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff9ff4fb0a682b378bd35406f8e196d6b6c8a61e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630041"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugPortRequest2::GetPortName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportrequest2-getportname).  
  
Pobiera nazwę portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrPortName`  
 [out] Zwraca nazwę portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interfejsu jest zwykle przekazywany z pakietu debugowania (klienta) do dostawcy portu (serwera), można uzyskać połączenia do portu. Zarówno pakietu debugowania, jak i dostawcy portu sobie sprawę z możliwych opcji dla portu. Jeśli prosty ciąg opisujący portu, a następnie `IDebugPortRequest2::GetPortName` metoda ma za mało informacji do nawiązania połączenia. W przeciwnym razie można podać dodatkowe interfejsy przez klienta, który można uzyskać za pomocą serwera `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)

