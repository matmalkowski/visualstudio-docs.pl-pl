---
title: "Przełącz punkt przerwania — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 21a763ee4b2d86a42566aa1d93b8313e5799cee7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="toggle-breakpoint-command"></a>Przełącz punkt przerwania — Polecenie
Włącza punkt przerwania lub wyłączyć, w zależności od bieżącego stanu w bieżącej lokalizacji w pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Argumenty  
 `text`  
 Opcjonalny. Jeśli tekst jest określona, wiersz jest oznaczony jako nazwane punktu przerwania. W przeciwnym razie wiersz jest oznaczony jako bez nazwy punktu przerwania przypominającego co się stanie, kiedy naciśniesz klawisz F9.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przełącza bieżącego punktu przerwania.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)