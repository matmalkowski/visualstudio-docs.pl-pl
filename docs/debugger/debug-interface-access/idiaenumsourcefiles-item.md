---
title: IDiaEnumSourceFiles::Item | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cb8172b36542d215502636c96126cae064b3b93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Pobiera plik źródłowy za pomocą indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 indeks  
 [in] Indeks o [idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md) obiektu do pobrania. Indeks znajduje się w zakresie od 0 do `count`-1, gdy `count` zwróconego przez [IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) metody.  
  
 sourceFile  
 [out] Zwraca [idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md) obiekt reprezentujący plik żądanego źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumsourcefiles —](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)