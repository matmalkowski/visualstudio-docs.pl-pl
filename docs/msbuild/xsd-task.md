---
title: XSD — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/27/2018
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
ms.openlocfilehash: b292c0bf1bc80f811cbf2f845385f91987184674
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057375"
---
# <a name="xsd-task"></a>XSD — Zadanie
Zawijania narzędzie definicji schematu XML (xsd.exe), które generuje pliki schematu lub klasy ze źródła.  

> [!NOTE]
> W programie Visual Studio 2017 r. xsd.exe obsługę projektów języka C++ jest przestarzały. Można nadal używać **Microsoft.VisualC.CppCodeProvider** interfejsów API przez ręczne dodanie **CppCodeProvider.dll** w pamięci GAC. 
  
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