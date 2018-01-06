---
title: "Porady: pomijanie ostrzeżeń kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d97695cae08352ea213ba02008ab99bef7f61c47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-compiler-warnings"></a>Porady: pomijanie ostrzeżeń kompilatora
Declutter z dziennika kompilacji, określając co najmniej jednego rodzaju ostrzeżeń kompilatora, że nie powinien on zawierać. Na przykład można użyć tej techniki, aby przejrzeć niektóre, ale nie wszystkie informacje, które jest generowany automatycznie podczas szczegółowości dziennika kompilacji jest ustawiony na normalny, szczegółowe lub diagnostyki. Aby uzyskać więcej informacji na temat szczegółowości, zobacz [porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Aby pominąć określone ostrzeżenia dla języka Visual C# lub języka F # #
  
1.  W **Eksploratora rozwiązań**, wybierz projekt, w którym chcesz tłumienie ostrzeżeń.  
  
2.  Na pasku menu wybierz **widoku**, **strony właściwości**.  
  
3.  Wybierz **kompilacji** strony.  
  
4.  W **tłumienie ostrzeżeń** polu, określ kody błędów, ostrzeżeń, które chcesz pominąć, oddzielone średnikami i ponownie skompiluj rozwiązanie.  
  
### <a name="to-suppress-specific-warnings-for-visual-c"></a>Aby pominąć określone ostrzeżenia w języku Visual C++  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt lub źródła plików, w którym chcesz tłumienie ostrzeżeń.  
  
2.  Na pasku menu wybierz **widoku**, **strony właściwości**.  
  
3.  Wybierz **właściwości konfiguracji** kategorii, wybierz **C/C++** kategorii, a następnie wybierz pozycję **zaawansowane** strony.  
  
4.  Wykonaj jedną z następujących czynności:  
  
    -   W **Wyłącz określone ostrzeżenia** Określ kody błędów, ostrzeżeń, które chcesz pominąć, oddzielone średnikami.  
  
    -   W **Wyłącz określone ostrzeżenia** wybierz **Edytuj** Aby wyświetlić więcej opcji.  
  
5.  Wybierz **OK** przycisk, a następnie ponownie skompiluj rozwiązanie.  
  
## <a name="suppressing-warnings-for-visual-basic"></a>Pomijanie ostrzeżeń dla języka Visual Basic  
 Ostrzeżenia kompilatora określonych w języku Visual Basic można ukryć, edytując plik vbproj dla projektu. Można również użyć [strona kompilowania, Projektant projektu](../ide/reference/compile-page-project-designer-visual-basic.md) do pomijania ostrzeżeń według kategorii. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Aby pominąć określone ostrzeżenia dla języka Visual Basic  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt, w którym chcesz tłumienie ostrzeżeń.  
  
2.  Na pasku menu wybierz **projektu**, **Zwolnij projekt**.  
  
3.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **Edytuj***ProjectName***vbproj**.  
  
     Plik projektu jest otwarty w edytorze kodu.  
  
4.  Zlokalizuj `<NoWarn></NoWarn>` element w konfiguracji kompilacji, z którym tworzysz.  
  
     W poniższym przykładzie przedstawiono `<NoWarn></NoWarn>` element pogrubione dla konfiguracji kompilacji debugowania na x86 platformy:  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn></NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  Dodaj co najmniej jeden numery ostrzeżeń jako wartość `<NoWarn>` elementu. Jeśli określisz wiele numerów ostrzeżeń, oddziel je przecinkami, jak przedstawiono na poniższym przykładzie.  
  
    ```  
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
  
6.  Zapisz zmiany w pliku vbproj.  
  
7.  Na pasku menu wybierz **projektu**, **Załaduj ponownie projekt**.  
  
8.  Na pasku menu wybierz **kompilacji**, **Kompiluj ponownie rozwiązanie**.  
  
     **Dane wyjściowe** okno nie jest już wyświetlana ostrzeżenia, określone przez użytkownika.  
  
 Aby uzyskać więcej informacji, zobacz [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie aplikacji](../ide/walkthrough-building-an-application.md)   
 [Porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)
