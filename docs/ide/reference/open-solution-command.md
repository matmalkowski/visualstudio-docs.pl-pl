---
title: Otwórz rozwiązanie — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e97fa5265550222b4df9143a900419a0994f9129
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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