---
title: IDiaEnumSymbolsByAddr::symbolByVA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByVA method
ms.assetid: ac84339f-70c6-48ed-85d0-6d7d1b5194e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a47c39a417e65d30178a2f878e53196e7f7fb27
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsymbolsbyaddrsymbolbyva"></a>IDiaEnumSymbolsByAddr::symbolByVA
Umieszcza modułu wyliczającego przez wykonywane jest wyszukiwanie w wirtualnym adresie (VA).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT symbolByVA (   
   DWORD**      virtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 virtualAddress  
 [in] Wirtualny adres.  
  
 ppsymbol  
 [out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt reprezentujący symbol znaleziono.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie można odnaleźć symbolu. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumsymbolsbyaddr —](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)