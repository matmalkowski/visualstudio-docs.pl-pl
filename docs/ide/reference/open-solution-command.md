---
title: "Otwórz rozwiązanie — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a67e3884fbb5e0c4bbb3a5aefe2cdcc8ac7d683e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="open-solution-command"></a>Otwórz rozwiązanie — Polecenie
Otwiera istniejącego rozwiązania, zamykanie innych rozwiązań Otwórz.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.OpenSolution filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `Filename`  
 Wymagany. Pełna ścieżka i nazwa pliku rozwiązania, aby otworzyć.  
  
 Składnia `filename` wymaga argumentu ścieżek zawierających spacje, użyj cudzysłowów.  
  
## <a name="remarks"></a>Uwagi  
 Automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas pisania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zostanie otwarte rozwiązanie Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)