---
title: IActiveScript::GetCurrentScriptThreadID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5921dc4d0f9a9bf0d505fece0f47354cb16d440c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791749"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Pobiera identyfikator skryptów aparatu zdefiniowanych dla wątku aktualnie wykonywane. Identyfikator może być używany w kolejnych wywołaniach metod Kontrola wykonywania wątku skryptu takich jak [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstidThread`  
 [out] Adres zmiennej, która odbiera identyfikator wątku skryptu skojarzony z bieżącego wątku. Interpretacja ten identyfikator jest od lewej do aparatu skryptów, ale można ją po prostu kopię identyfikator wątku systemu Windows. Jeśli zakończenie wątku Win32, ten identyfikator staje się nieprzypisane i mogą być później przypisane do innego wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_POINTER` Jeśli określono nieprawidłowy wskaźnik.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może być wywołana z wątków innych niż podstawowe powodowała objaśnienia innych niż podstawowe do obiektów hosta lub do [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)