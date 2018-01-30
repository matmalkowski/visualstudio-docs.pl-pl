---
title: "Pomijanie ostrzeżeń kompilatora w programie Visual Studio dla projektów i pakiety NuGet | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3af162101eb20e018be44480c862192c0c59276a
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-suppress-compiler-warnings"></a>Porady: pomijanie ostrzeżeń kompilatora

Dziennik kompilacji można declutter przez filtrowanie jednego lub więcej rodzajów ostrzeżeń kompilatora. Na przykład można przejrzeć tylko niektóre z danych wyjściowych, który jest generowany, gdy poziom szczegółowości dziennika kompilacji jest ustawiony na normalny, szczegółowe lub diagnostyki. Aby uzyskać więcej informacji na temat szczegółowości, zobacz [porady: widoku, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppressing-specific-warnings-for-visual-c-or-f"></a>Pomijanie określonych ostrzeżeń dla języka Visual C# lub języka F # #

Użyj **kompilacji** stronę właściwości i pomijanie określonych ostrzeżeń dla projektów C# i F #.

1. W **Eksploratora rozwiązań**, wybierz projekt, w którym chcesz tłumienie ostrzeżeń.

1. Na pasku menu wybierz **widoku** > **strony właściwości**.

1. Wybierz **kompilacji** strony.

1. W **tłumienie ostrzeżeń** Określ kody błędów, ostrzeżeń, które chcesz pominąć, oddzielając je średnikami.

1. Ponownie skompiluj rozwiązanie.

## <a name="suppressing-specific-warnings-for-visual-c"></a>Pomijanie określonych ostrzeżeń w języku Visual C++

Użyj **właściwości konfiguracji** strony właściwości, aby pominąć określone ostrzeżenia dla projektów C++.

1. W **Eksploratora rozwiązań**, wybierz projekt lub źródła plików, w którym chcesz tłumienie ostrzeżeń.

1. Na pasku menu wybierz **widoku** > **strony właściwości**.

1. Wybierz **właściwości konfiguracji** kategorii, wybierz **C/C++** kategorii, a następnie wybierz pozycję **zaawansowane** strony.

1. Wykonaj jedną z następujących czynności:

    - W **Wyłącz określone ostrzeżenia** Określ kody błędów, ostrzeżeń, które chcesz pominąć, oddzielone średnikami.

    - W **Wyłącz określone ostrzeżenia** wybierz **Edytuj** Aby wyświetlić więcej opcji.

1. Wybierz **OK** przycisk, a następnie ponownie skompiluj rozwiązanie.

## <a name="suppressing-warnings-for-visual-basic"></a>Pomijanie ostrzeżeń dla języka Visual Basic

Ostrzeżenia kompilatora określonych w języku Visual Basic można ukryć, edytując *vbproj* w pliku projektu. Aby tłumienie ostrzeżeń przy *kategorii*, można użyć [kompilacji — strona właściwości](../ide/reference/compile-page-project-designer-visual-basic.md). Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Aby pominąć określone ostrzeżenia dla języka Visual Basic

W tym przykładzie przedstawiono sposób edytowania *vbproj* pomijanie ostrzeżeń kompilatora określonego pliku.

1. W **Eksploratora rozwiązań**, wybierz projekt, w którym chcesz tłumienie ostrzeżeń.

1. Na pasku menu wybierz **projektu** > **Zwolnij projekt**.

1. W **Eksploratora rozwiązań**, otwórz menu skrótu lub kliknij prawym przyciskiem myszy dla projektu, a następnie wybierz **Edytuj** *ProjectName* **vbproj**.

    Plik XML projekt zostanie otwarty w edytorze kodu.

1. Zlokalizuj `<NoWarn>` element konfiguracji kompilacji zostanie jest kompilowanie z użyciem i dodać co najmniej jeden ostrzeżenie numery jako wartość `<NoWarn>` elementu. Jeśli określisz wiele numerów ostrzeżeń, oddziel je przecinkami.

     W poniższym przykładzie przedstawiono `<NoWarn>` elementu *debugowania* przy tworzeniu konfiguracji na x86 platformy z dwóch ostrzeżeń kompilatora pominięte:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
        <PlatformTarget>x86</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <ErrorReport>prompt</ErrorReport>
        <NoWarn>40059,42024</NoWarn>
        <WarningLevel>1</WarningLevel>
      </PropertyGroup>
    ```

   > [!NOTE]
   > Oprogramowanie .NET core projekty nie zawierają grup właściwości konfiguracji kompilacji domyślnie. Aby tłumienie ostrzeżeń w projekcie platformy .NET Core, ręcznie dodać sekcji konfiguracji kompilacji do pliku. Na przykład:
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFramework>netcoreapp2.0</TargetFramework>
   >     <RootNamespace>VBDotNetCore_1</RootNamespace>
   >   </PropertyGroup>
   >   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
   >     <NoWarn>42016,41999,42017</NoWarn>
   >   </PropertyGroup>
   > </Project>
   > ```

1. Zapisać zmiany w *vbproj* pliku.

1. Na pasku menu wybierz **projektu** > **Załaduj ponownie projekt**.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj ponownie rozwiązanie**.

    **Dane wyjściowe** okno nie jest już wyświetlana ostrzeżenia, określone przez użytkownika.

Aby uzyskać więcej informacji, zobacz [/nowarn — opcja kompilatora](/dotnet/visual-basic/reference/command-line-compiler/nowarn) dla kompilatora wiersza polecenia języka Visual Basic.

## <a name="suppressing-warnings-for-nuget-packages"></a>Pomijanie ostrzeżeń dla pakietów NuGet

W niektórych przypadkach warto pomijanie ostrzeżeń kompilatora NuGet dla jednego pakietu NuGet, a nie dla całego projektu. Ostrzeżenie służy cel, więc nie chcesz pominąć go na poziomie projektu. Na przykład jeden z ostrzeżeniami NuGet informuje, że pakiet może nie być w pełni zgodne z projektem. Jeśli Pomiń go na poziomie projektu i później dodać dodatkowe pakietu NuGet, czy nigdy nie wiesz, jeśli został produkujących ostrzeżenie zgodności.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Aby pominąć określone ostrzeżenie jednego pakietu NuGet

1. W **Eksploratora rozwiązań**, wybrać pomijanie ostrzeżeń kompilatora dla pakiet NuGet.

   ![Pakiet NuGet w Eksploratorze rozwiązań](media/nuget-package-with-warning.png)

1. Wybierz z menu kliknij prawym przyciskiem myszy lub kontekstu **właściwości**.

1. W **NoWarn** pole właściwości pakietu, wprowadź numer ostrzeżenia chcesz pominąć ten pakiet. Jeśli chcesz pominąć więcej niż jeden ostrzeżenie, użyj przecinka do oddzielania liczb ostrzeżenie.

   ![Właściwości pakietu NuGet](media/nuget-properties-nowarn.png)

   Ostrzeżenie zniknie z **Eksploratora rozwiązań** i **listy błędów**.

## <a name="see-also"></a>Zobacz także

[Przewodnik: Kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)  
[Instrukcje: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)  
[Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)
