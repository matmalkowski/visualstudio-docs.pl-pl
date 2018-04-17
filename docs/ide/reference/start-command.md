---
title: Polecenie uruchomienia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a4c372d3f384eeaa0ac137188e325ccde777cd4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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