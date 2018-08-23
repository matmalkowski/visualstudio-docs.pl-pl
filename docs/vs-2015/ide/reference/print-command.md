---
title: Print — polecenie | Dokumentacja firmy Microsoft
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
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e518b3c6ffc3520b408e7c1bfb1fd1703e40a8de
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42673993"
---
# <a name="print-command"></a>Print — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [polecenie Drukuj](https://docs.microsoft.com/visualstudio/ide/reference/print-command).  
  
  
Oblicza wyrażenie lub wyświetla określony tekst.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Argumenty  
 `text`  
 Wymagane. Wyrażenie do oceny lub tekst do wyświetlenia.  
  
## <a name="remarks"></a>Uwagi  
 Dla tego polecenia, można użyć znaku zapytania (?) jako alias. Tak na przykład polecenie  
  
```  
>Debug.Print expA  
```  
  
 można również zapisać  
  
```  
>? expA  
```  
  
 Obie wersje to polecenie zwraca bieżącą wartość wyrażenia `expA`.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Evaluate statement — polecenie](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



