---
title: IDiaSession::findSymbolsForAcceleratorPointerTag | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7df83017e60a9d3600c7e49bcf888c771a748cee
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Zwraca wyliczenie symboli dla zmiennej, która odpowiada wartości określonego tagu w obiekcie nadrzędnym funkcja stub akceleratora.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 [in] Idiasymbol — umożliwiająca funkcja stub klawiszy skrótów do wyszukania.  
  
 `tagValue`  
 [in] Wartość tagu wskaźnika.  
  
 `ppResult`  
 [out] Wskaźnik do `IDiaEnumSymbols` wskaźnika interfejsu, który został zainicjowany z wynikiem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)