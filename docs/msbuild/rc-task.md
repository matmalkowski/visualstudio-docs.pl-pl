---
title: RC — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28f600d01765c37b3e9a896afa8b6d2a55c7df12
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31574571"
---
# <a name="rc-task"></a>RC — Zadanie
Opakowuje narzędzia kompilatora zasobów systemu Windows firmy Microsoft rc.exe. **RC** zadań kompiluje zasoby, takie jak kursory, ikony, mapy bitowe, okna dialogowe i czcionek, do pliku zasobów (.res). Aby uzyskać więcej informacji, zobacz "Kompilator zasobów" w [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry RCtask. Większość zadań parametrów i kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Opcjonalne **String []** parametru.<br /><br /> Dodaje katalog do listy katalogów, które są wyszukiwane pliki nagłówkowe.<br /><br /> Aby uzyskać więcej informacji, zobacz **/I** opcji [przy użyciu RC (wiersza polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN.|  
|**AdditionalOptions**|Opcjonalne **ciąg** parametru.<br /><br /> Lista przykład wiersza polecenia optionsor **"*** / opcja 1 /option2 /option#*". Ten parametr umożliwia określenie opcji wiersza polecenia, które nie są reprezentowane przez inne **RC** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz Opcje w [przy użyciu RC (wiersza polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN.|  
|**Kultury**|Opcjonalne **ciąg** parametru.<br /><br /> Określa identyfikator ustawień regionalnych, który reprezentuje kulturę używaną w zasobach.<br /><br /> Aby uzyskać więcej informacji, zobacz **/l** opcji [przy użyciu RC (wiersza polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN.|  
|**IgnoreStandardIncludePath**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, zabezpiecza kompilator zasobów sprawdzanie zmiennej środowiskowej INCLUDE podczas wyszukiwania plików nagłówka lub zasobu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/x** opcji [przy użyciu RC (wiersza polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN.|  
|**NullTerminateStrings**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, wszystkie ciągi w tabeli ciągów kończy wartości null.<br /><br /> Aby uzyskać więcej informacji, zobacz **/n** opcji [przy użyciu RC (wiersza polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN.|  
|**PreprocessorDefinitions**|Opcjonalne **String []** parametru.<br /><br /> Należy zdefiniować co najmniej jeden symboli preprocesora kompilatora zasobów. Określ listę makro symboli.<br /><br /> Aby uzyskać więcej informacji, zobacz **/d** opcji [przy użyciu RC (wiersza polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN. Zobacz też **UndefinePreprocessorDefinitions** w tej tabeli.|  
|**ResourceOutputFileName**|Opcjonalne **ciąg** parametru.<br /><br /> Określa nazwę pliku zasobu. Określ nazwę pliku zasobu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/fo** opcji [przy użyciu RC (wiersza polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN.|  
|**ShowProgress**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, wyświetlane są komunikaty, które raport dotyczący postępu kompilatora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/v** opcji [przy użyciu RC (wiersza polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN.|  
|**Źródło**|Wymagane `ITaskItem[]` parametru.<br /><br /> Określa tablicę elementów MSBuild pliku źródłowego, które mogą być używane i emitowane przez zadania.|  
|**SuppressStartupBanner**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości copyright i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, wpisz **/?** Opcja wiersza polecenia, a następnie zobacz **/nologo** opcji.|  
|**Katalog TrackerLogDirectory**|Opcjonalne **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|  
|**UndefinePreprocessorDefinitions**|Usuń definicję symboli preprocesora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/u** opcji [przy użyciu RC (wiersza polecenia RC)](http://go.microsoft.com/fwlink/?LinkId=155730) w witrynie MSDN. Zobacz też **PreprocessorDefinitions** w tej tabeli.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)