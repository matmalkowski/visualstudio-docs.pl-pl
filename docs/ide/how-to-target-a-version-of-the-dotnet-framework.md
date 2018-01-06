---
title: 'Porady: wersja docelowa platformy .NET Framework | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: f648f07923117b89278ba0e5f44e351b923f7c26
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Porady: wersja docelowa platformy .NET Framework

W tym dokumencie opisano, jak wersja docelowa platformy .NET Framework podczas tworzenia projektu oraz jak zmienić wersję docelową w istniejących Visual Basic, Visual C# lub Visual F # projektu.

> [!IMPORTANT]
> Aby dowiedzieć się, jak zmienić docelową wersję dla projektów C++, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="targeting-a-version-when-you-create-a-project"></a>Ukierunkowywanie tworzonego projektu na konkretną wersję

Podczas tworzenia projektu, docelowa wersja .NET Framework określa szablony, których można użyć.

### <a name="to-target-a-version-when-you-create-a-project"></a>Aby ukierunkować tworzony projekt na konkretną wersję

1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.

2.  Na liście w górnej części **nowy projekt** oknie dialogowym Wybierz wersję systemu .NET Framework, które mają projektu docelowego.

3.  Na liście zainstalowanych szablonów, wybierz typ projektu, który chcesz utworzyć, nazwij projekt i wybierz **OK** przycisku.

    Lista szablonów pokazuje tylko projekty, które są obsługiwane przez wybraną przez użytkownika wersję .NET Framework.

## <a name="changing-the-target-version"></a>Zmiana wersji docelowej

Docelowa wersja programu .NET Framework w projektach Visual Basic, Visual C# lub Visual F # można zmienić, korzystając z następującej procedury.

Aby dowiedzieć się, jak zmienić docelową wersję dla projektów C++, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

### <a name="to-change-the-targeted-version"></a>Aby zmienić wersję docelową

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, który chcesz zmienić, a następnie wybierz pozycję **właściwości**.

    ![Właściwości Eksploratora rozwiązania programu Visual Studio](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")

2. W lewej kolumnie okna właściwości, wybierz **aplikacji** kartę.

    ![Visual Studio aplikacji właściwości aplikacji kartę](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > Po utworzeniu aplikacji platformy uniwersalnej systemu Windows, nie można zmienić docelowej wersji systemu Windows lub programu .NET Framework.

3.  W **platformy docelowej** listy, wybierz wersję, która ma.

4.  W oknie dialogowym weryfikacji wybierz **tak** przycisku.

    Projekt zostaje wyładowany Gdy się ponownie ładuje, jest ukierunkowany na wybraną wersję .NET Framework.

    > [!NOTE]
    > Jeśli kod zawiera odwołania do innej wersji platformy .NET Framework niż docelowa, podczas kompilacji lub uruchamiania kodu mogą się pojawić komunikaty o błędach. Aby usunąć te błędy, należy zmodyfikować odwołania. Zobacz [Rozwiązywanie problemów z błędami obiektów docelowych w programie .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Zobacz także

[Wielowersyjność kodu w programie Visual Studio ― przegląd](../ide/visual-studio-multi-targeting-overview.md)  
[Rozwiązywanie problemów z błędami obiektów docelowych programu .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)  
[Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)  
[Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  
[Porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)