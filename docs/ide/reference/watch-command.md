---
title: Czujka — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a82816acfbb995b47dfb34337b20488ad3787f04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="watch-command"></a>Czujka — Polecenie
Tworzy i otwiera określone wystąpienie programu **czujki** okna. Można użyć **czujki** okna do obliczania wartości zmiennych, wyrażenia i rejestrów, aby edytować te wartości i zapisać wyniki.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Argumenty  
 `index`  
 Wymagany. Liczba wystąpień okna czujki.  
  
## <a name="remarks"></a>Uwagi  
 `index` Musi być liczbą całkowitą. Prawidłowe wartości to 1, 2, 3 lub 4.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyczne i ustawień regionalnych systemu Windows](../../debugger/autos-and-locals-windows.md)   
 [Ustaw czujki na zmiennych czujki i QuickWatch Windows w programie Visual Studio](../../debugger/watch-and-quickwatch-windows.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)