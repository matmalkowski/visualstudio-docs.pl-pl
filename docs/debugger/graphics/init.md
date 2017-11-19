---
title: Init | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f32e2e4c5c57359acdc4348f0a83399096383ff2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="init"></a>Init
Przygotowuje składnika diagnostyki grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych w pliku dziennika grafiki w aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vsgLogGetter`  
 Jednostki można wywołać — takich jak funkcja, wskaźnik funkcji, lambda lub obiekt funkcji — która przyjmuje jako parametry długość buforu, składa się z `wchar_t` i wskaźnika do buforu i zwraca `void`. Po wywołaniu, można wywołać jednostki Określa nazwę pliku, który będzie używany do rejestrowania informacji graficznych i zapisuje go w buforze określona przed zwróceniem.  
  
## <a name="remarks"></a>Uwagi  
 `Init` Funkcja jest wywoływana automatycznie, gdy wystąpienie klasy `VsgDbg` klasy jest tworzony przez określenie `bDefaultInit` parametru jego konstruktora jako `true`; w przeciwnym razie `Init` musi być jawnie wywołana przed można przechwycić aktywnie i rejestrować informacji graficznych.  
  
 Można zakończyć i Zamknij aktywny grafiki pliku dziennika przez wywołanie metody `UnInit`, a następnie przechwycić i zarejestrować więcej informacji graficznych do nowego pliku dziennika grafiki przez wywołanie metody `Init` ponownie. Powtórz te dowolną liczbę razy utworzyć pliki dziennika kilku niezależnych grafiki przy użyciu takie same `VsgDbg` wystąpienia.  
  
## <a name="see-also"></a>Zobacz też  
 [UnInit](init.md)