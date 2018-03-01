---
title: "Lista rejestrów — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 016de257d1ce4e6d2aa95284adbe762a5c54eacf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="list-registers-command"></a>Lista rejestrów — Polecenie
Wyświetla wartość wybranego rejestruje i umożliwia zmodyfikowanie listy rejestrów do wyświetlenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>Przełączniki  
 / Wyświetlić [{`register`&#124;`registerGroup`} ...]  
 Wyświetla wartości z określonego `register` lub `registerGroup`. Jeśli nie `register` lub `registerGroup` jest określona, zostanie wyświetlona domyślna lista rejestrów. Jeśli nie jest określony, zachowanie jest takie same. Na przykład:  
  
 `Debug.ListRegisters /Display eax`  
  
 jest równoważny  
  
 `Debug.ListRegisters eax`  
  
 / List  
 Wyświetla wszystkie grupy rejestru na liście.  
  
 / Obejrzyj [{`register`&#124;`registerGroup`} ...]  
 Dodaje co najmniej jeden `register` lub `registerGroup` wartości do listy.  
  
 / Unwatch [{`register`&#124;`registerGroup`} ...]  
 Usuwa jeden lub więcej `register` lub `registerGroup` wartości z listy.  
  
## <a name="remarks"></a>Uwagi  
 Alias `r` można użyć zamiast `Debug.ListRegisters`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Debug.ListRegisters` alias `r` do wyświetlania wartości rejestru grupy `Flags`.  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Podstawy debugowania: Okno rejestrów](../../debugger/debugging-basics-registers-window.md)   
 [Porady: Korzystanie z okna rejestrów](../../debugger/how-to-use-the-registers-window.md)