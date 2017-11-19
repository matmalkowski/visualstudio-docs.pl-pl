---
title: IDiaSymbol::get_sizeInUdt | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a82ab896-0185-46a4-b4d5-babfcc660fe1
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a78155a9c0456ea8bc8fd628a0edabe5c7fe4ba1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetsizeinudt"></a>IDiaSymbol::get_sizeInUdt
Pobiera informacje o rozmiarze elementu członkowskiego typu zdefiniowanego przez użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_sizeInUdt(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Wskaźnik do `DWORD` , który określa rozmiar elementu członkowskiego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)