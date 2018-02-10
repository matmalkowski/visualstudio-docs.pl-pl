---
title: "Zastępowanie ustawień ToolsVersion | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f1efc774b4eb0c98ef6c5de36864dfc092133b52
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="overriding-toolsversion-settings"></a>Zastępowanie ustawień ToolsVersion
Można zmienić zestaw narzędzi dla projektów i rozwiązań w jeden z trzech sposobów:  
  
1.  za pomocą `/ToolsVersion` przełącznika (lub `/tv`, skrócie) podczas budowania projektu lub rozwiązania z wiersza polecenia  
  
2.  przez ustawienie `ToolsVersion` parametru na zadanie programu MSBuild  
  
3.  przez ustawienie `$(ProjectToolsVersion)` właściwości projektu w rozwiązaniu. Dzięki temu można utworzyć projektu w rozwiązaniu z zestawem narzędzi w wersji, która różni się od innych projektów.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Zastępowanie ustawień ToolsVersion projektów i rozwiązań w przypadku kompilacji wiersza polecenia  
 Chociaż projektów programu Visual Studio zwykle kompilacji z ToolsVersion określony w pliku projektu, można użyć `/ToolsVersion` (lub `/tv`) przełącznik w wierszu polecenia, aby zastąpić tę wartość i wszystkich projektów i ich projekt projekt kompilacji zależności z innego zestawu narzędzi. Na przykład:  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 W tym przykładzie wszystkie projekty zostały skompilowane przy użyciu ToolsVersion 12.0. (Jednak, zobacz sekcję "Kolejność pierwszeństwa" w dalszej części tego tematu).  
  
 Korzystając z `/tv` przełącznik w wierszu polecenia, można opcjonalnie użyć `$(ProjectToolsVersion)` właściwości w poszczególnych projektach je kompilować, podając inną wartość ToolsVersion niż innych projektów w rozwiązaniu.  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Zastąp ustawienia ToolsVersion przy użyciu parametru ToolsVersion zadania MSBuild  
 Zadanie programu MSBuild jest podstawowym elementem używanym dla jednego projektu do tworzenia drugiego. Aby włączyć zadanie programu MSBuild utworzyć projekt z różnych ToolsVersion niż określona w projekcie, zapewnia parametr opcjonalny zadań o nazwie `ToolsVersion`. W poniższym przykładzie pokazano sposób użycia tego parametru:  
  
1.  Utwórz plik o nazwie `projectA.proj` zawierający następujący kod:  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2.  Utwórz innego pliku o nazwie `projectB.proj` zawierający następujący kod:  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3.  Wprowadź następujące polecenie w wierszu polecenia:  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4.  Zostaną wyświetlone następujące dane wyjściowe. Dla `projectA`, `/toolsversion:3.5` zastępuje ustawienie w wierszu polecenia `ToolsVersion=12.0` w `Project` tagu.  
  
     `ProjectB`Metoda jest wywoływana przez zadanie w `projectA`. To zadanie ma `ToolsVersion=2.0`, która zastępuje innych `ToolsVersion` ustawienia `projectB`.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## <a name="order-of-precedence"></a>Hierarchia ważności  
 Kolejność pierwszeństwa, w kolejności malejącej, używany do określenia `ToolsVersion` jest:  
  
1.  `ToolsVersion` Atrybut używany do tworzenia projektu, jeśli zadanie programu MSBuild.  
  
2.  `/toolsversion` (Lub `/tv`) przełącznik, który jest używany w poleceniu msbuild.exe, jeśli istnieje.  
  
3.  Jeśli zmienna środowiskowa `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` jest ustawiona, a następnie użyj bieżącego `ToolsVersion`.  
  
4.  Jeśli zmienna środowiskowa `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` ustawiono i `ToolsVersion` zdefiniowane w projekcie plików jest większa niż bieżąca `ToolsVersion`, korzystanie z bieżącego `ToolsVersion`.  
  
5.  Jeśli zmienna środowiskowa `MSBUILDLEGACYDEFAULTTOOLSVERSION` jest ustawiona, lub jeśli `ToolsVersion` nie jest ustawiona, a następnie są używane następujące kroki:  
  
    1.  `ToolsVersion` Atrybutu [projektu](../msbuild/project-element-msbuild.md) element pliku projektu. Jeśli ten atrybut nie istnieje, przyjmowana jest wartość bieżącej wersji.  
  
    2.  Domyślnej wersji narzędzi w pliku MSBuild.exe.config.  
  
    3.  Domyślnej wersji narzędzi w rejestrze. Aby uzyskać więcej informacji, zobacz [standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6.  Jeśli zmienna środowiskowa `MSBUILDLEGACYDEFAULTTOOLSVERSION` nie jest ustawiona, a następnie są używane następujące kroki:  
  
    1.  Jeśli zmienna środowiskowa `MSBUILDDEFAULTTOOLSVERSION` ustawiono `ToolsVersion` który istnieje, z niego korzystać.  
  
    2.  Jeśli `DefaultOverrideToolsVersion` jest ustawiony w MSBuild.exe.config, z niego korzystać.  
  
    3.  Jeśli `DefaultOverrideToolsVersion` jest ustawiony w rejestrze, z niego korzystać.  
  
    4.  W przeciwnym razie Użyj bieżącego `ToolsVersion`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przeznaczanie dla wielu platform](../msbuild/msbuild-multitargeting-overview.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Konfiguracje standardowego i niestandardowego zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md)