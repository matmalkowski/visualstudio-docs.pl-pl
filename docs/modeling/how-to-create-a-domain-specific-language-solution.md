---
title: 'Porady: tworzenie rozwiązania języka właściwego dla domeny'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: c4851577a62db08e2c759f7140895e15b230ec60
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Porady: tworzenie rozwiązania języka właściwego dla domeny
Języka specyficznego dla domeny (DSL) jest tworzony przy użyciu specjalistycznej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania.

## <a name="prerequisites"></a>Wymagania wstępne
 Przed rozpoczęciem tej procedury, musisz najpierw zainstalować te składniki:

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|
|Visual Studio wizualizacji i modelowania zestawu SDK||


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


## <a name="creating-a-domain-specific-language-solution"></a>Tworzenie rozwiązania języka specyficznego dla domeny

#### <a name="to-create-a-domain-specific-language-solution"></a>Tworzenie rozwiązań języka specyficznego dla domeny

1.  Uruchom Kreatora DSL.

    1.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.

    2.  **Nowy projekt** zostanie wyświetlone okno dialogowe.

    3.  W obszarze **typy projektów**, rozwiń węzeł **inne typy projektów** węzeł, a następnie kliknij przycisk **rozszerzalności**.

    4.  Kliknij przycisk **projektanta języka specyficznego dla domeny**.

    5.  W **nazwa** wpisz nazwę dla rozwiązania. Kliknij przycisk **OK**.

         **Kreatora Designer języka specyficznego dla domeny** pojawi się.

        > [!NOTE]
        >  Najlepiej nazwa powinna być prawidłowy Visual C# identyfikator, ponieważ może być używane do generowania kodu.

     ![Okno dialogowe DSL tworzenie](../modeling/media/create_dsldialog.png "Create_DSLDialog")

2.  Wybierz szablon DSL.

     Na **wybierz opcje języka specyficznego dla domeny** wybierz jeden z szablonów rozwiązania takich jak **minimalnego języka**. Wybierz szablon, który jest podobny do DSL, który chcesz utworzyć.

     Aby uzyskać więcej informacji o szablonach rozwiązania, zobacz [wybieranie szablonów rozwiązania języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

3.  Wpisz rozszerzenie nazwy pliku **rozszerzenie pliku** strony. Powinny być unikatowe w komputerze, a w każdym komputerze, na którym chcesz zainstalować DSL. Powinien zostać wyświetlony komunikat **nie aplikacji lub programu Visual Studio edytory użyć tego rozszerzenia**.

    -   Jeśli używasz rozszerzenia nazwy pliku w poprzedniej DSLs eksperymentalne, które nie zostały całkowicie zainstalowane, możesz je wyczyścić limit przy użyciu **Zresetuj eksperymentalne wystąpienie** narzędzia, które znajdują się w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] menu zestawu SDK.

    -   Jeśli inny [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pełni zainstalowano rozszerzenia, która używa tego rozszerzenia pliku na komputerze, należy rozważyć odinstalowanie go. Na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzenia**.

4.  Sprawdź i w razie potrzeby Dostosuj, pola na pozostałych stronach kreatora. Po zakończeniu ustawienia, kliknij przycisk **Zakończ**. Aby uzyskać więcej informacji o ustawieniach, zobacz [stron kreatora DSL projektanta](#settings).

     Kreator tworzy rozwiązania, które zawiera dwa projekty, które są nazywane **Dsl** i **DslPackage**.

    > [!NOTE]
    >  Jeśli zostanie wyświetlony komunikat z ostrzeżeniem, nie uruchamianie szablonów tekstowych ze źródeł niezaufanych, kliknij **OK**. Można ustawić tej wiadomości nie pojawiają się ponownie.

##  <a name="settings"></a> Strony kreatora projektanta DSL
 Możesz pozostawić kilka pól takie same jak wartości domyślnych. Jednak należy się upewnić, że ustawiona w polu rozszerzenie pliku.

### <a name="solution-settings-page"></a>Strona Ustawienia rozwiązania
 **Szablon, który chcesz na podstawie określonego języka domeny?**
Wybierz szablon, który jest podobny do DSL, który chcesz utworzyć. Różne szablony zapewniają wygodną punktów początkowych. Jeśli wybierzesz szablon rozwiązania, Kreator wyświetli opis. Aby uzyskać więcej informacji o szablonach rozwiązania, zobacz [wybieranie szablonów rozwiązania języka specyficznego dla domeny](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Co chcesz nazwać języka specyficznego dla domeny?**
Wartość domyślna to nazwa rozwiązania. Kod jest generowany na podstawie tej wartości. Musi to być prawidłowy, jak nazwa klasy C#.

### <a name="file-extension-page"></a>Strona rozszerzenie pliku
 **Jakie rozszerzenia powinien modelu pliki używają?**
Wpisz nowe rozszerzenie pliku.

 Sprawdź, czy to rozszerzenie pliku nie już został zarejestrowany do użycia w tym komputerze w następujący sposób:

 Sprawdź w obszarze **innych narzędzi i aplikacji w zarejestrowany do obsługi tego rozszerzenia**. Jeśli zostanie wyświetlony komunikat **nie aplikacji lub programu Visual Studio edytory użyć tego rozszerzenia**, a następnie można użyć tego rozszerzenia pliku.

 Jeśli zobaczysz listę narzędzi lub pakietów, należy wykonać jedną z następujących czynności:

-   Wpisz rozszerzenie inny plik.

     \- lub -

-   Resetuj [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eksperymentalne wystąpienie. Będą to wszystkie DSLs, które zostały wcześniej utworzone wyrejestrować. Na **Start** menu, kliknij przycisk **wszystkie programy**, **zestawu SDK programu Microsoft Visual Studio 2010**, **narzędzia**, a następnie **resetowania Microsoft Visual Studio 2010 eksperymentalne wystąpienie**. Można ponownie utworzyć innych DSLs, których chcesz użyć ponownie.

     \- lub -

-   Jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pełni zainstalowano rozszerzenia, która używa tego rozszerzenia pliku na komputerze, należy go odinstalować. Na **narzędzia** menu, kliknij przycisk **Menedżera rozszerzenia**.

### <a name="product-settings-page"></a>Strona Ustawienia produktu
 **Co to jest nazwa produktu, należącego do nowego języka specyficznego dla domeny?**
Wartość domyślna to nazwa DSL.

 Ta wartość jest używana w Eksploratorze Windows (lub Eksploratora plików) do opisywania plików z rozszerzeniem pliku.

 **Co to jest nazwa produktu należy do firmy?**
Nazwa firmy.

 Ta wartość jest włączona do właściwości AssemblyInfo pakietu DSL.

 **Co to jest głównej przestrzeni nazw dla projektów w tym rozwiązaniu?**
Wartością domyślną nazwę składa się z Twojej firmy i nazwy produktu.

### <a name="signing-page"></a>Strona podpisywania
 **Utwórz plik klucza o silnej nazwie** opcją domyślną jest utworzenie nowego klucza do podpisywania używanego zestawu DSL.

 **Użyj istniejącego klucza silnej nazwy** Użyj tej opcji, jeśli chcesz zintegrować z DSL z innego zestawu.

 Aby uzyskać więcej informacji o silnych nazwach, zobacz [tworzenie i zestawy Using Strong-Named](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
