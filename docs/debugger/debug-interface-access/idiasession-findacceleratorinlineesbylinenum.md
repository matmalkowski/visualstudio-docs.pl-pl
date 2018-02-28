---
title: IDiaSession::findAcceleratorInlineesByLinenum | Dokumentacja firmy Microsoft
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
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 625c4368b1a05ae805a3df8cfe76574dfd332bb5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Zwraca wyliczenie symboli dla ramek wbudowanych, które odpowiadają na określoną lokalizacją źródłową.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 [in] `IDiaSymbol` Odpowiadającej funkcji stub skrótów, która musi być wyszukiwane.  
  
 `file`  
 [in] `IDiaSourceFile` Lokalizacji źródła.  
  
 `linenum`  
 [in] Numer wiersza w lokalizacji źródłowej.  
  
 `colnum`  
 [in] Numer kolumny lokalizacji źródła.  
  
 `ppResult`  
 [out] Wskaźnik do `IDiaEnumLineNumbers` wskaźnika interfejsu, który został zainicjowany z wynikiem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)