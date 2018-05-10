---
title: Visual Studio kompilacji narzędzia 2017 obciążenia i składnik identyfikatorów
description: Użyj identyfikatorów obciążenia i składników programu Visual Studio do tworzenia klasycznych aplikacji opartych na systemie Windows
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 05/07/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.workload:
- multiple
ms.openlocfilehash: 8634017862a12b3a399f003d6f16c9689b7aaa20
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Visual Studio kompilacji narzędzia 2017 składników katalogu

Tabele na tej stronie listy identyfikatorów, w której można zainstalować program Visual Studio przy użyciu wiersza polecenia lub można określić jako zależności w manifeście VSIX. Należy pamiętać, że będą dodawane dodatkowe składniki jako wydania aktualizacji dla programu Visual Studio.

Należy również zauważyć następujące informacje o stronie:

* Każde obciążenie ma osobny rozdział następuje identyfikator obciążenia i spisu składników, które są dostępne dla obciążeń.
* Domyślnie **wymagane** składników zostanie zainstalowany po zainstalowaniu obciążenie.
* Jeśli zostanie wybrana, można także zainstalować **zalecane** i **opcjonalnie** składników.
* Dodaliśmy również sekcja, która zawiera listę dodatkowych składników, które nie są powiązane z dowolnym obciążeniu.

Po ustawieniu zależności w manifeście VSIX, należy określić tylko identyfikatory składników. Użyj tabel na tej stronie, aby określić naszych zależności minimalna składnika. W niektórych scenariuszach może to oznaczać, że możesz określić tylko jeden składnik od obciążenia. W innych sytuacjach może oznaczać, możesz określić wiele składników z pojedyncze obciążenie lub wielu składników z wiele obciążeń. Aby uzyskać więcej informacji, zobacz [porady: Migracja projektów rozszerzalności programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) strony.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz [użyć parametrów wiersza polecenia do zainstalowania programu Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) strony. Oraz listę obciążenia i identyfikatory składników dla innych produktów, zobacz [obciążenia 2017 r w usłudze Visual Studio i identyfikatory składników](workload-and-component-ids.md) strony.

## <a name="azure-development-build-tools"></a>Narzędzia kompilacji rozwoju platformy Azure

**Identyfikator:** Microsoft.VisualStudio.Workload.AzureBuildTools

**Opis:** MSBuild zadań i obiekty docelowe do tworzenia aplikacji platformy Azure.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.6.1 | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia do programowania .NET framework 4.6.1 | 15.7.27520.0 | Wymagane
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.0.26621.2 | Wymagane
Microsoft.VisualStudio.Component.Azure.ClientLibs | Biblioteki Azure dla platformy .NET | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Usługi w chmurze Azure narzędzi kompilacji | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia deweloperskie kontenera — narzędzia kompilacji | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet obiektów docelowych i zadań kompilacji | 15.0.26919.1 | Wymagane
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie WCF | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie dla sieci Web | 15.7.27604.0 | Wymagane
Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet docelowy .NET framework 4.5.1 | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.5.2 | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia deweloperskie programu .NET framework 4 — 4.6 | 15.6.27406.0 | Zalecane
Microsoft.Net.Core.Component.SDK | Narzędzia do programowania .NET core 2.0 | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje platformy ASP.NET | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 zestawu SDK | 15.0.27617.1 | Zalecane
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia do programowania .NET framework 3.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 docelowego pakietu | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 docelowego pakietu | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia do programowania .NET framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia do programowania .NET framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia do programowania .NET framework 4.7 | 15.6.27406.0 | Optional

## <a name="net-desktop-build-tools"></a>Narzędzia kompilacji pulpitu .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**Opis:** narzędzia do tworzenia WPF, formularze systemu Windows i aplikacji konsoli przy użyciu języka C#, VB i F #.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.6.1 | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet obiektów docelowych i zadań kompilacji | 15.0.26919.1 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.Component.ClickOnce.MSBuild | Narzędzia kompilacji ClickOnce | 15.7.27617.1 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet docelowy .NET framework 4.5.1 | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.5.2 | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia deweloperskie programu .NET framework 4 — 4.6 | 15.6.27406.0 | Zalecane
Microsoft.Net.Core.Component.SDK | Narzędzia do programowania .NET core 2.0 | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.TestTools.BuildTools | Narzędzia do testowania podstawowe funkcje — narzędzia kompilacji | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie WCF | 15.6.27309.0 | Zalecane
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia do programowania .NET framework 3.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 docelowego pakietu | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 docelowego pakietu | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia do programowania .NET framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia do programowania .NET framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia do programowania .NET framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET podstawowe narzędzia do programowania 1.0 1.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.FSharp.MSBuild | kompilator F# | 15.7.27604.0 | Optional

