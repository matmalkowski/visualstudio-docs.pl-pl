---
title: IDiaSymbol::findInlineFramesByVA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 54295d3e-bbb6-4c10-ab9d-adcfc22b1f71
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 526c29ad7d3ebf0173133d4a480b1a07c7d6c68b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolfindinlineframesbyva"></a>IDiaSymbol::findInlineFramesByVA
Pobiera wyliczenie umożliwia klientowi iterację wszystkie ramki wbudowane na określony adres wirtualny (VA).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findInlineFramesByVA (   
   ULONGLONG         va,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `va`  
 [in] Określa adres jako VA.  
  
 `ppResult`  
 [out] Przechowuje `IDiaEnumSymbols` obiekt, który zawiera listę ramek, które są pobierane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)