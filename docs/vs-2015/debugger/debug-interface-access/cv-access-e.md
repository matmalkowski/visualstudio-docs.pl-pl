---
title: Cv_access_e — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5096c90727a1c8ffcf871853d1f59610a2baff37
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42673565"
---
# <a name="cvaccesse"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [cv_access_e —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/cv-access-e).  
  
Określa zakres widoczności (poziom dostępu), funkcji składowych i zmiennych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elementy  
 CV_private  
 Element członkowski ma prywatnie.  
  
 CV_protected  
 Element członkowski zabezpieczył dostępu.  
  
 CV_public  
 Element członkowski ma dostęp publiczny.  
  
## <a name="remarks"></a>Uwagi  
 `friend` Specyfikator dostępu nie jest uwzględniony w tym miejscu, ponieważ jest ona zwykle używana przez funkcje nieczłonkowskie, które mają dostęp do prywatnej i chronionych elementów klasy. Użyj [idiasymbol::get_symtag —](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metody do znalezienia symboli z `SymTagFriend` dostępu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol::get_access —](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)



