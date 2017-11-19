---
title: "Cv_access_e — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6112c72836c718dbd97ddfb62504186fdcf6ca33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="cvaccesse"></a>CV_access_e
Określa zakres funkcji Członkowskich i zmiennych widoczności (poziom dostępu).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elementy  
 CV_private  
 Element członkowski ma prywatny dostęp.  
  
 CV_protected  
 Element członkowski zabezpieczył dostępu.  
  
 CV_public  
 Element członkowski ma dostęp publiczny.  
  
## <a name="remarks"></a>Uwagi  
 `friend` Specyfikator dostępu nie jest dołączana w tym miejscu, ponieważ zwykle jest on używany przez funkcje niebędący elementem członkowskim, które mają dostęp do prywatnych i chronionych elementów klasy. Użyj [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metody do znalezienia symbole z `SymTagFriend` dostępu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)