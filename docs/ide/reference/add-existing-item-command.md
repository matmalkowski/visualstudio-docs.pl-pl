---
title: "Dodaj istniejący element — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a94546b8e480a661c175f946cc376fa92b30cbf8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="add-existing-item-command"></a>Dodaj istniejący element — Polecenie
Dodaje istniejący plik do bieżącego rozwiązania, a następnie go otwiera.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Wymagany. Pełna ścieżka i nazwa pliku, z rozszerzeniem element do dodania do bieżącego rozwiązania. Jeśli ścieżka pliku lub nazwa pliku zawiera spacje, ujmij całą ścieżkę w cudzysłów.  
  
## <a name="switches"></a>Przełączniki  
 / e:`editorname`  
 Opcjonalny. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument zostanie określony, ale zostanie podana żadna nazwa edytora, **Otwórz za pomocą** zostanie wyświetlone okno dialogowe.  
  
 / E:`editorname` składnię argumentu korzysta z nazw Edytor znajdujące się w **Otwieranie z okna dialogowego**, ujęty w cudzysłów. Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Uwagi  
 Autocompletion próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas pisania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie dodaje plik Form1.frm, do bieżącego rozwiązania.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)