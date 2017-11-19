---
title: 'Porady: wersja docelowa platformy .NET Framework | Dokumentacja firmy Microsoft'
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
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67145a9aaaf4c01b02bc1cc6db89e375639b4fcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Porady: wersja docelowa platformy .NET Framework
W tym dokumencie opisano, jak ukierunkować tworzony projekt na konkretną wersję .NET Framework i jak zmienić wersję docelową w istniejących projektach Visual Basic, Visual C# lub Visual F#.  
  
> [!IMPORTANT]
>  Aby dowiedzieć się, jak zmienić docelową wersję dla projektów C++, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).  
  
 **W tym temacie**  
  
-   [Przeznaczenie do wersji oprogramowania podczas tworzenia projektu](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Zmiana wersji docelowej](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a>Przeznaczenie do wersji oprogramowania podczas tworzenia projektu  
 Podczas tworzenia projektu, docelowa wersja .NET Framework określa szablony, których można użyć.  
  
> [!NOTE]
>  W wersji Express programu Visual Studio, należy utworzyć projekt najpierw, a następnie zmienić element docelowy jako [Zmienianie wersji docelowej](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) opisano w dalszej części tego tematu.  
  
#### <a name="to-target-a-version-when-you-create-a-project"></a>Aby ukierunkować tworzony projekt na konkretną wersję  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Na liście w górnej części **nowy projekt** oknie dialogowym Wybierz wersję systemu .NET Framework, które mają projektu docelowego.  
  
    > [!NOTE]
    >  Zwykle, tylko jedna wersja .NET Framework jest instalowana razem z Visual Studio. Jeśli chcesz utworzyć projekt dla innej wersji, najpierw się upewnij, że jest ona zainstalowana. Zobacz [Multi-Targeting programu Visual Studio — omówienie](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  Na liście zainstalowanych szablonów, wybierz typ projektu, który chcesz utworzyć, nazwij projekt i wybierz **OK** przycisku.  
  
     Lista szablonów pokazuje tylko projekty, które są obsługiwane przez wybraną przez użytkownika wersję .NET Framework.  
  
##  <a name="bkmk_existing"></a>Zmiana wersji docelowej  
 Docelowa wersja programu .NET Framework w projektach Visual Basic, Visual C# lub Visual F # można zmienić, korzystając z następującej procedury.  
  
#### <a name="to-change-the-targeted-version"></a>Aby zmienić wersję docelową  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, który chcesz zmienić, a następnie wybierz pozycję **właściwości**.  
  
     ![Właściwości Eksploratora rozwiązania programu Visual Studio](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  Aby dowiedzieć się, jak zmienić docelową wersję dla projektów C++, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).  
  
2.  W lewej kolumnie okna właściwości, wybierz **aplikacji** kartę.  
  
     ![Visual Studio aplikacji właściwości aplikacji kartę](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  Po utworzeniu aplikacji platformy uniwersalnej systemu Windows, nie można zmienić docelowej wersji systemu Windows lub programu .NET Framework.  
  
3.  W **platformy docelowej** listy, wybierz wersję, która ma.  
  
4.  W oknie dialogowym weryfikacji wybierz **tak** przycisku.  
  
     Projekt zostaje wyładowany Gdy się ponownie ładuje, jest ukierunkowany na wybraną wersję .NET Framework.  
  
    > [!NOTE]
    >  Jeśli kod zawiera odwołania do innej wersji platformy .NET Framework niż docelowa, podczas kompilacji lub uruchamiania kodu mogą się pojawić komunikaty o błędach. Aby usunąć te błędy, należy zmodyfikować odwołania. Zobacz [Rozwiązywanie problemów z błędami obiektów docelowych w programie .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Wielowersyjności kodu — omówienie](../ide/visual-studio-multi-targeting-overview.md)   
 [.NET framework Wielowersyjności kodu dla projektów sieci Web ASP.NET](http://msdn.microsoft.com/Library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [Rozwiązywanie problemów z błędami obiektów docelowych w programie .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Konfigurowanie projektów](http://msdn.microsoft.com/Library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)