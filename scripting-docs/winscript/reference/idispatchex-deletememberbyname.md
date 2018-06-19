---
title: IDispatchEx::DeleteMemberByName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb9a9dfd979954c42101fde41819d7e12db59e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794593"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Usuwa element członkowski o nazwie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrName`  
 Nazwa elementu członkowskiego do usunięcia.  
  
 `grfdex`  
 Określa, czy nazwa elementu członkowskiego jest uwzględniana wielkość liter. Może to być jedna z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|fdexNameCaseSensitive|Żądania, które wyszukiwanie nazw odbywać się w sposób, z uwzględnieniem wielkości liter. Można zignorować przez obiekt, który nie obsługuje wyszukiwania z uwzględnieniem wielkości liter.|  
|fdexNameCaseInsensitive|Żądania, które wyszukiwanie nazw odbywać się w sposób bez uwzględniania wielkości liter. Może być ignorowane przez obiekt, który nie obsługuje wyszukiwania bez uwzględniania wielkości liter.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|`S_FALSE`|Element członkowski istnieje, ale nie można go usunąć.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli element członkowski zostanie usunięty, identyfikator DISPID musi są ważne `GetNextDispID`.  
  
 Jeśli element członkowski o podanej nazwie zostanie usunięty, a później zostaje odtworzone element członkowski o takiej samej nazwie, identyfikator DISPID powinna być taka sama. (Czy elementy członkowskie, które różnią się tylko wielkością liter są "same" jest zależny od obiektu).  
  
## <a name="example"></a>Przykład  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispatchEx](../../winscript/reference/idispatchex-interface.md)