---
title: "Print — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bba20817c03b7ff542c3af11a440ad8e619f5567
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="print-command"></a>Print — Polecenie
Oblicza wyrażenie lub wyświetla określony tekst.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Argumenty  
 `text`  
 Wymagany. Wyrażenie do oceny lub tekst do wyświetlenia.  
  
## <a name="remarks"></a>Uwagi  
 Znak zapytania (?) można użyć jako alias dla tego polecenia. Tak na przykład, polecenie  
  
```  
>Debug.Print expA  
```  
  
 można również zapisać  
  
```  
>? expA  
```  
  
 Obie wersje to polecenie zwróci bieżącą wartość wyrażenia `expA`.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Evaluate statement — polecenie](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)