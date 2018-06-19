---
title: UnInit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56aa940d65934f7cc72f692f5bdf5e44854d276c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471456"
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