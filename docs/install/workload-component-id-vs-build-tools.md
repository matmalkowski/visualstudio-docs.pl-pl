---
title: "Visual Studio kompilacji narzędzia 2017 obciążenia i składnik identyfikatorów | Dokumentacja firmy Microsoft"
description: "Użyj identyfikatorów obciążenia i składników programu Visual Studio do tworzenia klasycznych aplikacji opartych na systemie Windows"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 10/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-acquisition
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.openlocfilehash: 4409ca641d35a6276cdbcf48137d48b71b85f58e
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2017
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Visual Studio kompilacji narzędzia 2017 składników katalogu

Tabele zawierają na tej stronie listę identyfikatorów, które można zainstalować program Visual Studio przy użyciu wiersza polecenia. Należy pamiętać, że będą dodawane dodatkowe składniki jako wydania aktualizacji dla programu Visual Studio.

Należy również zauważyć następujące kwestie dotyczące tej strony:

* Każde obciążenie ma osobny rozdział następuje identyfikator obciążenia i spisu składników, które są dostępne dla obciążeń.
* Domyślnie **wymagane** składników zostanie zainstalowany po zainstalowaniu obciążenie. Jeśli zostanie wybrana, można także zainstalować **zalecane** i **opcjonalnie** składników.
* Dodaliśmy również sekcja, która zawiera listę dodatkowych składników, które nie są powiązane z dowolnym obciążeniu.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz [użyć parametrów wiersza polecenia do zainstalowania programu Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) strony. Oraz listę obciążenia i identyfikatory składników dla innych produktów, zobacz [obciążenia 2017 r w usłudze Visual Studio i identyfikatory składników](workload-and-component-ids.md) strony.

## <a name="msbuild-tools"></a>Narzędzia MSBuild

**Identyfikator:** Microsoft.VisualStudio.Workload.MSBuildTools

**Opis:** udostępnia narzędzia potrzebne do tworzenia aplikacji opartych na MSBuild.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.CoreBuildTools | Podstawowe narzędzia kompilacji programu Visual Studio | 15.0.26711.1 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# i Visual Basic Roslyn | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.FSharp.MSBuild | kompilator F# | 15.0.26606.0 | Optional

## <a name="net-core-build-tools"></a>Narzędzia kompilacji platformy .NET core

**Identyfikator:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Opis:** narzędzia do tworzenia aplikacji platformy .NET Core.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | .NET podstawowe narzędzia do programowania 1.0 1.1 | 15.0.26606.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet obiektów docelowych i zadań kompilacji | 15.0.26919.1 | Wymagane
Microsoft.Net.Core.Component.SDK.1x | Oprogramowanie .NET core narzędzi programistycznych 1.0 1.1 dla komputerów typu Desktop | 15.0.26919.1 | Optional

## <a name="visual-c-build-tools"></a>Narzędzia kompilacji w usłudze Visual C++

**Identyfikator:** Microsoft.VisualStudio.Workload.VCTools

**Opis:** tworzenia klasycznych aplikacji opartych na systemie Windows przy użyciu zestawu narzędzi Visual C++ ATL i opcjonalne funkcje, takie jak MFC i C + +/ CLI.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Visual C++ Build Tools podstawowe funkcje | 15.0.26823.1 | Wymagane
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aktualizacji pakietu redystrybucyjnego Visual C++ 2017 r. | 15.0.26606.0 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK | Środowisko wykonawcze systemu Windows Universal C | 15.0.26621.2 | Wymagane
Component.Microsoft.VisualStudio.RazorExtension | Usługi językowe razor | 15.0.26720.2 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języka C# i Visual Basic Roslyn | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.0.26711.1 | Zalecane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Zalecane
Microsoft.VisualStudio.Component.VC.CMake.Project | Narzędzia Visual C++ tools for CMake | 15.0.27004.2002 | Zalecane
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Zestaw narzędzi v141 2017 VC ++ (x86, x64) | 15.0.26823.1 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) dla pulpitu C++ [x86 i x64] | 15.0.27004.2002 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.0.27004.2002 | Zalecane
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) dla platformy uniwersalnej systemu Windows: C++ | 15.0.27004.2002 | Zalecane
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET i sieć web development | 15.0.26606.0 | Zalecane
Microsoft.Component.VC.Runtime.UCRTSDK | Zestaw Windows Universal CRT SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET framework 4.6.1 zestawu SDK | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.6.1 | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.140 | Zestaw narzędzi w wersji 140 2015.3 VC ++ dla komputerów typu desktop (x86, x64) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL — Obsługa | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Obsługa MFC i ATL (x86 i x64) | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (eksperymentalne) | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C + +/ CLI pomocy technicznej | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduły biblioteki standardowej (eksperymentalne) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) dla pulpitu C++ [x86 i x64] | 15.0.26929.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C#, VB, JS | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) dla platformy uniwersalnej systemu Windows: C++ | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Windows 10 SDK (10.0.16299.0) dla pulpitu C++ [ARM i ARM64] | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Zestaw SDK systemu Windows 8.1 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK i Biblioteka UCRT | 15.0.26208.0 | Optional

## <a name="web-development-build-tools"></a>Narzędzia kompilacji programowanie dla sieci Web

**Identyfikator:** Microsoft.VisualStudio.Workload.WebBuildTools

**Opis:** zadania programu MSBuild i elementów docelowych dla tworzenia aplikacji sieci web.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET framework 4.6.1 zestawu SDK | 15.0.26621.2 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.6.1 | 15.0.26621.2 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia do programowania .NET framework 4.6.1 | 15.0.26606.0 | Wymagane
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Narzędzia kompilacji programowanie dla sieci Web | 15.0.26323.1 | Wymagane
Microsoft.Net.Component.4.5.1.TargetingPack | Pakiet docelowy .NET framework 4.5.1 | 15.0.26621.2 | Zalecane
Microsoft.Net.Component.4.5.2.TargetingPack | Pakiet określania wartości docelowej platformy .NET framework 4.5.2 | 15.0.26621.2 | Zalecane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.0.26621.2 | Zalecane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.0.26621.2 | Zalecane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.0.26621.2 | Zalecane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia deweloperskie programu .NET framework 4 — 4.6 | 15.0.26606.0 | Zalecane
Microsoft.Net.Core.Component.SDK | .NET podstawowe narzędzia do programowania 1.0 1.1 | 15.0.26606.0 | Zalecane
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet obiektów docelowych i zadań kompilacji | 15.0.26919.1 | Zalecane
Microsoft.Net.Component.3.5.DeveloperTools | Narzędzia do programowania .NET framework 3.5 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET framework 4.6.2 zestawu SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET framework 4.6.2 docelowego pakietu | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET framework 4.7 zestawu SDK | 15.0.26419.1 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET framework 4.7 targeting pack | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Narzędzia do programowania .NET framework 4.6.2 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Narzędzia do programowania .NET framework 4.7 | 15.0.26606.0 | Optional

## <a name="unaffiliated-components"></a>Odłączony składników

Są to składniki, które nie są dołączone każde obciążenie, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilatory w programie Visual C++ i bibliotek dla ARM | 15.0.26906.1
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilatory w programie Visual C++ i bibliotek dla ARM64 | 15.0.26906.1

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroki rozwiązywania problemów, można skontaktować się nam przez rozmów na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [strony pomocy technicznej programu Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta).

## <a name="see-also"></a>Zobacz także

* [Visual Studio obciążenia i składnik identyfikatorów](workload-and-component-ids.md)
* [Przewodnik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykłady parametru wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie w trybie offline instalację programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
