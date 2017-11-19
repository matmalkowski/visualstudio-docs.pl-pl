---
title: "Bscmake — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 8a5977d40f8903e99dd904e5fe09ec86572895b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="bscmake-task"></a>BscMake — Zadanie
> [!IMPORTANT]
>  bscmake nie jest już używany przez Visual Studio IDE. Od programu Visual Studio 2008 informacje o przeglądaniu są automatycznie przechowywane w pliku .sdf w folderze rozwiązania.  
  
 Zawijania narzędzie przeglądać informacje o konserwacji narzędzie Microsoft (bscmake.exe).  Narzędzie bscmake.exe kompilacji pliku informacyjnego przeglądarki (.bsc) z pliki przeglądarki źródła (.sbr), które są tworzone podczas kompilacji. Użyj **przeglądarki obiektów** do wyświetlenia pliku .bsc. Aby uzyskać więcej informacji, zobacz [odwołanie BSCMAKE](/cpp/build/reference/bscmake-reference).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **BscMake** zadań. Większość parametrów zadania odpowiada opcji wiersza polecenia.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalOptions**|Opcjonalne **ciąg** parametru.<br /><br /> Lista opcje określone w wierszu polecenia. Na przykład "/*opcja 1* /*option2* /*opcji #*". Ten parametr umożliwia określenie opcji, które nie są reprezentowane przez inne **BscMake** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w [opcje BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**OutputFile**|Opcjonalne **ciąg** parametru.<br /><br /> Określa nazwę pliku, która zastępuje domyślną nazwę pliku wyjściowego.<br /><br /> Aby uzyskać więcej informacji, zobacz **/o** opcji [opcje BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**PreserveSBR**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, wymusza nieprzyrostowa kompilacji. Pełne, nieprzyrostowa kompilacji występuje niezależnie od tego, czy istnieje plik .bsc i uniemożliwia obcinania plików SBR.<br /><br /> Aby uzyskać więcej informacji, zobacz  **/n**  opcji [opcje BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**Źródeł**|Opcjonalne **[ITaskItem]** parametru.<br /><br /> Określa tablicę elementów MSBuild pliku źródłowego, które mogą być używane i emitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości copyright i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcji [opcje BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**Katalog TrackerLogDirectory**|Opcjonalne **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)