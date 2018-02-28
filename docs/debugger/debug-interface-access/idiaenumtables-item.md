---
title: IDiaEnumTables::Item | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fd0049e15f17d5dff58d35d4279bb0ab0673091e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Pobiera tabeli za pomocą indeksu lub name.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 [in] Indeks lub nazwę [idiatable —](../../debugger/debug-interface-access/idiatable.md) do pobrania. Jeśli variant liczba całkowita jest używany, musi być w zakresie od 0 do `count`-1, gdzie `count` jest zwracane przez [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) metody.  
  
 `table`  
 [out] Zwraca [idiatable —](../../debugger/debug-interface-access/idiatable.md) obiekt reprezentujący żądanej tabeli.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli jest określony wariant ciąg, ciąg nazwy określonej tabeli. Nazwa musi mieć jedną z nazw tabel, zgodnie z definicją w [— stałe (debugowania Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Przykład  
  
```C++  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumtables —](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiatable —](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Stałe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)