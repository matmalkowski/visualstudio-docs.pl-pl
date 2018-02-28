---
title: IDiaSourceFile::get_compilands | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e393b4c40a780066b68819af4cbec9bb4765c4c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasourcefilegetcompilands"></a>IDiaSourceFile::get_compilands
Pobiera moduł wyliczający jednostki kompilacji, które mają numery wierszy odwołujące się do tego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_compilands (   
   IDiaEnumSymbols** ppRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppRetVal`  
 [out] Zwraca [idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md) obiekt, który zawiera listę wszystkich jednostki kompilacji, które mają numery wierszy odwołujące się do tego pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)