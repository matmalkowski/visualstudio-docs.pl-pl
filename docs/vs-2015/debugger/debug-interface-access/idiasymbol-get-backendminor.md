---
title: Idiasymbol::get_backendminor — | Dokumentacja firmy Microsoft
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
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3169318bc1f73a8e23e0b4f72f1683a23e8b99c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682756"
---
# <a name="idiasymbolgetbackendminor"></a>IDiaSymbol::get_backEndMinor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiasymbol::get_backendminor —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-backendminor).  
  
Pobiera zaplecza pomocniczy numer wersji kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca numer wersji pomocniczej zaplecza. Zobacz uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Kompilatora zwykle składa się z dwóch podstawowe elementy: fronton (analizatora), która obsługuje analizowania kodu źródłowego w formie pośredniego, i zapleczem (generator kodu) konwertująca pośrednich formularza do zestawu. Nie jest niczym niezwykłym frontonu do innej wersji niż zaplecza.  
  
 Frontonu lub zaplecza numer wersji składa się z trzech części: \<główna >.\< pomocnicza >. \<kompilacji >, gdzie \<główne > jest główny numer wersji, \<pomocnicza > jest numerem wersji pomocniczej i \<kompilacji > jest numerem kompilacji. Na przykład 13.10.3077.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



