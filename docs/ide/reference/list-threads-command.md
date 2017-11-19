---
title: "Lista wątków polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa71ec1c6eb8ac50d957782dda02a2c3fb59a3c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="list-threads-command"></a>Lista wątków — Polecenie
Wyświetla listę wątki bieżącego programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Argumenty  
 `index`  
 Opcjonalny. Wybiera wątku przez jego indeksu bieżącego wątku.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku `index` argumentu oznacza wskazanych wątku, co bieżący wątek. Znak gwiazdki (*) jest wyświetlana na liście obok bieżącego wątku.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Lista stosu wywołań — polecenie](../../ide/reference/list-call-stack-command.md)   
 [Lista dezasemblacji — polecenie](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)