---
title: "Otwórz plik — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 59b0c421fa5a62394a32a2b9ad9926df58a40cb9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="open-file-command"></a>Otwórz plik — Polecenie
Otwiera istniejący plik i umożliwia określenie edytora.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Wymagany. Pełnej lub częściowej ścieżkę i nazwę pliku, aby otworzyć. Ścieżek zawierających spacje musi być ujęta w cudzysłów.  
  
## <a name="switches"></a>Przełączniki  
 / e:`editorname`  
 Opcjonalny. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument zostanie określony, ale zostanie podana żadna nazwa edytora, **Otwórz za pomocą** zostanie wyświetlone okno dialogowe.  
  
 / E:`editorname` argumentu składni korzysta z nazw Edytor znajdujące się w otwartych z okno dialogowe, ujęty w cudzysłów.  
  
 Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Uwagi  
 Podczas wprowadzania ścieżki automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie otwiera plik stylu "Test1.css" w edytorze kodu źródłowego.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Okno bezpośrednie](../../ide/reference/immediate-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)