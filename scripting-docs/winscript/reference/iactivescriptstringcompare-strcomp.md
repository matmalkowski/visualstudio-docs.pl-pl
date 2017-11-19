---
title: IActiveScriptStringCompare::StrComp | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptStringCompare.StrComp
apilocation: scrobj.dll
helpviewer_keywords: StrComp method, IActiveScriptStringCompare interface
ms.assetid: 124d1281-8037-4766-a2a1-61244ac1f114
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b92b29f4e40f5e8de567337957aabbcb3c057fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstringcomparestrcomp"></a>IActiveScriptStringCompare::StrComp
Definiuje metodę porównywania ciągów dla aparatu skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrComp(  
// The first string:  
    [in] BSTR bszStr1,    
// The second string:   
    [in] BSTR bszStr2,    
// The result of the comparison:  
    [out, retval] LONG* iRet   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bszStr1`  
 Pierwszy ciąg.  
  
 `bszStr2`  
 Drugi ciąg.  
  
 `iRet`  
 Wynik porównania. Jeśli 0 `bszStr1` i `bszStr2`są identyczne; -1 Jeśli `bszStr1`  <  `bszStr2`; 1, gdy `bszStr1`  >  `bszStr2`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument jest nieprawidłowy.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować).|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana zawsze, która jest wykonywana porównania ciągów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można przeciążyć funkcji porównanie ciągu. Przeciążanie jest dozwolone, gdy używasz [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) można ustawić SCRIPTPROP_STRINGCOMPAREINSTANCE.  
  
```cpp#  
cpp_quote("// {58562769-ED52-42f7-8403-4963514E1F11}")  
cpp_quote("DEFINE_GUID(IID_IActiveScriptStringCompare, 0x58562769,   
    0xED52, 0x42f7, 0x84, 0x03, 0x49, 0x63, 0x51, 0x4E, 0x1F, 0x11);")  
cpp_quote("")  
  
cpp_quote("#define SCRIPTPROP_INTEGERMODE              0x00003000")  
cpp_quote("#define SCRIPTPROP_STRINGCOMPAREINSTANCE    0x00003001")  
cpp_quote("")  
interface IActiveScriptStringCompare;  
[  
         object,  
         uuid(58562769-ED52-42f7-8403-4963514E1F11),  
         pointer_default(unique)  
]  
interface IActiveScriptStringCompare : IUnknown  
{  
        // StrComp  
        //     bszStr1: first string  
        //     bszStr2: second string  
        //     iRet: 0 if identical, -1 if bszStr1 < bszStr2, 1 if   
        //         bszStr1 > bszStr2  
        //            
        //     Return values:  
        //         S_OK: Success  
        //         E_NOTIMPL: Not implemented  
        //  
        HRESULT StrComp(  
                [in] BSTR bszStr1,  
                [in] BSTR bszStr2,  
                [out, retval] LONG* iRet  
        );  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md)