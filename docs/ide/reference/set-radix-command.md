---
title: "Ustaw radix — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0ba6b4d3ce4aa362c63cace8481bacec90c91716
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="set-radix-command"></a>Ustaw Radix — Polecenie
Ustawia lub zwraca base liczbowego, używany do wyświetlania wartości będące liczbami całkowitymi.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Argumenty  
 `10`lub `16` lub `hex` lub`dec`  
 Opcjonalny. Wskazuje dziesiętna (10 lub gru) lub liczba szesnastkowa (16 lub szesnastkowych). Jeśli argument zostanie pominięty, zwracany jest bieżąca wartość Podstawa.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie środowiska do wyświetlenia w formacie szesnastkowym wartości będące liczbami całkowitymi.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)