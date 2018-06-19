---
title: IDiaSourceFile::get_compilands | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64e1d29f9f27dcbe2f85a7d9f4e015264d685be7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460700"
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