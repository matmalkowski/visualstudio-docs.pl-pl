---
title: IDiaEnumFrameData::frameByVA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51d526c1ba187720952208b9b015ca7bfc2776d3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Przywraca ramkę wirtualnego adresu (VA).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 virtualAddress  
 [in] VA ramki zainteresowań.  
  
 ramowe  
 [out] Zwraca [idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md) obiekt, który reprezentuje ramkę, która zawiera podany adres.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli dane ramki nie pasują pod określony adres. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumframedata —](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [Idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md)