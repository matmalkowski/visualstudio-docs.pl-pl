---
title: IDiaSymbol::get_acceleratorPointerTags | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24db7164335a8deffbac7cb4f62207a974f6efb9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460674"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Zwraca wszystkie akceleratora wskaźnika tagu wartości odpowiadających funkcji stub akceleratora C++ AMP.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cnt`  
 [in] Rozmiar tablicy danych wyjściowych `pPointerTags`.  
  
 `pcnt`  
 [out] Liczba tagów wskaźnika akceleratora w funkcji stub akceleratora C++ AMP.  
  
 `pPointerTags`  
 [out] A `DWORD` wskaźnik tablicy jest wypełniony wartości skrótów wskaźnika tagów w funkcji stub akceleratora C++ AMP.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana na `IDiaSymbol` interfejs, który odpowiada na funkcję stub akceleratora C++ AMP.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)