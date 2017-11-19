---
title: "Instalowanie znajduje się poza folderem rozszerzeń z VSIX v3 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b604a70c44b6fd25888ee5419efbb95f95a0a4a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="installing-outside-the-extensions-folder"></a>Instalowanie znajduje się poza folderem rozszerzeń

Począwszy od wersji programu Visual Studio 2017 i VSIX 3 (wersja 3) obsługuje teraz instalowanie rozszerzeń zasobów poza folderem rozszerzenia. Obecnie następujące lokalizacje są włączone jako lokalizacje prawidłowej instalacji (gdzie [INSTALLDIR] jest mapowany na katalog instalacyjny wystąpienie programu Visual Studio):

* \MSBuild [INSTALLDIR]
* \Xml\Schemas [INSTALLDIR]
* \Common7\IDE\PublicAssemblies [INSTALLDIR]
* \Licenses [INSTALLDIR]
* \Common7\IDE\ReferenceAssemblies [INSTALLDIR]
* \Common7\IDE\RemoteDebugger [INSTALLDIR]
* \Common7\IDE\VC\VCTargets [INSTALLDIR]

>**Uwaga:** format pliku VSIX nie zezwoli na zainstalowanie poza struktura folderów instalacji programu VS.

Aby zapewnić obsługę instalowanie na tych katalogów, pliku VSIX musi być zainstalowana "poszczególnych wystąpień dla maszyny". Można je włączyć, zaznaczając pole wyboru "wszystkich użytkowników" w Projektancie extension.vsixmanifest:

![Sprawdź wszyscy użytkownicy](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Jak ustawić InstallRoot

Aby ustawić katalogi instalacyjne, można użyć **właściwości** okna w programie Visual Studio. Na przykład można ustawić `InstallRoot` właściwości odwołania projektu do jednej z powyższych lokalizacji:

![Zainstaluj właściwości głównej](media/install-root-properties.png)

Spowoduje to dodanie niektóre metadane do odpowiednich `ProjectReference` właściwości wewnątrz pliku .csproj projektu VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Uwaga:** edycji pliku .csproj bezpośrednio, jeśli wolisz.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Jak ustawić podrzędną katalog_główny_instalacji

Jeśli chcesz zainstalować podrzędną poniżej `InstallRoot`, możesz to zrobić przez ustawienie `VsixSubPath` podobnie jak właściwość `InstallRoot` właściwości. Na przykład chcemy dane wyjściowe nasze odwołanie projektu do zainstalowania "[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0". Firma Microsoft to łatwo zrobić przy użyciu projektanta właściwości:

![zestaw podrzędną](media/set-subpath.png)

Odpowiednie zmiany .csproj będzie wyglądać następująco:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Dodatkowe informacje

Zmiany projektanta właściwości są stosowane do więcej niż tylko odwołania do projektu; można ustawić `InstallRoot` metadanych dla elementów wewnątrz projektu również (przy użyciu tych samych metod opisanych powyżej).
