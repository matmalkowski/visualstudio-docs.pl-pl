---
title: Cv_call_e — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccdc9df86180883a5a3891563b22625fab4a2ad2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466386"
---
# <a name="cvcalle"></a>CV_call_e
Określa konwencję wywołania funkcji.  
  
> [!NOTE]
>  Tylko najbardziej typowe wartości wyliczenia są opisane w tym miejscu. Wyliczenie pełną jest dostępna w pliku nagłówka cvconst.h.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Elementy  
 CV_CALL_NEAR_C  
 Określa Konwencję wywoływania funkcji wypychania near od prawej do lewej. Wywołanie funkcji spowoduje wyczyszczenie stosu.  
  
 CV_CALL_NEAR_FAST  
 Określa Konwencję wywoływania funkcji przy użyciu near wypychania od lewej do prawej z rejestrów. Wywołana funkcja używa Suma bajtów parametrów, aby wyczyścić stosu.  
  
 CV_CALL_NEAR_STD  
 Określa Konwencję wywoływania funkcji przy użyciu standardowych near wywołania (push od prawej do lewej).  
  
 CV_CALL_NEAR_SYS  
 Określa konwencji wywoływania funkcji przy użyciu near wywołania systemu.  
  
 CV_CALL_THISCALL  
 Określa Konwencję wywoływania funkcji przy użyciu `this` wywołania (`this` wskaźnik przekazany w rejestrze).  
  
 CV_CALL_CLRCALL  
 Określa Konwencję wywoływania funkcji, używany przez wspólnego języka środowiska uruchomieniowego (CLR) (znanej także jako zarządzany kod Konwencja wywoływania).  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie wartości są zwracane przez wywołanie do [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)