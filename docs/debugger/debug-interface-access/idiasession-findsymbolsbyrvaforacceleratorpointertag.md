---
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Dokumentacja firmy Microsoft
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
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2156aeec1f8e1b6b2f3670111946acf3e69392e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Biorąc pod uwagę odpowiadającą mu wartość tagu, ta metoda zwraca wyliczenie symboli, które są zawarte w funkcji stub akceleratora określonego elementu nadrzędnego pod określonym adresem względnym wirtualnego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 [in] `IDiaSymbol` Odpowiadającej funkcji stub klawiszy skrótów do wyszukania.  
  
 `tagValue`  
 [in] Wartość tagu wskaźnika.  
  
 `rva`  
 [in] Wirtualny adres względny.  
  
 `ppResult`  
 [out] Wskaźnik do `IDiaEnumSymbols` wskaźnika interfejsu, który został zainicjowany z wynikiem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Tę metodę można wywołać tylko w systemie `IDiaSymbol` interfejs, który odpowiada funkcja stub akceleratora.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)