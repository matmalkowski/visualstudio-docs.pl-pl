---
title: IDiaSymbol::get_compilerGenerated | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_compilerGenerated method
ms.assetid: 864d9249-f0c8-4a34-b391-eb785f7e8865
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e239bd31126de7e36edd4fc6300cbdf4de8a6f85
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetcompilergenerated"></a>IDiaSymbol::get_compilerGenerated
Pobiera flagę wskazującą, czy symbol został wygenerowany przez kompilator.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_compilerGenerated (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca `TRUE` Jeśli kompilator, generowany symbol; w przeciwnym razie zwraca `FALSE` , jeśli symbol został wygenerowany na podstawie źródła zapisane przez użytkownika.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)