---
title: Xdcmake — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.task.xdcmake
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce1d7c88ffa0f2232b31a3c559e8339710582aeb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632565"
---
# <a name="xdcmake-task"></a>XDCMake — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [xdcmake — zadanie](https://docs.microsoft.com/visualstudio/msbuild/xdcmake-task).  
  
  
Opakowuje narzędzie dokumentacji XML (xdcmake.exe), które scala pliki komentarzy (.xdc) dokumentu XML w pliku XML.  
  
 Po podaniu komentarzy do dokumentacji w kodzie źródłowym języka Visual C++ i kompilacji za pomocą, tworzony jest plik .xdc [/doc](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [xdcmake — dokumentacja](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [strony właściwości narzędzia generowania dokumentów XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)i opcji Pomoc w wierszu polecenia (**/?**) dla xdcmake.exe.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie narzędzie xdcmake.exe obsługuje kilka opcji wiersza polecenia. Dodatkowe opcje są obsługiwane w przypadku określenia **/stare** opcji wiersza polecenia.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **XDCMake** zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Opcjonalnie **String []** parametru.<br /><br /> Określa jeden lub więcej plików xdc dodatkowe do scalenia.<br /><br /> Aby uzyskać więcej informacji, zobacz **dodatkowe pliki dokumentów** opis [strony właściwości narzędzia generowania dokumentów XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0). Zobacz też **/stare** i **/Fs** opcje wiersza polecenia dla xdcmake.exe.|  
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.<br /><br /> Lista opcji określonych w wierszu polecenia. Na przykład "*/option1 /option2 /option#*". Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez inne **XDCMake** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz [xdcmake — dokumentacja](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [strony właściwości narzędzia generowania dokumentów XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)i pomoc w wierszu polecenia (**/?**) dla xdcmake.exe.|  
|**DocumentLibraryDependencies**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true` i bieżący projekt zależny od projektu biblioteka statyczna (lib), w rozwiązaniu, plików xdc dla tego projektu biblioteki znajdują się dane wyjściowe pliku XML dla bieżącego projektu.<br /><br /> Aby uzyskać więcej informacji, zobacz **zależności biblioteki dokumentów** opis [strony właściwości narzędzia generowania dokumentów XML](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0).|  
|**OutputFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Przesłania domyślną nazwę pliku wyjściowego. Domyślną nazwą jest pochodną nazwę pierwszego pliku .xdc, który jest przetwarzany.<br /><br /> Aby uzyskać więcej informacji, zobacz **/out:** `filename` opcji [xdcmake — dokumentacja](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac). Zobacz też **/stare** i **/Fo** opcje wiersza polecenia dla xdcmake.exe.|  
|**ProjectName**|Opcjonalnie **ciąg** parametru.<br /><br /> Nazwa bieżącego projektu.|  
|**SlashOld**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, włącza xdcmake.exe dodatkowe opcje.<br /><br /> Aby uzyskać więcej informacji, zobacz **/stare** opcji wiersza polecenia dla xdcmake.exe.|  
|**Źródła**|Wymagane `ITaskItem[]` parametru.<br /><br /> Określa tablicę elementów pliku źródłowego programu MSBuild, które mogą być używane i wyemitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcji [xdcmake — dokumentacja](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac).|  
|**Katalog TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)



