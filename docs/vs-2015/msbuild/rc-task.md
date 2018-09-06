---
title: RC — zadanie | Dokumentacja firmy Microsoft
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
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ff118a6d32a182d1060cc051f24352b16037039
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775427"
---
# <a name="rc-task"></a>RC — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [RC — zadanie](https://docs.microsoft.com/visualstudio/msbuild/rc-task).  
  
  
Opakowuje narzędzie kompilatora zasobów systemu Microsoft Windows rc.exe. **RC** zadań kompiluje zasoby, takie jak kursorów, ikony, mapy bitowe, okna dialogowe i czcionek, w pliku zasobów (.res). Aby uzyskać więcej informacji, zobacz "Kompilator zasobów" w [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry RCtask. Większość parametrów zadania oraz kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Opcjonalnie **String []** parametru.<br /><br /> Dodaje katalog do listy katalogów przeszukiwanych w poszukiwaniu plików dołączanych.<br /><br /> Aby uzyskać więcej informacji, zobacz **/I** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.<br /><br /> Lista przykład wiersza polecenia optionsor **"**_/option1 /option2 /option#_". Użyj tego parametru, aby określić opcje wiersza polecenia, które nie są reprezentowane przez inne **RC** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**Kultury**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa identyfikator ustawień regionalnych, który reprezentuje kulturę używaną w zasobach.<br /><br /> Aby uzyskać więcej informacji, zobacz **/l** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**IgnoreStandardIncludePath**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia sprawdzanie zmienną środowiskową INCLUDE podczas wyszukiwania plików nagłówkowych lub plików zasobów przez kompilator zasobów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/x** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**NullTerminateStrings**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, wartość null kończy wszystkie ciągi w tablicy ciągów.<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**PreprocessorDefinitions**|Opcjonalnie **String []** parametru.<br /><br /> Należy zdefiniować co najmniej jeden symboli preprocesora kompilatora zasobów. Określ listę symbole makra.<br /><br /> Aby uzyskać więcej informacji, zobacz **/d** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web. Zobacz też **UndefinePreprocessorDefinitions** w tej tabeli.|  
|**ResourceOutputFileName**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa nazwę pliku zasobów. Określ nazwę pliku zasobu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/fo** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**ShowProgress**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, wyświetla komunikaty, które składać sprawozdania z postępów kompilatora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/v** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web.|  
|**Źródło**|Wymagane `ITaskItem[]` parametru.<br /><br /> Określa tablicę elementów pliku źródłowego programu MSBuild, które mogą być używane i wyemitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, wpisz **/?** Opcja wiersza polecenia, a następnie zobacz **/nologo** opcji.|  
|**Katalog TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|  
|**UndefinePreprocessorDefinitions**|Usuń definicje symboli preprocesora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/u** opcji [przy użyciu RC (wiersz polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN w sieci Web. Zobacz też **PreprocessorDefinitions** w tej tabeli.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)



