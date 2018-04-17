---
title: UnInit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 735eb1948acfb03a6aa1a70fb27f012c41bb097d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="uninit"></a>UnInit
Kończenie znajdujących się w pliku dziennika grafiki, zamyka i zwalnia zasoby, które były używane podczas aplikacji został aktywnie rejestrowanie informacji graficznych.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Uwagi  
 `UnInit` jest wywoływana automatycznie, gdy wystąpienie klasy `VsgDbg` klasa zostanie zniszczony. Jeśli `VsgDbg` wystąpienie nie zostało aktywnie rejestrowanie informacji graficznych, to ustawienie nie działa.  
  
 Po `UnInit` została wywołana dla wystąpienia `VsgDbg` klas grafiki nowy plik dziennika można utworzyć przez wywołanie metody `Init` i przetwarzania przez wywołanie metody `UnInit`. Powtórz te dowolną liczbę razy używać tego samego `VsgDbg` wystąpienie można utworzyć kilka grafiki niezależnie od plików dziennika.  
  
## <a name="see-also"></a>Zobacz też  
 [Init](init.md)