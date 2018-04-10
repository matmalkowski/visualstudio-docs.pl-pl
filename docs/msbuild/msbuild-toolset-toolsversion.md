---
title: Zestaw narzędzi MSBuild (ToolsVersion) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/31/2018
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e274fa60ff209436be9d11f52464d7b42972ef47
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="msbuild-toolset-toolsversion"></a>Zestaw narzędzi MSBuild (ToolsVersion)
Program MSBuild używa zestawu narzędzi zadań, elementy docelowe i narzędzia do tworzenia aplikacji. Zazwyczaj narzędzi MSBuild zawiera plik microsoft.common.tasks, microsoft.common.targets i kompilatory, takie jak csc.exe i vbc.exe. Większość procesami może służyć do skompilowania aplikacji, aby więcej niż jedna wersja programu .NET Framework i więcej niż jednej platformie systemu. Jednak zestaw narzędzi MSBuild 2.0 może służyć do mają być stosowane tylko programu .NET Framework 2.0.  
  
## <a name="toolsversion-attribute"></a>ToolsVersion — atrybut  
 Określ zestaw narzędzi w `ToolsVersion` atrybutu [projektu](../msbuild/project-element-msbuild.md) elementu w pliku projektu. Poniższy przykład określa, że projekt powinny zostać skompilowane przy użyciu zestawu narzędzi 15.0 MSBuild.  
  
```xml  
<Project ToolsVersion="15.0" ... </Project>  
``` 

> [!NOTE] 
> Użyj typów niektórych projektu `sdk` atrybutu zamiast `ToolsVersion`. Aby uzyskać więcej informacji, zobacz [pakietów, metadane i platform](/dotnet/core/packages) i [dodatki do csproj format .NET Core](/dotnet/core/tools/csproj).
  
