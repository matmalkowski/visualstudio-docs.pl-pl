---
title: Przejdź do polecenia | Dokumentacja firmy Microsoft
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
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 123398be5bf8b4aece11e2624390507cec2252d0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679721"
---
# <a name="go-to-command"></a>Przejdź do — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [polecenia przejdź do](https://docs.microsoft.com/visualstudio/ide/reference/go-to-command).  
  
  
Przenosi kursor do określonego wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Argumenty  
 `linenumber`  
 Opcjonalna. Liczba całkowita reprezentująca numer wiersza, aby przejść do.  
  
## <a name="remarks"></a>Uwagi  
 Numerowanie wierszy rozpoczyna się od jednego. Jeśli wartość `linenumber` jest mniejsza niż jeden, pierwszy wyświetla wiersz. Jeśli wartość `linenumber` jest większa niż liczba ostatnim wierszu ostatniej wyświetla wiersz.  
  
 Jeśli wartość `linenumber` nie zostanie określony, **przejdź do wiersza** Wyświetla okno dialogowe.  
  
 Alias dla tego polecenia jest GoToLn.  
  
## <a name="example"></a>Przykład  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



