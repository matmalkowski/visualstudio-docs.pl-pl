---
title: Konfigurowanie testów jednostkowych pod kątem starszej wersji programu .NET Framework w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 2c0a34e3a046b840024e7dbfb4b7761fcaec5cfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Porady: konfigurowanie testów jednostkowych pod kątem starszej wersji oprogramowania .NET Framework

Po utworzeniu projektu testu w programie Microsoft Visual Studio najnowszej wersji programu .NET Framework jest domyślnie jako element docelowy. Ponadto jeśli projekty testowe uaktualnienie poprzedniej wersji programu Visual Studio, ich uaktualnienia do najnowszej wersji programu .NET Framework. Edytując właściwości projektu, można jawnie ponownie docelowych projektu do wcześniejszych wersji programu .NET Framework.

Jednostki można tworzyć projekty testowe, które odnoszą się do określonych wersji systemu .NET Framework. Docelowa wersja musi być w wersji 3.5 lub nowszej, a nie może być wersji klienta. Program Visual Studio pozwala podstawowe obsługę testy jednostek, które odnoszą się do określonych wersji:

- Można tworzyć projektów testów jednostkowych i adresować je do określonej wersji programu .NET Framework.

- Można uruchomić testów jednostkowych kierowanych określonej wersji programu .NET Framework w programie Visual Studio na komputerze lokalnym.

- Testy jednostkowe można uruchomić kierowanych określonej wersji programu .NET Framework za pomocą MSTest.exe z wiersza polecenia.

- Testy jednostkowe można uruchamiać na agenta kompilacji podczas kompilacji.

**Testowanie aplikacji SharePoint**

Funkcje wymienione powyżej również umożliwia pisanie testów jednostkowych i integracji aplikacji programu SharePoint przy użyciu programu Visual Studio. Aby uzyskać więcej informacji o sposobie tworzenia aplikacji programu SharePoint przy użyciu programu Visual Studio, zobacz [tworzenie rozwiązań programu SharePoint](/office-dev/office-dev/create-sharepoint-solutions), [kompilowanie i debugowanie rozwiązań SharePoint](/office-dev/office-dev/building-and-debugging-sharepoint-solutions) i [weryfikacji i debugowanie kodu aplikacji programu SharePoint](/office-dev/office-dev/verifying-and-debugging-sharepoint-code).

**Ograniczenia**

Gdy ponownie docelowego Twoje projekty testowe do wcześniejszych wersji programu .NET Framework, obowiązują następujące ograniczenia:

- W .NET Framework 3.5 przeznaczanie dla wielu platform obsługuje projekty testowe, zawierające testy jednostkowe tylko. .NET Framework 3.5 nie obsługuje żadnego innego typu testu, takie jak kodowanego testu interfejsu użytkownika lub obciążenia. Ponownie celem jest zablokowana dla testu typu innego niż testy jednostkowe.

- Wykonywanie testów, które są przeznaczone dla wcześniejszych wersji programu .NET Framework jest obsługiwany tylko w domyślnego adaptera hosta. Nie jest obsługiwane na karcie hosta platformy ASP.NET. Aplikacji programu ASP.NET, które nie zostały uruchomione w kontekście ASP.NET Development Server muszą być zgodne z bieżącą wersją programu .NET Framework.

- Obsługa danych kolekcji jest wyłączone, po uruchomieniu testów, które obsługują przeznaczanie dla wielu platform .NET Framework 3.5. Można uruchomić pokrycia kodu za pomocą narzędzia wiersza polecenia programu Visual Studio.

- Testy jednostkowe, które używają programu .NET Framework 3.5 nie można uruchomić na komputerze zdalnym.

- Nie może wskazać testów jednostkowych do starszych wersji klienta platformy.

## <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-basic-unit-test-projects"></a>Ponownego określenia wartości docelowej do określonej wersji programu .NET Framework dla projektów testów jednostkowych programu Visual Basic

1.  Tworzenie nowego projektu testu jednostkowego języka Visual Basic. Na **pliku** menu, wybierz **nowy** , a następnie wybierz **projektu**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

2.  W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual Basic**. Wybierz **testu** , a następnie wybierz **projekt testowy** szablonu.

3.  W **nazwa** polu tekstowym, wpisz nazwę dla języka Visual Basic projekt testowy, a następnie wybierz pozycję **OK**.

4.  W Eksploratorze rozwiązań wybierz **właściwości** w menu skrótów nowy projekt testowy Visual Basic.

     Są wyświetlane właściwości projekt testowy Visual Basic.

