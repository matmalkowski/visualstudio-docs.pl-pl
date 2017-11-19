---
title: UnInit | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285cfb5a68055612fc7d77022b8f9d1d61067ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="uninit"></a>UnInit
Kończenie znajdujących się w pliku dziennika grafiki, zamyka i zwalnia zasoby, które były używane podczas aplikacji został aktywnie rejestrowanie informacji graficznych.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Uwagi  
 `UnInit`jest wywoływana automatycznie, gdy wystąpienie klasy `VsgDbg` klasa zostanie zniszczony. Jeśli `VsgDbg` wystąpienie nie zostało aktywnie rejestrowanie informacji graficznych, to ustawienie nie działa.  
  
 Po `UnInit` została wywołana dla wystąpienia `VsgDbg` klas grafiki nowy plik dziennika można utworzyć przez wywołanie metody `Init` i przetwarzania przez wywołanie metody `UnInit`. Powtórz te dowolną liczbę razy używać tego samego `VsgDbg` wystąpienie można utworzyć kilka grafiki niezależnie od plików dziennika.  
  
## <a name="see-also"></a>Zobacz też  
 [Init](init.md)