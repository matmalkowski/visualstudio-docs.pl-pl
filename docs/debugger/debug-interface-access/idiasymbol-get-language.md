---
title: IDiaSymbol::get_language | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_language method
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b17984e25da5812d60008f7a9b5291ce0cb703ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetlanguage"></a>IDiaSymbol::get_language
Pobiera języka źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_language (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca wartość z zakresu od [cv_cfl_lang — wyliczenie](../../debugger/debug-interface-access/cv-cfl-lang.md) wyliczenia, który określa języka źródłowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Cv_cfl_lang — wyliczenie](../../debugger/debug-interface-access/cv-cfl-lang.md)