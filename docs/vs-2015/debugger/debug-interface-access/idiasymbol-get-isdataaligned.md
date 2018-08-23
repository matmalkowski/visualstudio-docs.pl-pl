---
title: Idiasymbol::get_isdataaligned — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isDataAligned method
ms.assetid: ddd11a41-6c00-4829-acf4-aa1ace8c21a7
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8a21774721b48d239d1d5851cf30c6accc0e304
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681551"
---
# <a name="idiasymbolgetisdataaligned"></a>IDiaSymbol::get_isDataAligned
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiasymbol::get_isdataaligned —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-isdataaligned).  
  
Pobiera flagę określającą, czy typ zdefiniowany przez użytkownika (UDT) została wyrównana do granicy niektóre pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT get_isDataAligned(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlag`  
 [out] Zwraca `TRUE` Jeśli UDT ma zostać wyrównane do pewnych granic pamięci; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest ustawiona zazwyczaj, gdy plik wykonywalny został skompilowany z wyrównanie danych innej niż domyślna. Na przykład, kompilator Microsoft C++ można zmienić wyrównanie danych przy użyciu opcji wiersza polecenia/ZP*#*, gdzie *#* jest wartością bajtu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|DIA SDK w wersji 8.0|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



