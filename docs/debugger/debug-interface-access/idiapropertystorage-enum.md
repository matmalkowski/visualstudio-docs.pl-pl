---
title: IDiaPropertyStorage::Enum | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2f28e47ab15160aa9b9dfadbe039325e2f7ffa7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Pobiera moduł wyliczający dla właściwości w tym zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppenum`  
 [out] Zwraca `IEnumSTATPROPSTG` obiektu (w przestrzeni nazw Microsoft.VisualStudio.OLE.Interop) reprezentujący wyliczenie właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiapropertystorage —](../../debugger/debug-interface-access/idiapropertystorage.md)