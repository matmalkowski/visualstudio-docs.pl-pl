---
title: IActiveScript::GetScriptThreadID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8850319035b7b5e3a9cbbd4bbe4340e1eefacc96
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792004"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Pobiera identyfikator wątku skojarzone z danym wątku Win32 skryptów aparatu zdefiniowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwWin32ThreadID` ,  
 [in] Identyfikator wątku uruchomiony wątek Win32 w bieżącym procesie. Użyj [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) funkcji, aby pobrać identyfikator wątku aktualnie wykonywane wątku.  
  
 `pstidThread` ,  
 [out] Adres zmiennej, która odbiera identyfikator wątku skryptu, które są skojarzone z danym wątku Win32. Interpretacja ten identyfikator jest od lewej do aparatu skryptów, ale można ją po prostu kopię identyfikator wątku systemu Windows. Należy pamiętać, że jeśli zakończenie wątku Win32, ten identyfikator staje się nieprzypisane i później może być przypisana do innego wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować) i dlatego nie powiodła się.|  
  
## <a name="remarks"></a>Uwagi  
 Pobrano identyfikator może służyć w kolejnych wywołaniach metod kontroli wykonanie wątku skryptu takich jak [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) metody.  
  
 Ta metoda może być wywołana z wątków innych niż podstawowe powodowała objaśnienia innych niż podstawowe do obiektów hosta lub do [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)