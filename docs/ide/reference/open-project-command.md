---
title: "Otwórz projekt — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3b0916874fbd4c16dfe2232a6a5865743d0c388
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="open-project-command"></a>Otwórz projekt — Polecenie
Otwiera istniejący projekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Wymagany. Pełna ścieżka i nazwa projektu, aby otworzyć.  
  
 Składnia `filename` wymaga argumentu ścieżek zawierających spacje, użyj cudzysłowów.  
  
## <a name="remarks"></a>Uwagi  
 Automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas pisania.  
  
 To polecenie nie jest dostępna podczas debugowania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie otwiera [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)