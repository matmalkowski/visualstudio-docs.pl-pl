---
title: Jak używać niestandardowych NuGet źródła danych w środowisku połączonym | Dokumentacja firmy Microsoft
author: ghogen
ms.author: ghogen
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Użyj niestandardowego źródła danych dostęp i używanie pakietów NuGet w środowisku połączonym NuGet.
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: douge
ms.openlocfilehash: 71fcf1c3cfb37d783de13514f6a048c3b3711a53
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
#  <a name="use-a-custom-nuget-feed-in-a-connected-environment"></a>Użyj niestandardowych NuGet źródła danych w środowisku połączonym

Źródło danych NuGet oferują wygodny sposób uwzględnienie źródła pakietów w projekcie. Połączonych środowiska musi być w stanie uzyskać dostępu do tego źródła danych w poszukiwaniu zależności jest prawidłowo zainstalowany w kontenerze Docker.

Aby skonfigurować NuGet źródła danych:
1. Dodaj [odwołania pakować](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files) w `*.csproj` plików w obszarze `PackageReference` węzła.

   ```xml
   <ItemGroup>
       <!-- ... -->
       <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0" />
       <!-- ... -->
   </ItemGroup>
   ```

2. Utwórz [NuGet.Config](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file) plików w folderze projektu.
     * Użyj `packageSources` sekcji, aby odwołać programu NuGet źródła lokalizacji. Ważne: Źródło NuGet musi być dostępny publicznie.
     * Użyj `packageSourceCredentials` sekcji, aby skonfigurować poświadczenia użytkownika i hasło. 

   ```xml
   <packageSources>
       <add key="Contoso" value="https://contoso.com/packages/" />
   </packageSources>

   <packageSourceCredentials>
       <Contoso>
           <add key="Username" value="user@contoso.com" />
           <add key="ClearTextPassword" value="33f!!lloppa" />
       </Contoso>
   </packageSourceCredentials>
   ```

3. Jeśli używasz kontroli kodu źródłowego:
    - Odwołanie `NuGet.Config` w Twojej `.gitignore` pliku, poświadczenia nie przypadkowo zatwierdzenia w repozytorium źródła.
    - Otwórz `vsce.yaml` pliku w projekcie, a następnie zlokalizuj `build` sekcji i Wstaw następujący fragment kodu w celu zapewnienia, że `NuGet.Config` plik zostanie zsynchronizowany na platformie Azure, tak aby użyć podczas procesu tworzenia obrazu kontenera. (Domyślnie połączony środowiska nie synchronizuje pliki, które spełniają `.gitignore` i `.dockerignore` reguły.)

        ```yaml
        build:
        useGitIgnore: true
        ignore:
        - “!NuGet.Config”
        ```


## <a name="next-steps"></a>Następne kroki

Po wykonaniu powyższych czynności, przy następnym uruchomieniu `vsce up` (lub kliknij przycisk `F5` VSCode lub Visual Studio), połączone środowisko będzie synchronizować `NuGet.Config` plików na platformie Azure, który następnie jest wykorzystywany przez `dotnet restore` można zainstalować pakietu zależności w kontenerze.