## <a name="msbuild-tools"></a>Narzędzia MSBuild

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**Opis:** udostępnia narzędzia potrzebne do tworzenia aplikacji opartych na MSBuild.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.VisualStudio.Component.CoreBuildTools | Podstawowe narzędzia kompilacji programu Visual Studio | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane

## <a name="net-core-build-tools"></a>Narzędzia kompilacji platformy .NET core

**ID:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Opis:** narzędzia do tworzenia aplikacji przy użyciu platformy .NET Core, platformy ASP.NET Core, HTML/JavaScript i kontenerów.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Narzędzia do programowania .NET core 2.0 | 15.6.27406.0 | Wymagane
Microsoft.NetCore.BuildTools.ComponentGroup | Narzędzia kompilacji platformy .NET core | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet obiektów docelowych i zadań kompilacji | 15.0.26919.1 | Wymagane
Microsoft.Net.Core.Component.SDK.1x | .NET podstawowe narzędzia do programowania 1.0 1.1 | 15.6.27406.0 | Optional

## <a name="nodejs-build-tools"></a>Narzędzia node.js kompilacji

**ID:** Microsoft.VisualStudio.Workload.NodeBuildTools

**Opis:** tworzyć aplikacje skalowalne sieci przy użyciu środowiska Node.js, asynchroniczne sterowane zdarzeniami środowiska wykonawczego języka JavaScript.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Obsługa środowiska node.js | 15.6.27406.0 | Wymagane

## <a name="officesharepoint-build-tools"></a>Narzędzia kompilacji Office i SharePoint

**Identyfikator:** Microsoft.VisualStudio.Workload.OfficeBuildTools

**Opis:** kompilacji pakietu Office i programu SharePoint dodatków i dodatkach VSTO.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.ClickOnce.MSBuild | Narzędzia kompilacji ClickOnce | 15.7.27617.1 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.5.2 | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.6.1 | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia do programowania .NET framework 4.6.1 | 15.7.27520.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet obiektów docelowych i zadań kompilacji | 15.0.26919.1 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Narzędzia kompilacji programowanie Office i SharePoint | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie WCF | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie dla sieci Web | 15.7.27604.0 | Wymagane
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | Narzędzia kompilacji programu Visual Studio Tools dla pakietu Office (środowisko VSTO) | 15.7.27617.1 | Zalecane
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 docelowego pakietu | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 docelowego pakietu | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia do programowania .NET framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia do programowania .NET framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia do programowania .NET framework 4.7 | 15.6.27406.0 | Optional

## <a name="universal-windows-platform-build-tools"></a>Narzędzia kompilacji uniwersalnych platformy systemu Windows

**Identyfikator:** Microsoft.VisualStudio.Workload.UniversalBuildTools

**Opis:** udostępnia narzędzia potrzebne do tworzenia aplikacji platformy uniwersalnej systemu Windows.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Component.NetFX.Native | Architektura .NET Native | 15.0.26208.0 | Wymagane
Microsoft.Component.VC.Runtime.OSSupport | Środowiska uruchomieniowego Visual C++ dla platformy uniwersalnej systemu Windows | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet obiektów docelowych i zadań kompilacji | 15.0.26919.1 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilatory w programie Visual C++ i bibliotek dla ARM | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 wersji 15.7 v14.14 najnowsze v141 narzędzia | 15.7.27625.0 | Wymagane
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | Wymagania wstępne dotyczące uniwersalnych platformy systemu Windows kompilacji | 15.7.27703.1 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional

## <a name="visual-c-build-tools"></a>Narzędzia kompilacji w usłudze Visual C++

**ID:** Microsoft.VisualStudio.Workload.VCTools

