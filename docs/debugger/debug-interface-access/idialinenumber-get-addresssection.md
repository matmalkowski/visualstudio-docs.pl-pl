---
title: IDiaLineNumber::get_addressSection | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLineNumber::get_addressSection method
ms.assetid: a01c1bae-04b2-4c30-8621-60939a3124c2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 302ee0d1223b6f1b922a2e949f36f2a14d6890e8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idialinenumbergetaddresssection"></a>IDiaLineNumber::get_addressSection
Pobiera część sekcji adres pamięci, w którym rozpoczyna się blok.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pRetVal  
 [out] Zwraca sekcji część adres pamięci, w którym rozpoczyna się bloku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
  
```C++  
CComPtr< IDiaLineNumber > pLine;  
DWORD seg;  
pLine->get_addressSection( &seg );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idialinenumber —](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaLineNumber::get_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)