---
title: "MT — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (Visual C++), MT task
- MT task (MSBuild (Visual C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 2b0c421ca3d1e56c22cab7ff066d17d59914961c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="mt-task"></a>MT — Zadanie
Zawijania narzędzie Microsoft Manifest mt.exe. Aby uzyskać więcej informacji, zobacz "Mt.exe" w [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **MT** zadań. Większość zadań parametrów i kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
> [!NOTE]
>  Łącznik korzysta z dokumentacji mt.exe (**-**) jako prefiks dla opcji wiersza polecenia, ale w tym temacie używa ukośnika (**/**). Dopuszczalne jest albo prefiksu.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Opcjonalne **String []** parametru.<br /><br /> Określa nazwę co najmniej jeden plik manifestu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/manifest** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**AdditionalOptions**|Opcjonalne **ciąg** parametru.<br /><br /> Listę opcji wiersza polecenia. Na przykład "*/option1 /option2 /option#*". Ten parametr umożliwia określenie opcji wiersza polecenia, które nie są reprezentowane przez inne **MT** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz "Mt.exe" w [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**Element AssemblyIdentity**|Opcjonalne **ciąg** parametru.<br /><br /> Określa wartości atrybutu **assemblyIdentity** element manifestu. Określ rozdzieloną przecinkami listę, gdzie znajduje się pierwszy składnik jest wartością `name` atrybutu następuje pary nazwa/wartość, których formularz,  *\<nazwa atrybutu > = < attribute_value >*.<br /><br /> Aby uzyskać więcej informacji, zobacz **/identity** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**ComponentFileName**|Opcjonalne **ciąg** parametru.<br /><br /> Określa nazwę biblioteki dołączanej, które mają zostać kompilacji z plików .rgs lub .tlb. Ten parametr jest wymagany, jeśli określono **RegistrarScriptFile** lub **TypeLibraryFile** MT parametrów zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/dll** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**DependencyInformationFile**|Opcjonalne **ciąg** parametru.<br /><br /> Określa plik informacji o zależnościach, używany przez program Visual Studio do śledzenia informacji o zależnościach kompilacji dla narzędzia manifestu.|  
|**EmbedManifest**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, osadza plik manifestu w zestawie. Jeśli `false`, tworzy jako autonomiczny plik manifestu.|  
|**EnableDPIAwareness**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, dodaje do manifestu informacje, wskazującą aplikację jako obsługującą ustawienia DPI. Pisanie aplikacji obsługującą ustawienia DPI sprawia, że interfejs użytkownika wyglądać spójnie z wieloma różnymi ustawienia wysokiej rozdzielczości ekranu.<br /><br /> Aby uzyskać więcej informacji, zobacz "Wysokiej rozdzielczości" w [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**GenerateCatalogFiles**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, generuje katalogu plików definicji (.cdf).<br /><br /> Aby uzyskać więcej informacji, zobacz **/makecdfs** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**GenerateCategoryTags**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, powoduje, że tagi kategorii do wygenerowania. Jeśli ten parametr ma `true`, **ManifestFromManagedAssemblyMT** również musi zostać określony parametr zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/category** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**InputResourceManifests**|Opcjonalne **ciąg** parametru.<br /><br /> Dane wejściowe manifestu z zasobu typu RT_MANIFEST, który ma określony identyfikator. Określ zasób w postaci  *\<Plik > [***;** *[***#***] < resource_id >]*, gdzie opcjonalny `resource_id` parametru jest liczbą nieujemną, 16-bitowych.<br /><br /> Jeśli nie `resource_id` jest określona, zostanie użyta wartość domyślna CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Aby uzyskać więcej informacji, zobacz **/inputresource** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**ManifestFromManagedAssembly**|Opcjonalne **ciąg** parametru.<br /><br /> Generuje manifest z określonego zestawu zarządzanego.<br /><br /> Aby uzyskać więcej informacji, zobacz **/managedassemblyname** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**ManifestToIgnore**|Opcjonalne **ciąg** parametru.<br /><br /> (Nie jest używany.)|  
|**OutputManifestFile**|Opcjonalne **ciąg** parametru.<br /><br /> Określa nazwę manifestu wyjściowego. Jeśli ten parametr zostanie pominięty, tylko jeden manifest jest on obsługiwany przez tego manifestu jest modyfikowany w miejscu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/out** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**OutputResourceManifests**|Opcjonalne **ciąg** parametru.<br /><br /> Dane wyjściowe manifestu do zasobu typu RT_MANIFEST, który ma określony identyfikator. Zasób jest w formie  *\<Plik > [***;** *[***#***] < resource_id >]*, gdzie opcjonalny `resource_id` parametru jest liczbą nieujemną, 16-bitowych.<br /><br /> Jeśli nie `resource_id` jest określona, zostanie użyta wartość domyślna CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Aby uzyskać więcej informacji, zobacz **/outputresource** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**RegistrarScriptFile**|Opcjonalne **ciąg** parametru.<br /><br /> Określa nazwę rejestratora pliku skryptu (.rgs) bez rejestrowania COM manifestu pomocy technicznej.<br /><br /> Aby uzyskać więcej informacji, zobacz **/rgs** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**ReplacementsFile**|Opcjonalne **ciąg** parametru.<br /><br /> Określa plik, który zawiera wartości dla wymienialnych ciągów w pliku skryptu (.rgs) rejestratora.<br /><br /> Aby uzyskać więcej informacji, zobacz **/replacements** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**ResourceOutputFileName**|Opcjonalne **ciąg** parametru.<br /><br /> Określa plik zasobów wynikowych, używany do osadzania manifestu w projekcie wynikowym.|  
|**Źródeł**|Opcjonalne `ITaskItem[]` parametru.<br /><br /> Określa listę plików źródłowych manifestu rozdzielone spacjami.<br /><br /> Aby uzyskać więcej informacji, zobacz **/manifest** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**SuppressDependencyElement**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, generuje manifest bez zależności elementów. Jeśli ten parametr ma `true`, również określić **ManifestFromManagedAssemblyMT** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nodependency** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**SuppressStartupBanner**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości copyright i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**Katalog TrackerLogDirectory**|Opcjonalne `String` parametru.<br /><br /> Określa katalog pośredni, w którym są przechowywane dzienniki śledzenia dla tego zadania.|  
|**TypeLibraryFile**|Opcjonalne **ciąg** parametru.<br /><br /> Określa nazwę pliku (.tlb) biblioteki typów. Jeśli ten parametr jest określony, również określić **ComponentFileNameMT** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/TLB** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
|**UpdateFileHashes**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, oblicza wartość skrótu pliki w ścieżce określonej przez **UpdateFileHashesSearchPathMT** parametru zadania, a następnie aktualizuje wartość **skrótu** atrybutu **pliku** element manifestu za pomocą obliczoną wartością.<br /><br /> Aby uzyskać więcej informacji, zobacz **/hashupdate** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web. Zobacz też **UpdateFileHashesSearchPath** parametru w tej tabeli.|  
|**UpdateFileHashesSearchPath**|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę wyszukiwania do użycia podczas aktualizacji plików skrótu. Użyj tego parametru z **UpdateFileHashesMT** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **UpdateFileHashes** parametru w tej tabeli.|  
|**VerboseOutput**|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, wyświetla pełne informacje o debugowaniu.<br /><br /> Aby uzyskać więcej informacji, zobacz **/ verbose** opcji "Mt.exe" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)