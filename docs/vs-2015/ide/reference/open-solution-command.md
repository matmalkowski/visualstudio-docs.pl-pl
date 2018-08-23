---
title: Otwórz rozwiązanie — polecenie | Dokumentacja firmy Microsoft
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
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8c2c93f44ba7c801b31390c411da1d16c1645bf6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42629692"
---
# <a name="open-solution-command"></a>Otwórz rozwiązanie — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Otwórz rozwiązanie, polecenie](https://docs.microsoft.com/visualstudio/ide/reference/open-solution-command).  
  
  
Powoduje otwarcie istniejącego rozwiązania, zamyka wszystkie otwarte rozwiązania.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.OpenSolution filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `Filename`  
 Wymagane. Pełna ścieżka i nazwa pliku rozwiązania, aby otworzyć.  
  
 Składnia `filename` argument wymaga, że ścieżki zawierające spacje, użyj znaków cudzysłowu.  
  
## <a name="remarks"></a>Uwagi  
 Automatyczne uzupełnianie próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie otwiera rozwiązanie Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



