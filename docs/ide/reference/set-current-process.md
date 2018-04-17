---
title: Ustaw bieżący proces | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ea3028be32fdccffd70f7b3d0aa9d3b4eba172c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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