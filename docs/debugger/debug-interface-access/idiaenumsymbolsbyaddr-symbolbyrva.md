---
title: IDiaEnumSymbolsByAddr::symbolByRVA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSymbolsByAddr::symbolByRVA method
ms.assetid: f7828029-f2ee-4ccd-afac-785adc60a4c8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d5a29f06cea1624b66dcd09ec78821446cce97b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumsymbolsbyaddrsymbolbyrva"></a>IDiaEnumSymbolsByAddr::symbolByRVA
Umieszcza modułu wyliczającego przez wykonywane jest wyszukiwanie przez wirtualny adres względny (RVA).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT symbolByRVA (   
   DWORD**      relativeVirtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 relativeVirtualAddress  
 [in] Adres względny na początek obrazu.  
  
 ppsymbol  
 [out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt reprezentujący symbol znaleziono.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie można odnaleźć symbolu. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumsymbolsbyaddr —](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)