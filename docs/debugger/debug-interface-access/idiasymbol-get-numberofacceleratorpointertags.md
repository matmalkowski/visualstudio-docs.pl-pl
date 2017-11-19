---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4d7145903269822fbc67d0894cbbea1530044e4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Zwraca liczbę tagów wskaźnika akceleratora w funkcji stub C++ AMP.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 [out] Wskaźnik do `DWORD` przechowuje tagi wskaźnika liczbę klawiszy skrótów w funkcji stub C++ AMP.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana na `IDiaSymbol` interfejs, który odpowiada na funkcję stub akceleratora C++ AMP.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)