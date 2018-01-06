---
title: "Szybka czujka — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bad8605a2a7b9f9606c448680d583c55a2762a75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="quick-watch-command"></a>Szybka czujka — Polecenie
Wyświetla wybrany lub określony tekst w polu wyrażenie [QuickWatch](../../debugger/watch-and-quickwatch-windows.md) okna. To okno dialogowe służy do obliczania bieżącą wartość zmiennej lub wyrażenie rozpoznawane przez debuger lub zawartość rejestru. Ponadto można zmienić wartość zmiennej żadnych wartością stałą lub zawartość dowolnego rejestru.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Argumenty  
 `text`  
 Opcjonalny. Tekst, aby dodać do **QuickWatch** okno dialogowe.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `text` jest pominięty, aktualnie zaznaczonego tekstu lub word wskazywanej przez kursor jest dodawany do okna czujki.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Ustaw czujki na zmiennych czujki i QuickWatch Windows w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)