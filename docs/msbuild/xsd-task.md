---
title: XSD — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7505f3d18e0b32ebdbc8b82d447e49b26fe4182e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="xsd-task"></a>XSD — Zadanie
Zawijania narzędzie definicji schematu XML (xsd.exe), które generuje pliki schematu lub klasy ze źródła.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **XSD** zadań.  
  
-   **AdditionalOptions**  
  
     Opcjonalne **ciąg** parametru.  
  
     Lista opcje określone w wierszu polecenia. Na przykład "*/option1 /option2 /option#*". Ten parametr umożliwia określenie opcji, które nie są reprezentowane przez inne **XSD** parametru zadania.  
  
-   **GenerateFromSchema**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa typy, które są generowane na podstawie określonego schematu.  
  
     Określ jedną z następujących wartości, z których każdy odpowiada opcji XSD.  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Język**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa język programowania dla wygenerowanego kodu.  
  
     Wybierz jedną z **CS** (C#, która jest ustawiona domyślnie), **VB** (Visual Basic), lub **JS** (JScript). Można również określić pełną nazwę klasy, która implementuje `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
-   **Namespace**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa przestrzeń nazw czasu wykonywania wygenerowany typów.  
  
-   **Źródeł**  
  
     Wymagane `ITaskItem[]` parametru.  
  
     Określa tablicę elementów MSBuild pliku źródłowego, które mogą być używane i emitowane przez zadania.  
  
-   **SuppressStartupBanner**  
  
     Opcjonalne **logiczna** parametru.  
  
     Jeśli `true`, uniemożliwia wyświetlanie wiadomości copyright i wersji, podczas uruchamiania zadania.  
  
-   **Katalog TrackerLogDirectory**  
  
     Opcjonalne **ciąg** parametru.  
  
     Określa katalog dziennika śledzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)