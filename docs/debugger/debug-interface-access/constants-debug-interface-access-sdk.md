---
title: Stałe (zestaw SDK dostępu do interfejsu debugowania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c77febb7ad9f41880fef604849af75aa065ff593
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458921"
---
# <a name="constants-debug-interface-access-sdk"></a>Stałe (Zestaw SDK dostępu do interfejsu debugowania)
Te stałych ciąg można używać do identyfikowania różnych sekcji pliku bazy danych (PDB) program debugowania za pośrednictwem DIA SDK.  
  
## <a name="constants"></a>Stałe  
 Poniżej są deklarowane jako makr C/C++.  
  
|Macro|Wartość|  
|-----------|-----------|  
|`DiaTable_Symbols`|L "Symbole"|  
|`DiaTable_Sections`|L "Sekcji"|  
|`DiaTable_SrcFiles`|L "SourceFiles"|  
|`DiaTable_LineNums`|L "LineNumbers"|  
|`DiaTable_SegMap`|L "SegmentMap"|  
|`DiaTable_Dbg`|L "Dbg"|  
|`DiaTable_InjSrc`|L "InjectedSource"|  
|`DiaTable_FrameData`|L "FrameData"|  
  
## <a name="example"></a>Przykład  
 Oto przykład przy użyciu jednej z tych symboli:  
  
```C++  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)