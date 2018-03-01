---
title: Polecenie uruchomienia | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8eb0efae140613c6caa7bd71d72e0ce4cda37db8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="start-command"></a>Uruchomienie — Polecenie
Rozpoczyna debugowania projektu startowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Argumenty  
 `address`  
 Opcjonalny. Adres, pod którym program wstrzymuje wykonywanie, podobnie jak punkt przerwania w kodzie źródłowym. Ten argument jest prawidłowy tylko w trybie debugowania.  
  
## <a name="remarks"></a>Uwagi  
 **Start** polecenia po wykonaniu wykonuje operację RunToCursor do określonego adresu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie uruchomienie debugera i ignoruje wszelkie wyjątki, które występują.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)