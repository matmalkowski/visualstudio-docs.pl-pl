---
title: Dodaj istniejący projekt — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 278ed3e13f29746aab963129418dc07f1dcf5234
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="add-existing-project-command"></a>Dodaj istniejący projekt — Polecenie
Dodaje istniejący projekt do bieżącego rozwiązania.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Opcjonalny. Pełna ścieżka i projektu nazwa, z rozszerzeniem projektu do dodania do rozwiązania.  
  
 Jeśli `filename` argument zawiera spacje, musi być ujęta w cudzysłów.  
  
 Jeśli nazwa pliku nie zostanie określony, polecenie będzie Otwórz okno dialogowe pliku, użytkownik może wybrać projekt.  
  
## <a name="remarks"></a>Uwagi  
 Automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas pisania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie dodaje [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu, TestProject1, do bieżącego rozwiązania.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)