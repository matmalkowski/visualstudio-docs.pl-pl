---
title: Uruchom polecenie | Dokumentacja firmy Microsoft
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
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e70a682d9b9ef67e9f0372173c3396a0706cd2f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676647"
---
# <a name="start-command"></a>Uruchomienie — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [polecenia Start](https://docs.microsoft.com/visualstudio/ide/reference/start-command).  
  
  
Rozpoczyna się debugowanie projektu startowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Argumenty  
 `address`  
 Opcjonalna. Adres, w którym program zawiesza wykonywanie, podobnie jak punkt przerwania w kodzie źródłowym. Ten argument jest prawidłowy tylko w trybie debugowania.  
  
## <a name="remarks"></a>Uwagi  
 **Start** polecenia po wykonaniu wykonuje operację RunToCursor do określonego adresu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie Uruchamia debuger i ignoruje wszelkie wyjątki, które występują.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



