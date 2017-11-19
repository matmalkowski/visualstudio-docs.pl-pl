---
title: "Visual Studio Wielowersyjności kodu — omówienie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ad2917a1cf0a620f2e228828a152d91ec8948734
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-multi-targeting-overview"></a>Wielowersyjność kodu Visual Studio ― Omówienie
W tej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], można określić wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wymagany dla aplikacji. W związku z tym jeśli chcesz używać tej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aby kontynuować tworzenie projektu, który został uruchomiony w starszej wersji, nie trzeba zmienić cel struktury. Rozwiązanie zawiera projekty może także utworzyć różne wersje tego docelowej platformy. Docelowy Framework pozwala zagwarantować, że aplikacja używa tylko funkcje, które są dostępne w określonej wersji platformy.  
  
> [!TIP]
>  Możesz też określić aplikacje dla różnych platform. Aby uzyskać więcej informacji, zobacz [przeznaczanie dla wielu platform](../msbuild/msbuild-multitargeting-overview.md)  
  
## <a name="framework-targeting-features"></a>Funkcje określania wartości docelowej Framework  
 Docelowy Framework obejmuje następujące funkcje:  
  
-   Po otwarciu projektu, który jest przeznaczony dla starszej wersji programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] można automatycznie uaktualnić go lub pozostaw element docelowy jest.  
  
-   Podczas tworzenia projektu można określić wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , który ma być docelowa.  
  
-   Można zmienić wersję [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] czy istniejącego projektu elementów docelowych.  
  
-   Celem może być inna wersja [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] w każdym z wielu projektów w tym samym rozwiązaniu.  
  
-   Po zmianie wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] który docelowych projektu, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] sprawia, że wszelkie wymagane zmiany do odwołania i plików konfiguracji.  
  
 Podczas pracy w projekcie, który jest przeznaczony dla starszej wersji programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio dynamicznie zmienia środowisko projektowe w następujący sposób:  
  
-   Filtruje elementy **nowy projekt** okno dialogowe **Dodaj nowy element** okno dialogowe **Dodaj nowe odwołanie** okno dialogowe i **Dodaj odwołanie do usługi** okno dialogowe, aby pominąć decyzje, które nie są dostępne w docelowej wersji.  
  
-   Filtruje niestandardowe formanty w **przybornika** Usuń te, które nie są dostępne w docelowej wersji i Pokaż tylko najnowsze kontrolek dostępnych wiele formantów.  
  
-   Filtruje IntelliSense, aby pominąć funkcje językowe, które nie są dostępne w wersji docelowej.  
  
-   Filtruje właściwości w **właściwości** okno, aby pominąć te, które nie są dostępne w docelowej wersji.  
  
-   Filtruje opcji menu, aby pominąć opcje, które nie są dostępne w wersji docelowej.  
  
-   Dla kompilacji używa wersji kompilatora i opcje kompilatora, które są odpowiednie dla docelowej wersji.  
  
> [!NOTE]
>  Docelowy Framework nie gwarantuje, że aplikacja jest uruchamiana poprawnie. Konieczne jest przetestowanie aplikacji upewnij się, że jej jest uruchamiana dla docelowej wersji. Nie można target framework w wersji starszej niż .NET Framework 2.0.  
  
## <a name="selecting-a-target-framework-version"></a>Wybieranie Framework w wersji docelowej  
 Podczas tworzenia projektu, wybierz element docelowy [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji w **nowy projekt** okno dialogowe. Lista szablonów projektów dostępne są filtrowane na podstawie wybranego. W istniejącego projektu, można zmienić obiektu docelowego [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji w oknie dialogowym właściwości projektu. Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
> [!NOTE]
>  W wersji Express programu Visual Studio, nie można ustawić platformę docelową **nowy projekt** okno dialogowe.  
  
## <a name="resolving-system-and-user-assembly-references"></a>Rozpoznawanie systemu i odwołania do zestawów użytkownika  
 Aby skierować je do wersji programu .NET Framework, należy najpierw zainstalować odwołuje się do odpowiedniego zestawu. Odwołania do zestawów dla wersji systemu .NET Framework 2.0, 3.0 i 3.5 są uwzględnione w .NET Framework 3.5 SP1, który można pobrać z [Microsoft Download Center, programu Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602) witryny sieci Web. Odwołania do zestawów profil klienta programu .NET Framework 3.5, .NET Framework 4, .NET Framework 4 Client Profile i Silverlight są także dostępne w [programu Visual Studio pobiera](http://go.microsoft.com/fwlink/?LinkId=179687) witryny sieci Web.  
  
> [!NOTE]
>  Profil klienta .NET Framework jest podzbiorem programu .NET Framework, która zapewnia ograniczony zestaw funkcji i bibliotek. Aby uzyskać więcej informacji o profilach klienta, zobacz [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
 **Dodaj odwołanie** okno dialogowe wyłącza zestawy systemu, które nie odnoszą się do obiektu docelowego [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji, aby nie można ich dodać do projektu przypadkowo. (Zestawy systemu są plików .dll, które znajdują się w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji.) Nie można rozwiązać odwołania, które należą do wersji struktury, która jest nowsza niż wersja docelowa, i nie można dodać formantów, które są zależne od odniesienie. Jeśli chcesz włączyć odniesienie, zresetuj [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] docelowej projektu, który obejmuje odwołania.  Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
 Aby uzyskać więcej informacji na temat odwołania do zestawów, zobacz [rozwiązywanie zestawów w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md).  
  
## <a name="enabling-linq"></a>Włączanie LINQ  
 Jeśli zostanie rozpoczęta dla programu .NET Framework 3.5 lub nowszej, odwołanie do System.Core i importowanie poziom projektu dla System.Linq (w tylko Visual Basic) są dodawane automatycznie. Jeśli chcesz korzystać z funkcji LINQ, należy również włączyć Option Infer (w tylko Visual Basic). Odwołanie i importu są usuwane automatycznie, jeśli zmienisz element docelowy do wcześniejszej wersji .NET Framework. Aby uzyskać więcej informacji, zobacz [pracy za pomocą LINQ](/dotnet/csharp/tutorials/working-with-linq).  
  
## <a name="see-also"></a>Zobacz też  
 [Przeznaczanie dla wielu platform](../msbuild/msbuild-multitargeting-overview.md)   
 [Wymagania dotyczące systemu i zgodności platformy](http://www.microsoft.com/visualstudio/eng/products/compatibility)