## <a name="how-the-toolsversion-attribute-works"></a>Jak działa ten atrybut ToolsVersion  
 Podczas tworzenia projektu w programie Visual Studio lub uaktualnienie istniejącego projektu o nazwie atrybutu `ToolsVersion` jest automatycznie uwzględnione w projekcie plików i jej wartość odpowiada to wersji programu MSBuild, który znajduje się w wersji Visual Studio. Aby uzyskać więcej informacji, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Gdy `ToolsVersion` wartość jest zdefiniowana w pliku projektu, program MSBuild używa tej wartości w celu określenia wartości właściwości zestawu narzędzi, które są dostępne do projektu. Jedna właściwość zestawu narzędzi jest `$(MSBuildToolsPath)`, który określa ścieżkę narzędzia .NET Framework. Tej właściwości zestawu narzędzi (lub `$(MSBuildBinPath)`), jest wymagana.  
  
 Począwszy od programu Visual Studio 2013, wersja zestawu narzędzi MSBuild jest taki sam jak numer wersji Visual Studio. Domyślnie ten zestaw narzędzi w programie Visual Studio i w wierszu polecenia, niezależnie od wersji zestawu narzędzi, określona w pliku projektu MSBuild.  To zachowanie można przesłonić przy użyciu flagi /ToolsVersion. Aby uzyskać więcej informacji, zobacz [Zastępowanie ustawienia ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 W poniższym przykładzie MSBuild znajduje przy użyciu pliku Microsoft.CSharp.targets `MSBuildToolsPath` zastrzeżone właściwości.  
  
```xml  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Można zmodyfikować wartości `MSBuildToolsPath` przez zdefiniowanie niestandardowego zestawu narzędzi. Aby uzyskać więcej informacji, zobacz [standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md)  
  
 Podczas tworzenia rozwiązania w wierszu polecenia i określić `ToolsVersion` msbuild.exe, wszystkie projekty oraz ich zależności projektu do projektu są tworzone zgodnie z którym `ToolsVersion`nawet w przypadku każdego projektu w rozwiązaniu określa własnej `ToolsVersion`. Aby zdefiniować `ToolsVersion` wartość dla projektu, zobacz [Zastępowanie ustawienia ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 `ToolsVersion` Atrybut służy do migracji projektu. Na przykład po otwarciu projektu programu Visual Studio 2008 w Visual Studio 2010 pliku projektu została zaktualizowana do ToolsVersion = "4.0". Jeśli następnie spróbuj otworzyć tego projektu w programie Visual Studio 2008, nie rozpoznaje uaktualnionego `ToolsVersion` i w związku z tym tworzy projekt tak, jakby nadal ustawiono atrybut 3.5.  
  
 Visual Studio 2010 i Visual Studio 2012 Użyj ToolsVersion 4.0. ToolsVersion 12.0 korzysta z programu Visual Studio 2013. Visual Studio 2015 korzysta ToolsVersion 14.0 i Visual Studio 2017 używa ToolsVersion 15.0. W wielu przypadkach można otworzyć projektu w różnych wersjach programu Visual Studio bez żadnych modyfikacji. Visual Studio zawsze używa poprawny zestaw narzędzi, ale powiadomienie, jeśli używana wersja nie jest zgodna z wersją w pliku projektu. W większości przypadków to ostrzeżenie jest niegroźne procesami są zgodne w większości przypadków.  
  
 Zezwalaj na podzestawach, które zostały opisane w dalszej części tego tematu, MSBuild, aby automatycznie przełącznika, który zestaw narzędzi do użycia na podstawie kontekstu w którym jest uruchamiana kompilacji. Na przykład program MSBuild używa nowszej zestaw narzędzi podczas uruchamiania niż po jej uruchomieniu w programie Visual Studio 2010, bez konieczności jawnego zmiany pliku projektu w programie Visual Studio 2012.  
  
## <a name="toolset-implementation"></a>Zestaw narzędzi implementacji  
 Implementuje zestawu narzędzi, wybierając ścieżek różnych narzędzi, cele i zadania, które tworzą zestaw narzędzi. Narzędzia w zestawie narzędzi, który definiuje MSBuild pochodzą z następujących źródeł:  
  
-   Folder .NET Framework.  
  
-   Dodatkowe narzędzia zarządzanych.  
  
 Narzędzia zarządzanych obejmują ResGen.exe i TlbImp.exe.  
  
 MSBuild zapewnia dostęp do zestawu narzędzi na dwa sposoby:  
  
-   Za pomocą właściwości zestawu narzędzi  
  
-   Za pomocą <xref:Microsoft.Build.Utilities.ToolLocationHelper> metod  
  
 Właściwości zestawu narzędzi, określ ścieżki narzędzi. Począwszy od programu Visual Studio 2017 MSBuild już ma położenie ustalone. Domyślnie znajduje się w folderze MSBuild\15.0\Bin względną wobec lokalizacji instalacji programu Visual Studio. We wcześniejszych wersjach programu MSBuild używa wartości `ToolsVersion` atrybutu w pliku projektu, aby zlokalizować odpowiedni klucz rejestru, a następnie używa informacji w kluczu rejestru można ustawić właściwości zestawu narzędzi. Na przykład jeśli `ToolsVersion` ma wartość `12.0`, a następnie MSBuild ustawia właściwości zestawu narzędzi, zgodnie z tego klucza rejestru: HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0.  
  
 Są to zestaw narzędzi właściwości:  
  
-   `MSBuildToolsPath` Ścieżka plików binarnych programu MSBuild.  
  
-   `SDK40ToolsPath` Określa ścieżkę dodatkowe narzędzia zarządzanych dla MSBuild 4.x (co może być 4.0 i 4.5).  
  
-   `SDK35ToolsPath` Określa ścieżkę dodatkowe narzędzia zarządzanego programu MSBuild 3.5.  
  
 Alternatywnie można określić zestaw narzędzi programowo przez wywołanie metody <xref:Microsoft.Build.Utilities.ToolLocationHelper> klasy. Klasa zawiera następujące metody:  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> zwraca ścieżkę folderu .NET Framework.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> zwraca ścieżkę do pliku w folderze .NET Framework.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> zwraca ścieżkę do folderu Narzędzia zarządzanych.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> zwraca ścieżkę pliku, który zazwyczaj znajduje się w folderze Narzędzia zarządzanych.  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToBuildTools%2A> zwraca ścieżkę narzędzia kompilacji.  
  
### <a name="sub-toolsets"></a>Podzestawach  
 Dla wersji programu MSBuild przed 15.0 MSBuild korzysta z klucza rejestru do określenia ścieżki podstawowe narzędzia. Jeśli klucz ma podklucz, MSBuild używa go do określenia ścieżki sub narzędzi, który zawiera dodatkowe narzędzia. W takim przypadku zestaw narzędzi jest zdefiniowany przez połączenie definicji właściwości, które są zdefiniowane w obydwu kluczy.  
  
> [!NOTE]
>  Jeśli powodują kolizję nazw właściwości zestawu narzędzi, wartość, która jest zdefiniowana dla ścieżki podkluczy zastępuje wartość, która jest zdefiniowana w ścieżce klucza głównego.  
  
 Podzestawach stają się aktywne w obecności z `VisualStudioVersion` kompilacji właściwości. Ta właściwość może mieć jedną z następujących wartości:  
  
-   Określa "10.0" sub-zestaw narzędzi platformy .NET Framework 4  
  
-   Określa "11.0" sub-zestaw narzędzi platformy .NET Framework 4.5  
  
-   Określa "12,0" sub-zestaw narzędzi platformy .NET Framework 4.5.1 
  
 Podzestawach 10.0 i 11.0 powinien być używany z ToolsVersion 4.0. W nowszych wersjach wersję zestawu narzędzi podkluczy i wartości ToolsVersion powinna być zgodna.  
  
 Podczas kompilacji MSBuild automatycznie określa i ustawia wartość domyślną dla `VisualStudioVersion` właściwość, o ile jeszcze nie jest zdefiniowany.  
  
 MSBuild zapewnia przeciążenia dla `ToolLocationHelper` metod, które dodać `VisualStudioVersion` wyliczyć wartość jako parametr  
  
 Podzestawach wprowadzono w programie .NET Framework 4.5.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfiguracje standardowego i niestandardowego zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)
