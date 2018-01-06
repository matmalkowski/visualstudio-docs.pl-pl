---
title: IDiaSymbol::findInlineeLinesByRVA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ac108db1-9dbf-4dc4-bf48-159ca8d3725c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bc9c5b87933940b2f1f98766c1fd477460bf18b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolfindinlineelinesbyrva"></a>IDiaSymbol::findInlineeLinesByRVA
Pobiera wyliczenie umożliwia klientowi iterację informacja o numerach wierszy wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w tym symbolu w ramach określonej wirtualnej adres względny (RVA).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findInlineeLinesByRVA (    DWORD                 rva,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rva`  
 [in] Określa adres co adres RVA.  
  
 `length`  
 [in] Określa zakres adresów w liczba bajtów, aby pokrywał się z tym zapytaniem.  
  
 `ppResult`  
 [out] Przechowuje `IDiaEnumLineNumbers` obiekt, który zawiera listę numerów wierszy, które są pobierane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [Idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)