5.  Na **skompilować** , wybierz pozycję **zaawansowane opcje kompilacji** jak pokazano na poniższej ilustracji.

     ![Zaawansowane opcje kompilacji](../test/media/howtoconfigureunittest35frameworka.png "HowToConfigureUnitTest35FrameworkA")

6.  Użyj **platformy docelowej (wszystkie konfiguracje)** listy rozwijanej, aby zmienić platformę docelową, aby **.NET Framework 3.5** lub nowszej wersji, jak pokazano na poniższej ilustracji, objaśnienia B. Nie należy określać wersji klienta.

     ![Docelowy framework upuszczania&#45;pozycji listy](../test/media/howtoconfigureunitest35frameworkstepb.png "HowToConfigureUniTest35FrameworkStepB")

## <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-c-unit-test-projects"></a>Ponownego określenia wartości docelowej do określonej wersji programu .NET Framework dla programu Visual C# projektów testów jednostkowych

1.  Tworzenie nowego projektu testu jednostkowego języka Visual C#. Na **pliku** menu, wybierz **nowy** , a następnie wybierz **projektu**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

2.  W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C#**. Wybierz **testu** , a następnie wybierz **projekt testowy** szablonu.

3.  W **nazwa** polu tekstowym, wpisz nazwę dla programu Visual C# projekt testowy, a następnie wybierz pozycję **OK**.

4.  W Eksploratorze rozwiązań wybierz **właściwości** z menu skrótów nowego projektu testu Visual C#.

     Są wyświetlane właściwości projekt testowy Visual C#.

5.  Na **aplikacji** , wybierz pozycję **platformy docelowej**. Z listy rozwijanej wybierz **.NET Framework 3.5** lub nowszej wersji, jak pokazano na poniższej ilustracji. Nie należy określać wersji klienta.

     ![Docelowy framework upuszczania&#45;pozycji listy](../test/media/howtoconfigureunittest35frameworkcsharp.png "HowToConfigureUnitTest35FrameworkCSharp")

## <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-ccli-unit-test-projects"></a>Ponownego określenia wartości docelowej do określonej wersji programu .NET Framework dla języka C + +/ projektów testów jednostkowych interfejsu wiersza polecenia

1.  Tworzenie nowego projektu testu jednostkowego języka C++. Na **pliku** menu, wybierz opcję **nowy** , a następnie kliknij przycisk **projektu**.

     **Nowy projekt** zostanie wyświetlone okno dialogowe.

    > [!WARNING]
    > Aby utworzyć C + +/ testów jednostkowych interfejsu wiersza polecenia dla wcześniejszych wersji programu .NET framework dla programu Visual C++, należy użyć odpowiedniej wersji programu Visual Studio. Na przykład docelową programu .NET Framework 3.5, należy zainstalować program Visual Studio 2008 i dodatku Service Pack 1 dla programu Visual Studio 2008.

2.  W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C ++**. Wybierz **testu** , a następnie wybierz **projekt testowy** szablonu.

3.  W **nazwa** polu tekstowym, wpisz nazwę dla programu Visual C++ projekt testowy, a następnie kliknij przycisk **OK**.

4.  W Eksploratorze rozwiązań wybierz **Zwolnij projekt** z projekt testowy Visual C++.

5.  W Eksploratorze rozwiązań wybierz zwolniony projekt testowy Visual C++, a następnie wybierz **Edytuj \<Nazwa projektu > .vcxproj**.

     Plik .vcxproj zostanie otwarty w edytorze.

6.  Ustaw `TargetFrameworkVersion` w wersji 3.5 lub nowszej wersji w `PropertyGroup` etykietą `"Globals"`. Wersja klienta nie należy określać:

    ```xml
    <PropertyGroup Label="Globals">
        <TargetName>DefaultTest</TargetName>
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>
        <Keyword>ManagedCProj</Keyword>
        <RootNamespace>CPP_Test</RootNamespace>
      </PropertyGroup>
    ```

7.  Zapisz i zamknij plik .vcxproj.

8.  W Eksploratorze rozwiązań wybierz Zaznacz **Załaduj ponownie projekt** w menu skrótów projekt testowy Visual C++.

## <a name="see-also"></a>Zobacz także

- [Tworzenie rozwiązań SharePoint](/office-dev/office-dev/create-sharepoint-solutions)
- [Kompilowanie i debugowanie rozwiązań SharePoint](/office-dev/office-dev/building-and-debugging-sharepoint-solutions)
- [Zaawansowane ustawienia kompilatora (Visual Basic), okno dialogowe](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
