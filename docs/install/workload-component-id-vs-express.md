---
title: Visual Studio Desktop Express 2017 obciążeń i składników identyfikatorów
description: Użyj obciążenia i identyfikatory składników, aby zainstalować program Visual Studio przy użyciu wiersza polecenia lub określić jako zależności w manifestu VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 08/14/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.workload:
- multiple
ms.openlocfilehash: 5250166a1cccf0b46e533ad4ed22b28454c1ac33
ms.sourcegitcommit: 2b1f8e5288582367af2bed20848ba556f146716e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42623924"
---
# <a name="visual-studio-2017-desktop-express-component-directory"></a>Visual Studio 2017 Desktop Express składników katalogu

Tabele na tej stronie listy identyfikatorów, w której można zainstalować program Visual Studio przy użyciu wiersza polecenia lub można określić jako zależności w manifestu VSIX. Należy pamiętać, że dodamy dodatkowe składniki, jak wydaniu aktualizacji do programu Visual Studio.

Ponadto należy pamiętać, że informacje o stronie:

* Każde obciążenie ma osobny rozdział, następuje identyfikator obciążenia i tabeli składników, które są dostępne dla obciążenia.
* Domyślnie **wymagane** składniki zostaną zainstalowane po zainstalowaniu obciążenia.
* Jeśli chcesz, możesz także zainstalować **zalecane** i **opcjonalnie** składników.
* Dodaliśmy również sekcję, która zawiera listę dodatkowych składników, które nie są powiązane z dowolnych obciążeń.

Po ustawieniu współzależności w manifeście VSIX tylko należy określić identyfikatory składników. Użyj tabel na tej stronie, aby określić nasze zależności minimalnej składnika. W niektórych scenariuszach to oznaczać, że należy określić tylko jeden składnik z obciążenia. W innych przypadkach może oznaczać, możesz określić wiele składników z pojedynczego obciążenia lub wielu składników z wielu obciążeń. Aby uzyskać więcej informacji, zobacz [instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) strony.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz [Użyj parametry wiersza polecenia, aby zainstalować program Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) strony. I dla listy, obciążenie i identyfikatorów składników dla innych produktów, zobacz [Visual Studio 2017 obciążenia i identyfikatory składnika](workload-and-component-ids.md) strony.

## <a name="express-for-windows-desktop"></a>Express for Windows Desktop

**ID:** Microsoft.VisualStudio.Workload.WDExpress

**Opis:** Twórz aplikacje natywne i zarządzane, takie jak WPF, WinForms i Win32 z kodu uwzględniającej składnię, edytowanie, kontroli kodu źródłowego i zarządzanie elementami roboczymi. Obejmuje obsługę języka C#, Visual Basic i Visual C++.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Publikowania ClickOnce | 15.8.27825.0 | Wymagane
Microsoft.Component.HelpViewer | Podgląd pomocy | 15.6.27323.2 | Wymagane
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Wymagane
Microsoft.Component.VC.Runtime.OSSupport | Środowisko uruchomieniowe Visual C++ dla platformy uniwersalnej systemu Windows | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.1.TargetingPack | .NET framework 4.5.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.2.TargetingPack | .NET framework 4.5.2 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.5.TargetingPack | .NET framework 4.5 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.SDK | Program .NET framework 4.6.1 zestawu SDK | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.1.TargetingPack | Platformy .NET framework 4.6.1 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.6.TargetingPack | .NET framework 4.6 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.Component.4.TargetingPack | .NET framework 4 targeting pack | 15.6.27406.0 | Wymagane
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Narzędzia programistyczne programu .NET framework 4.6.1 | 15.8.27825.0 | Wymagane
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Narzędzia programistyczne programu .NET framework 4 – 4.6 | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Common.Azure.Tools | Narzędzia łączności i publikowania | 1.10.50912.1 | Wymagane
Microsoft.VisualStudio.Component.CoreEditor | Edytor rdzeni programu Visual Studio | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 tools | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.NuGet | Menedżer pakietów NuGet | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.Compiler | Kompilatory języków C# i Visual Basic Roslyn | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# i Visual Basic | 15.8.27729.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.ADAL | Środowisko uruchomieniowe SQL ADAL | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.CLR | Typy danych CLR dla programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.CMDUtils | Narzędzia wiersza polecenia programu SQL Server | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.DataSources | Źródła danych na potrzeby obsługi programu SQL Server | 15.0.26621.2 | Wymagane
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Wymagane
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.7.27625.0 | Wymagane
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Narzędzia do analizy statycznej | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.TextTemplating | Przekształcenia szablonu tekstu | 15.0.26208.0 | Wymagane
Microsoft.VisualStudio.Component.VC.CLI.Support | C + +/ interfejsu wiersza polecenia | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.ARM | Kompilatory języka Visual C++ i bibliotek dla ARM | 15.8.27825.0 | Wymagane
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Kompilatory języka Visual C++ i bibliotek dla architektury ARM64 | 15.6.27309.0 | Wymagane
Microsoft.VisualStudio.Component.VisualStudioData | Źródła danych i odwołania do usług | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK.14393 | System Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.Windows10SDK.17134 | System Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Wymagane

## <a name="unaffiliated-components"></a>Składniki nie podlega

Są to składniki, które nie są uwzględniane przy użyciu dowolnego obciążenia, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
n/d | n/d | n/d

## <a name="get-support"></a>Uzyskaj pomoc techniczną

Czasami mogą wystąpić problemy. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) strony. Jeśli żaden z kroków rozwiązywania problemów pomoże, możesz skontaktować nam się przez czat na żywo, aby uzyskać pomoc przy instalacji (tylko w języku angielskim). Aby uzyskać więcej informacji, zobacz [stronę pomocy technicznej programu Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Poniżej przedstawiono kilka więcej opcji pomocy technicznej:

* Możesz zgłosić problemy z produktu z nami za pośrednictwem [Zgłoś Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Możesz udostępnić sugestię dotyczącą produktu z nami w [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Możesz śledzić problemy z produktu i Szukaj odpowiedzi w [społeczności deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/).
* Można także nawiązać kontakt z nami i innych deweloperów programu Visual Studio za pośrednictwem [konwersacji programu Visual Studio community dotyczącym oprogramowania Gitter](https://gitter.im/Microsoft/VisualStudio). (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
