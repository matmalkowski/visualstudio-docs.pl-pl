---
title: Lista rejestrów — polecenie | Dokumentacja firmy Microsoft
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
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c9ff1287bb4c92d074c0a0e123d48ddb7e61cc90
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694060"
---
# <a name="list-registers-command"></a>Lista rejestrów — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [lista rejestrów — polecenie](https://docs.microsoft.com/visualstudio/ide/reference/list-registers-command).  
  
  
Wyświetla wartość wybranego rejestruje i pozwala zmodyfikować listę rejestrów, aby pokazać.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>Przełączniki  
 / Wyświetlania [{`register`&#124;`registerGroup`} …]  
 Wyświetla wartości określonego `register` lub `registerGroup`. Jeśli nie `register` lub `registerGroup` jest określony, wyświetlany jest domyślną listę rejestrów. Jeśli przełącznik nie zostanie określony, zachowanie jest takie same. Na przykład:  
  
 `Debug.ListRegisters /Display eax`  
  
 odpowiada wyrażeniu  
  
 `Debug.ListRegisters eax`  
  
 / List  
 Wyświetla wszystkie zarejestrować grupy na liście.  
  
 / Obejrzyj [{`register`&#124;`registerGroup`} …]  
 Dodaje jeden lub więcej `register` lub `registerGroup` wartości do listy.  
  
 / Cofnijwyrażeniekontrolne [{`register`&#124;`registerGroup`} …]  
 Usuwa jeden lub więcej `register` lub `registerGroup` wartości z listy.  
  
## <a name="remarks"></a>Uwagi  
 Alias `r` mogą być używane zamiast `Debug.ListRegisters`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Debug.ListRegisters` alias `r` do wyświetlania wartości grupy rejestru `Flags`.  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Podstawy debugowania: Okno rejestrów](../../debugger/debugging-basics-registers-window.md)   
 [Porady: Korzystanie z okna rejestrów](../../debugger/how-to-use-the-registers-window.md)



