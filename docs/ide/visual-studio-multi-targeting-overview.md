---
title: Docelowy program .NET Framework w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/06/2018
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 00f6baad44b4276ed4de81a2fd55c4f5b9d1c8a2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-multi-targeting-overview"></a>Visual Studio omówienie wielowersyjności kodu

W programie Visual Studio można określić wersji lub profilu .NET Framework, która ma projektu pod kątem. Dla aplikacji do uruchomienia na innym komputerze, Framework w wersji celów aplikacji musi być zgodna z wersją Framework jest zainstalowana na komputerze.

Rozwiązanie zawiera projekty można również utworzyć różne wersje tego docelowej platformy. Docelowy Framework pomaga zagwarantować, że aplikacja używa tylko funkcje, które są dostępne w określonej wersji platformy.

> [!TIP]
> Możesz też określić aplikacje dla różnych platform. Aby uzyskać więcej informacji, zobacz [przeznaczanie dla wielu platform](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Framework przeznaczonych dla funkcji

Docelowy Framework obejmuje następujące funkcje:

- Po otwarciu projektu, który jest przeznaczony dla starszej wersji programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio można automatycznie uaktualnić go lub pozostaw cel jako — jest.

- Podczas tworzenia projektu można określić wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , który ma być docelowa.

- Można zmienić wersję [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] czy istniejącego projektu elementów docelowych.

- Celem może być inna wersja [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] w każdym z wielu projektów w tym samym rozwiązaniu.

- Po zmianie wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] który docelowych projektu, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] sprawia, że wszelkie wymagane zmiany do odwołania i plików konfiguracji.

Podczas pracy w projekcie, który jest przeznaczony dla starszej wersji programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio dynamicznie zmienia środowisko projektowe w następujący sposób:

- Filtruje elementy **Dodaj nowy element** okno dialogowe **Dodaj nowe odwołanie** okno dialogowe i **Dodaj odwołanie do usługi** okno dialogowe, aby pominąć decyzje, które nie są dostępne w Docelowa wersja.

- Filtruje niestandardowe formanty w **przybornika** Usuń te, które nie są dostępne w docelowej wersji i Pokaż tylko najnowsze kontrolek dostępnych wiele formantów.

- Filtruje IntelliSense, aby pominąć funkcje językowe, które nie są dostępne w wersji docelowej.

- Filtruje właściwości w **właściwości** okno, aby pominąć te, które nie są dostępne w docelowej wersji.

- Filtruje opcji menu, aby pominąć opcje, które nie są dostępne w wersji docelowej.

- Dla kompilacji używa wersji kompilatora i opcje kompilatora, które są odpowiednie dla docelowej wersji.

> [!NOTE]
> Docelowy Framework nie gwarantuje, że aplikacja jest uruchamiana poprawnie. Konieczne jest przetestowanie aplikacji upewnij się, że jej jest uruchamiana dla docelowej wersji. Nie można target framework w wersji starszej niż .NET Framework 2.0.

## <a name="selecting-a-target-framework-version"></a>Wybieranie framework w wersji docelowej

Podczas tworzenia projektu, wybierz docelową wersję platformy .NET w **nowy projekt** okno dialogowe. Lista dostępnych platform zawiera wersje zainstalowano framework, które mają zastosowanie do typu wybranego szablonu. Dla typów szablonów, które nie wymagają platformy .NET, na przykład szablony .NET Core **Framework** listy rozwijanej jest ukryty.

![W ramach listy rozwijanej w oknie dialogowym Nowy projekt](media/vside-newproject-framework.png)

W istniejącego projektu, można zmienić obiektu docelowego [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji w oknie dialogowym właściwości projektu. Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolving-system-and-user-assembly-references"></a>Rozpoznawanie odwołania do zestawów systemu i użytkownika

Aby skierować je do wersji programu .NET Framework, należy najpierw zainstalować odwołuje się do odpowiedniego zestawu. Możesz pobrać pakiety developer dla różnych wersji programu .NET Framework na [pobiera .NET](https://www.microsoft.com/net/download/windows) strony.

**Dodaj odwołanie** okno dialogowe wyłącza zestawy systemu, które nie odnoszą się do obiektu docelowego [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji, aby nie można ich dodać do projektu przypadkowo. (Zestawy systemu są plików .dll, które znajdują się w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji.) Nie można rozwiązać odwołania, które należą do wersji struktury, która jest nowsza niż wersja docelowa, i nie można dodać formantów, które są zależne od odniesienie. Jeśli chcesz włączyć odniesienie, zresetuj [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] docelowej projektu, który obejmuje odwołania.  Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Aby uzyskać więcej informacji na temat odwołania do zestawów, zobacz [rozwiązywanie zestawów w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enabling-linq"></a>Włączanie LINQ

Jeśli zostanie rozpoczęta dla programu .NET Framework 3.5 lub nowszej, odwołanie do System.Core i importowanie poziom projektu dla System.Linq (w tylko Visual Basic) są dodawane automatycznie. Jeśli chcesz korzystać z funkcji LINQ, należy również włączyć Option Infer (w tylko Visual Basic). Odwołanie i importu są usuwane automatycznie, jeśli zmienisz element docelowy do wcześniejszej wersji .NET Framework. Aby uzyskać więcej informacji, zobacz [pracy za pomocą LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Zobacz także

- [Przeznaczanie dla wielu platform (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
