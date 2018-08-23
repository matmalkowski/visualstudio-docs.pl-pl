---
title: Ustaw radix — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99b5623fff4e2919bb34bc7dd4ba60d14ba93077
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632037"
---
# <a name="set-radix-command"></a>Ustaw Radix — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Ustaw radix — polecenie](https://docs.microsoft.com/visualstudio/ide/reference/set-radix-command).  
  
  
Ustawia lub zwraca base numeryczne, używany do wyświetlania wartości całkowitych.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Argumenty  
 `10` lub `16` lub `hex` lub `dec`  
 Opcjonalna. Wskazuje dziesiętne (10 lub gru) lub liczba szesnastkowa (16 lub szesnastkowych). Jeśli argument jest pominięty, zwracany jest bieżąca wartość podstawy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie środowiska, aby wyświetlić wartości całkowite w formacie szesnastkowym.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