**Opis:** tworzenia aplikacji klasycznych systemu Windows przy użyciu zestawu narzędzi firmy Microsoft C++ ATL i MFC.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Visual C++ Build Tools podstawowe funkcje | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aktualizacji pakietu redystrybucyjnego Visual C++ 2017 r. | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC ++ 2017 wersji 15.7 v14.14 najnowsze v141 narzędzia | 15.7.27625.0 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK | Środowisko wykonawcze systemu Windows Universal C | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.TestTools.BuildTools | Narzędzia do testowania podstawowe funkcje — narzędzia kompilacji | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Zalecane
Microsoft.Component.VC.Runtime.UCRTSDK | Zestaw Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.6.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | Zestaw narzędzi v14.00 (w wersji 140) 2015.3 VC ++ dla komputerów typu desktop | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL dla x86 i x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Visual C++ MFC dla x86 i x64 | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C + +/ CLI pomocy technicznej | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduły biblioteki standardowej (eksperymentalne) | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilatory w programie Visual C++ i bibliotek dla ARM | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilatory w programie Visual C++ i bibliotek dla ARM64 | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) dla pulpitu C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) dla pulpitu C++ [x86 i x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.WinXP | Obsługa systemu Windows XP dla języka C++ | 15.7.27703.1 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK i Biblioteka UCRT | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Obsługa systemu Windows XP dla języka C++ | 15.7.27703.1 | Optional

## <a name="web-development-build-tools"></a>Narzędzia kompilacji programowanie dla sieci Web

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**Opis:** zadania programu MSBuild i elementów docelowych dla tworzenia aplikacji sieci web.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.6.1 | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia do programowania .NET framework 4.6.1 | 15.7.27520.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet obiektów docelowych i zadań kompilacji | 15.0.26919.1 | Wymagane
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie dla sieci Web | 15.7.27604.0 | Wymagane
Microsoft.Component.ClickOnce.MSBuild | Narzędzia kompilacji ClickOnce | 15.7.27617.1 | Zalecane
Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet docelowy .NET framework 4.5.1 | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.5.2 | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia deweloperskie programu .NET framework 4 — 4.6 | 15.6.27406.0 | Zalecane
Microsoft.Net.Core.Component.SDK | Narzędzia do programowania .NET core 2.0 | 15.6.27406.0 | Zalecane
Microsoft.VisualStudio.Component.AspNet45 | Zaawansowane funkcje platformy ASP.NET | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Narzędzia deweloperskie kontenera — narzędzia kompilacji | 15.7.27617.1 | Zalecane
Microsoft.VisualStudio.Component.TestTools.BuildTools | Narzędzia do testowania podstawowe funkcje — narzędzia kompilacji | 15.7.27625.0 | Zalecane
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 zestawu SDK | 15.0.27617.1 | Zalecane
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie WCF | 15.6.27309.0 | Zalecane
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia do programowania .NET framework 3.5 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 docelowego pakietu | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET framework 4.7.1 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET framework 4.7.1 docelowego pakietu | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia do programowania .NET framework 4.6.2 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Narzędzia do programowania .NET framework 4.7.1 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia do programowania .NET framework 4.7 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET podstawowe narzędzia do programowania 1.0 1.1 | 15.6.27406.0 | Optional

## <a name="mobile-development-with-net"></a>Programowanie przenośnych z platformą .NET

**Identyfikator:** Microsoft.VisualStudio.Workload.XamarinBuildTools

**Opis:** narzędzia do tworzenia aplikacji dla wielu platform dla systemu iOS, Android i Windows za pomocą języka C# i F #.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.6.1 | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet obiektów docelowych i zadań kompilacji | 15.0.26919.1 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Component.JavaJDK | Zestaw Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | Zalecane
Component.Android.SDK25 | Instalacja zestawu SDK systemu android (interfejs API na poziomie 25) | 15.6.27413.0 | Optional

## <a name="unaffiliated-components"></a>Odłączony składników

Są to składniki, które nie są dołączone każde obciążenie, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 zestawu SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 zestawu SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 zestawu SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 zestawu SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript 2.6 zestawu SDK | 15.0.27520.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | Visual C++ ATL dla ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Visual C++ ATL dla ARM z Spectre środki zaradcze | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | Visual C++ ATL dla ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Visual C++ ATL dla ARM64 z Spectre środki zaradcze | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Visual C++ ATL (x86/x64) z Spectre środki zaradcze | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Visual C++ MFC dla x86/x64 z Spectre środki zaradcze | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (eksperymentalne) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | Visual C++ MFC dla ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Visual C++ MFC dla ARM z Spectre środki zaradcze | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | Visual C++ MFC dla ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Visual C++ MFC obsługę ARM64 z Spectre środki zaradcze | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | VC ++ 2017 wersji 15.7 v14.14 biblioteki Spectre (ARM) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | VC ++ 2017 wersji 15.7 v14.14 biblioteki dla Spectre (ARM64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | VC ++ 2017 wersji 15.7 v14.14 biblioteki dla Spectre (x86 i x64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Zestaw narzędzi v14.11 wersji 15.4 2017 VC ++ | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Zestaw narzędzi v14.12 wersji 15,5 cala 2017 VC ++ | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | Zestaw narzędzi v14.13 wersji 15,6 2017 VC ++ | 15.0.27625.0

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu i odpowiedzi w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/).
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Przewodnik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
