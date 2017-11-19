---
title: IDebugApplication::AddStackFrameSniffer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.AddStackFrameSniffer
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89faa6481bd5e5934ae2d3b85a0bade83949633a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Dodaje dostawcę modułu wyliczającego ramki stosu w tej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdsfs`  
 [in] Dostawca modułu wyliczającego ramki stosu do dodania do tej aplikacji.  
  
 `pdwCookie`  
 [out] Plik cookie, który służy do usuwania tego dostawcy modułu wyliczającego ramki stosu z aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Chociaż język aparaty zwykle wywołać tę metodę do udostępnienia ich ramek stosu do debugera, możliwe jest dla innych jednostek do udostępnienia ramki stosu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [Interfejs IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)