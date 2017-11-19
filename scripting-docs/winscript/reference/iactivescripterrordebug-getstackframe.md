---
title: IActiveScriptErrorDebug::GetStackFrame | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptErrorDebug.GetStackFrame
apilocation: jscript.dll
helpviewer_keywords: IActiveScriptErrorDebug::GetStackFrame
ms.assetid: a6f43102-68c5-46f5-a4df-fa3aaf53a967
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: affb385f2c057b7ac69b56d1e8b8c22d7391e43f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrordebuggetstackframe"></a>IActiveScriptErrorDebug::GetStackFrame
Udostępnia ramki stosu, które są włączone dla błędów czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStackFrame(  
   IDebugStackFrame**  ppdsf  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppdsf`  
 [out] Ramki stosu tego błędu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia ramki stosu, które są włączone dla błędów czasu wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)