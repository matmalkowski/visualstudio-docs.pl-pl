---
title: Jaki &#39; s nowego w Visual Studio 2015 SDK | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8b1fa4647cd5b145d19e2264381b186394be814
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Jaki &#39; s nowego w Visual Studio 2015 SDK
Visual Studio SDK ma następujące nowe i zaktualizowane funkcje programu Visual Studio 2015, Visual Studio 2015 zaktualizowane i Visual Studio 2017 r.  
  
## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK Update 1  
 Aktualizacja 1 zawiera narzędzia do rozszerzenia działają prawidłowo w przypadku motywy kolorów i Usługa obrazów programu Visual Studio.  
  
 Te tematy podlegają [VSSDK narzędzia](../extensibility/internals/vssdk-utilities.md) sekcji:  
  
-   [Narzędzia tworzenia motywów kolor](../extensibility/internals/color-theming-tools.md) ułatwiają tworzenie i edytowanie kolorów niestandardowych dla programu Visual Studio.  
  
-   [Narzędzia usługi obrazów](../extensibility/internals/image-service-tools.md) let pracować z manifestu pliki obrazów programu Visual Studio.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nowy sposób, aby dodać programu Visual Studio SDK dla programu Visual Studio  
 Począwszy od programu Visual Studio 2015, nie trzeba pobrać osobno programu Visual Studio SDK. Zamiast tego można ją zainstalować jako część procesu normalnej instalacji lub użytkownik może zainstalować ją później. Po otwarciu lub utworzyć rozwiązanie VSIX Visual Studio zostanie wyświetlony monit o Zainstaluj narzędzia rozszerzalności programu Visual Studio. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Nowe sposoby Tworzenie rozszerzeń  
 Począwszy od programu Visual Studio 2015 SDK masz różne sposoby tworzenia rozszerzenia, w zależności od tego, jaki język programowania używany.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# i Visual Basic  
 C# i Visual Basic brak pełnego zakresu szablony elementów projektu, które pozwalają tworzyć VSPackages, polecenia menu okna narzędzi, klasyfikatory edytora, skojarzenia edytora i rozszerzenia marginesu edytora. Można dodać wybranych lub wszystkich z nich do standardowych projektu VSIX. Aby uzyskać więcej informacji, zobacz:  
  
-   [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Tworzenie rozszerzenia z pakiet VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     Pakiet VSPackage Kreator nie tworzy już rozszerzeń w języku C# lub Visual Basic.  
  
### <a name="c"></a>C++  
 Dla języka C++ Kreator pakiet VSPackage obsługuje polecenia menu okna narzędzi i edytory niestandardowych. Wyszukaj go w **nowy projekt** okno dialogowe w **Visual C++ / rozszerzalności**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Zestawy odwołanie do zestawu SDK programu VS za pośrednictwem pakietu NuGet  
 Zwiększona przenośność oraz udostępniania tych projektów rozszerzalności można użyć wersji NuGet zestawów odwołań zestawu VS SDK.  Są one dostępne na [nuget.org](http://www.nuget.org) opublikowanych przez [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) i można je łatwo dodać do projektu lub rozwiązania za pomocą programu Visual Studio **odwołuje się do / Zarządzaj NuGet Pakiety** okna dialogowego. Można dodać poszczególnych odwołań do zestawów określonych rozszerzeń lub dodać zestawu SDK programu VS odwołuje się do zestawów jednocześnie przy użyciu zestawu SDK dla programu [Meta pakietu](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Aby dowiedzieć się więcej na temat narzędzia NuGet, zobacz [dokumentacji NuGet](http://docs.microsoft.com/NuGet) i [interfejsu użytkownika Menedżera pakietów](http://docs.microsoft.com/NuGet/Tools/Package-Manager-UI) tematów.  
  
 Gdy używasz wersji NuGet zestawów odwołań zestawu VS SDK inny użytkownik nie należy zainstalować zestawu SDK dla programu do otwierania i skompilowanie projektu.  Zestawy odwołań NuGet i narzędzia kompilacji zestawu VS SDK automatycznie zostaną zainstalowane na komputerze dla tego projektu.  
  
 Szablony elementu zestawu VS SDK użycie narzędzia NuGet dla ich odwołań i narzędzi kompilacji, aby uzyskać korzyści NuGet domyślnie.  
  
> [!NOTE]
>  Można kontynuować korzystanie z zestawów odwołania zestawu SDK zainstalowany z projektami (znajdujący się w obszarze \<programu Visual Studio lokalizacji instalacji > \ VSSDK\VisualStudioIntegration\Common\Assemblies) i istniejące projekty rozszerzalności nie muszą być uaktualnione w celu obsługi pakietów NuGet.  Projekt **odwołuje się do / Dodaj odwołanie** okna dialogowego w dalszym ciągu używa zestawów odwołań zestawu VS SDK zainstalowany.  
>   
>  Jeśli chcesz zmodyfikować istniejących projektów NuGet, zobacz [porady: VSPackages migracji do programu Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) mającego sekcję na temat aktualizowania rozszerzalności projekty do pakietów NuGet.  
  
## <a name="light-bulbs"></a>Żarówki  
 Jedną z najbardziej ekscytujące nowe sposoby pisania kodu rozszerzenia są udostępniane przez Roslyn projektu. Aby uzyskać więcej informacji, zobacz [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Żarówki to nowa funkcja, która jest dostarczana z VSSDK. Są one ikon używanych w edytorze programu Visual Studio, które Rozwiń, aby wyświetlić zestaw akcji refaktoryzacji kodu lub poprawki na problemy, identyfikowane przez analizatorów wbudowanego kodu. Aby uzyskać więcej informacji, zobacz [wskazówki: wyświetlanie sugestii żarówki](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Wskazówki dotyczące czynności użytkownika zaktualizowane  
 Projektowanie nowych rozszerzeń lub funkcje programu Visual Studio? Sprawdź zaktualizowane i rozwinięte [dotyczące środowiska użytkownika w usłudze Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Można znaleźć [kolor tokenów](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [rozmiary czcionek](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [specyfikacje układu okna dialogowego](../extensibility/ux-guidelines/layout-for-visual-studio.md)i innych wskazówek należy bezproblemową integrację z nowego interfejsu użytkownika programu Visual Studio.