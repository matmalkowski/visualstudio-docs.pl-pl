---
title: "Xdcmake — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 09b308084d9fd839c3b24a7d60317a9f93efd32a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xdcmake-task"></a>XDCMake — Zadanie
Zawijania narzędzie dokumentacji XML (xdcmake.exe), które scala pliki dokumentacji XML (.xdc) w pliku XML.  
  
 Plik .xdc jest tworzony, podając komentarze do dokumentacji w Visual C++ kod źródłowy i kompilacji za pomocą [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [xdcmake — odwołanie](/cpp/ide/xdcmake-reference), [strony właściwości narzędzia generowania dokumentów XML](/cpp/ide/xml-document-generator-tool-property-pages)i opcji Pomoc wiersza polecenia (**/?**) dla xdcmake.exe.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie narzędzie xdcmake.exe obsługuje kilka opcji wiersza polecenia. Dodatkowe opcje są obsługiwane w przypadku określenia **/starego** opcji wiersza polecenia.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **xdcmake —** zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Opcjonalne **String []** parametru.<br /><br /> Określa jeden lub więcej plików xdc dodatkowe do scalenia.<br /><br /> Aby uzyskać więcej informacji, zobacz **dodatkowe pliki dokumentów** opis w [strony właściwości narzędzia generowania dokumentów XML](/cpp/ide/xml-document-generator-tool-property-pages). Zobacz też **/starego** i **/Fs** xdcmake.exe opcji wiersza polecenia.|  
|**AdditionalOptions**|Opcjonalne **ciąg** parametru.<br /><br /> Lista opcje określone w wierszu polecenia. Na przykład "*/option1 /option2 /option#*". Ten parametr umożliwia określenie opcji, które nie są reprezentowane przez inne **xdcmake —** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz [xdcmake — odwołanie](/cpp/ide/xdcmake-reference), [strony właściwości narzędzia generowania dokumentów XML](/cpp/ide/xml-document-generator-tool-property-pages)i pomoc wiersza polecenia (**/?**) dla xdcmake.exe.|  
|**DocumentLibraryDependencies**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true` i bieżącego projektu zależności projektu w rozwiązaniu biblioteka statyczna (lib), plików xdc dla tego projektu biblioteki zostaną uwzględnione w danych wyjściowych pliku XML dla bieżącego projektu.<br /><br /> Aby uzyskać więcej informacji, zobacz **zależności biblioteki dokumentów** opis w [strony właściwości narzędzia generowania dokumentów XML](/cpp/ide/xml-document-generator-tool-property-pages).|  
|**OutputFile**|Opcjonalne **ciąg** parametru.<br /><br /> Przesłania domyślną nazwę pliku wyjściowego. Domyślna nazwa pochodzi od Nazwa pierwszego pliku .xdc, która została przetworzona.<br /><br /> Aby uzyskać więcej informacji, zobacz **/out:** `filename` opcji [xdcmake — odwołanie](/cpp/ide/xdcmake-reference). Zobacz też **/starego** i **/Fo** opcje wiersza polecenia dla xdcmake.exe.|  
|**ProjectName**|Opcjonalne **ciąg** parametru.<br /><br /> Nazwa bieżącego projektu.|  
|**SlashOld**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, włącza xdcmake.exe dodatkowe opcje.<br /><br /> Aby uzyskać więcej informacji, zobacz **/starego** opcji wiersza polecenia dla xdcmake.exe.|  
|**Źródeł**|Wymagane `ITaskItem[]` parametru.<br /><br /> Określa tablicę elementów MSBuild pliku źródłowego, które mogą być używane i emitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości copyright i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcji [xdcmake — odwołanie](/cpp/ide/xdcmake-reference).|  
|**Katalog TrackerLogDirectory**|Opcjonalne **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)