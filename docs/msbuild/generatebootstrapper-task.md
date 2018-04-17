---
title: Generatebootstrapper — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7b04cbc20876f1a286d40d3e37e7d9e8e2211c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper — Zadanie
Umożliwia automatyczne wykrywanie, pobieranie i instalowanie aplikacji i jego wymagań wstępnych. Służy on jako pojedynczego Instalatora, która integruje się oddzielne pliki instalacyjne dla wszystkich składników tworzących aplikacji.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `GenerateBootstrapper` zadań.  
  
-   `ApplicationFile`  
  
     Opcjonalne `String` parametru.  
  
     Określa plik inicjujący będzie używane do instalowania aplikacji po zainstalowaniu wszystkich wymagań wstępnych. Spowoduje to błąd kompilacji, jeśli żadna `BootstrapperItems` ani `ApplicationFile` parametr jest określony.  
  
-   `ApplicationName`  
  
     Opcjonalne `String` parametru.  
  
     Określa nazwę aplikacji, która zainstaluje program inicjujący. Ta nazwa będzie wyświetlana w Interfejsie użytkownika inicjujący jest używany podczas instalacji.  
  
-   `ApplicationRequiresElevation`  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, składnik jest uruchamiany z podwyższonym poziomem uprawnień, gdy jest zainstalowany na komputerze docelowym.  
  
-   `ApplicationUrl`  
  
     Opcjonalne `String` parametru.  
  
     Określa lokalizację w sieci Web obsługujący Instalatora aplikacji.  
  
-   `BootstrapperComponentFiles`  
  
     Opcjonalne `String[]` parametru wyjściowego.  
  
     Określa lokalizację skompilowanych plików pakietu programu inicjującego.  
  
-   `BootstrapperItems`  
  
     Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.  
  
     Określa produktów, które mają wbudowane w program inicjujący. Elementy przekazanych do tego parametru powinien mieć następującą składnię:  
  
    ```xml  
    <BootstrapperItem  
        Include="ProductCode">  
        <ProductName>  
            ProductName  
        </ProductName>  
    </BootstrapperItem>  
    ```  
  
     `Include` Atrybut jest używany do reprezentowania nazwy wymagań wstępnych, która powinna zostać zainstalowana. `ProductName` Metadanych elementu jest opcjonalna i będzie służyć przez aparat kompilacji jako nazwę przyjazną dla użytkownika w przypadku, gdy nie można odnaleźć pakietu. Te elementy nie są wymagane [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] parametrów wejściowych, o ile nie `ApplicationFile` jest określona. Dla aplikacji, należy uwzględnić jeden element dla każdego wstępnie wymaganego programu, który musi być zainstalowany.  
  
     Spowoduje to błąd kompilacji, jeśli żadna `BootstrapperItems` ani `ApplicationFile` parametr jest określony.  
  
-   `BootstrapperKeyFile`  
  
     Opcjonalne `String` parametru wyjściowego.  
  
     Określa lokalizację wbudowanych setup.exe  
  
-   `ComponentsLocation`  
  
     Opcjonalne `String` parametru.  
  
     Określa lokalizację do wyszukania wymagań wstępnych instalacji zainstalować program inicjujący. Ten parametr może mieć następujące wartości:  
  
    -   `HomeSite`: Wskazuje, że wstępnie wymagane jest obsługiwana przez dostawcę składnika.  
  
    -   `Relative`: Wskazuje, że preqrequisite znajduje się w tej samej lokalizacji aplikacji.  
  
    -   `Absolute`: Wskazuje, że wszystkie składniki znajdują się pod adresem URL scentralizowane. Ta wartość będzie używana w połączeniu z `ComponentsUrl` parametru wejściowego.  
  
     Jeśli `ComponentsLocation` nie zostanie określony, `HomeSite` jest używany domyślnie.  
  
-   `ComponentsUrl`  
  
     Opcjonalne `String` parametru.  
  
     Określa adres URL zawierający wymagania wstępne instalacji.  
  
-   `CopyComponents`  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, inicjujący kopiuje wszystkie pliki wyjściowe do ścieżki określonej w `OutputPath` parametru. Wartości `BootstrapperComponentFiles` parametru wszystkie opierają się na tej ścieżce. Jeśli `false`, pliki nie zostaną skopiowane, a `BootstrapperComponentFiles` wartości są oparte na wartość `Path` parametru.  Wartością domyślną tego parametru jest `true`.  
  
-   `Culture`  
  
     Opcjonalne `String` parametru.  
  
     Określa kulturę na użytek programu inicjującego interfejsu użytkownika i wymagania wstępne instalacji. Jeśli określona kultura jest niedostępny, zadanie używa wartości `FallbackCulture` parametru.  
  
-   `FallbackCulture`  
  
     Opcjonalne `String` parametru.  
  
     Określa kulturę dodatkowej na użytek bootstraper interfejsu użytkownika i wymagania wstępne instalacji.  
  
-   `OutputPath`  
  
     Opcjonalne `String` parametru.  
  
     Określa lokalizację kopii setup.exe i wszystkie pliki pakietu.  
  
-   `Path`  
  
     Opcjonalne `String` parametru.  
  
     Określa lokalizację wszystkie dostępne pakiety wymagań wstępnych.  
  
-   `SupportUrl`  
  
     Opcjonalne `String` parametru.  
  
     Określa adres URL, aby zapewnić w przypadku instalacji programu inicjującego nie  
  
-   `Validate`  
  
     Opcjonalne `Boolean` parametru.  
  
     Jeśli `true`, inicjujący przeprowadza weryfikację XSD elementów określonego programu inicjującego wejściowego. Wartością domyślną tego parametru jest `false`.  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `GenerateBootstrapper` zadanie, aby zainstalować aplikację, którą muszą dysponować [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] zainstalowany jako warunek wstępny.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">  
            <ProductName>Microsoft .NET Framework 2.0</ProductName>  
        </BootstrapperFile>  
    </ItemGroup>  
  
    <Target Name="BuildBootstrapper">  
        <GenerateBootstrapper  
            ApplicationFile="WindowsApplication1.application"  
            ApplicationName="WindowsApplication1"  
            ApplicationUrl="http://mycomputer"  
            BootstrapperItems="@(BootstrapperFile)"  
            OutputPath="C:\output" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)