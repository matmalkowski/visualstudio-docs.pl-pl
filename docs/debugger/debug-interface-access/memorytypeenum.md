---
title: Memorytypeenum — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 616bae99a4cb3ffafa4cdf773bce63576ed04e7a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Określa typ pamięci, aby uzyskać dostęp.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `MemTypeCode`  
 Uzyskuje dostęp do kodu tylko pamięci.  
  
 `MemTypeData`  
 Uzyskuje dostęp do danych lub stosu pamięci.  
  
 `MemTypeStack`  
 Dostęp tylko stosu pamięci.  
  
 `MemTypeAny`  
 Uzyskuje dostęp do dowolnego rodzaju pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są przekazywane do [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) metodę, aby ograniczyć dostęp do różnych rodzajów pamięci.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)