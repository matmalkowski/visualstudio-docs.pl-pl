---
title: IDiaSession::findLinesByAddr | Dokumentacja firmy Microsoft
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
- IDiaSession::findLinesByAddr method
ms.assetid: 640403c0-14cf-403c-ad19-38b3bdc28ca8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e7a8fd6b98f6c92eb90c253917be2374c3195b9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindlinesbyaddr"></a>IDiaSession::findLinesByAddr
Pobiera wierszy w określonych compiland, które zawierają określony adres.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findLinesByAddr (   
   DWORD                 seg,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `seg`  
 [in] Określa składnik sekcji określonego adresu.  
  
 `offset`  
 [in] Określa przesunięcie składnik określonego adresu.  
  
 `length`  
 [in] Określa liczbę bajtów zakres adresów, aby pokrywał się z tym zapytaniem.  
  
 `ppResult`  
 [out] Zwraca [idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md) obiekt, który zawiera listę wszystkich linii numery ochrona ta określony zakres adresów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia funkcję, która uzyskuje wszystkie numery wierszy zawartych w funkcji za pomocą funkcji adres i długości.  
  
```C++  
IDiaEnumLineNumbers* GetLineNumbersByAddr(IDiaSymbol *pFunc,  
                                          IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    DWORD                seg;  
    DWORD                offset;  
    ULONGLONG            length;  
  
    if (pFunc->get_addressSection ( &seg ) == S_OK &&  
        pFunc->get_addressOffset ( &offset ) == S_OK)  
    {  
        pFunc->get_length ( &length );  
        pSession->findLinesByAddr( seg, offset, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)