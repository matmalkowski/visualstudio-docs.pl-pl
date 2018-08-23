---
title: Czujka — polecenie | Dokumentacja firmy Microsoft
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
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d06e15f23a8f75e4a771b9db1991f5aba2ffc0d8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678445"
---
# <a name="watch-command"></a>Czujka — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Czujka — polecenie](https://docs.microsoft.com/visualstudio/ide/reference/watch-command).  
  
  
Tworzy i otwiera określone wystąpienie **Obejrzyj** okna. Możesz użyć **Obejrzyj** okna do obliczania wartości zmiennych, wyrażenia i rejestry, aby edytować te wartości i zapisać wyniki.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Argumenty  
 `index`  
 Wymagane. Liczba wystąpień okna czujki.  
  
## <a name="remarks"></a>Uwagi  
 `index` Musi być liczbą całkowitą. Prawidłowe wartości to 1, 2, 3 lub 4.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiennych automatycznych i zmiennych lokalnych Windows](../../debugger/autos-and-locals-windows.md)   
 [Porady: Edytowanie wartości w oknie zmiennych](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Porady: Użyj okna dialogowego QuickWatch](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



