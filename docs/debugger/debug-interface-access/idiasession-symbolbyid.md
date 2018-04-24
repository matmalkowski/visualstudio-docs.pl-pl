---
title: IDiaSession::symbolById | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55e5e2815985aacd43603d24f1c6f4052b66c19c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Pobiera symbol przez jego unikatowy identyfikator.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [in] Unikatowy identyfikator.  
  
 `ppSymbol`  
 [out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) pobrać obiekt reprezentujący symbol.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Określony identyfikator jest używana wewnętrznie przez DIA SDK, aby zapewnić, że wszystkie symbole unikatowy unikatową wartość.  
  
 Ta metoda może służyć, na przykład można pobrać symbol reprezentujący typ symbolu innego (Zobacz przykład).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pobierana [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) reprezentujący typ symbolu innego. Ten przykład przedstawia sposób użycia `symbolById` metody w sesji. Prostsze jest wywołanie [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) metodę, aby bezpośrednio pobrać symbol typu.  
  
```C++  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)