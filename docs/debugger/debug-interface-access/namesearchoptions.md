---
title: "Namesearchoptions — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ceadd085a3099721e73e04dd09ea5a0b81ad1d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="namesearchoptions"></a>NameSearchOptions
Określa opcje wyszukiwania dla nazwy symbolu i plików.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>Elementy  
 `nsNone`  
 Nie określono opcji.  
  
 `nsfCaseSensitive`  
 Stosuje musi odpowiadać nazwie z uwzględnieniem wielkości liter.  
  
 `nsfCaseInsensitive`  
 Stosuje musi odpowiadać nazwie bez uwzględniania wielkości liter.  
  
 `nsfFNameExt`  
 Traktuje jako ścieżki nazwy i stosuje nazwa_pliku.ext musi odpowiadać nazwie.  
  
 `nsfRegularExpression`  
 Stosuje dopasowania z uwzględnieniem wielkości liter nazwy za pomocą gwiazdki (*) i znaki zapytania (?) jako symboli wieloznacznych.  
  
 `nsfUndecoratedName`  
 Dotyczy tylko symbole, które mają zarówno bez i nazwy ozdobione.  
  
## <a name="remarks"></a>Uwagi  
 Wartości z tego wyliczenia są przekazywane do następujących metod:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)