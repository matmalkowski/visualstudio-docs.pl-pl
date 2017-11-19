---
title: "Ustaw bieżący proces | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6bd4ab27a36e37e31ec348b80327b6046c5ecbd3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="set-current-process"></a>Ustaw bieżący proces
Ustawia określony proces jako aktywnego procesu w debugerze.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Argumenty  
 `index`  
 Wymagany. Indeks procesu.  
  
## <a name="remarks"></a>Uwagi  
 Możesz dołączyć do wielu procesów podczas debugowania, ale tylko jeden proces jest aktywny w dubber w danym momencie. Można użyć `SetCurrentProcess` polecenie, aby ustawić aktywnego procesu.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)