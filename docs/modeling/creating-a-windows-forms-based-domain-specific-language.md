---
title: Tworzenie języka specyficznego dla domeny opartego na formularzach systemu Windows
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8f4cfe9549880646fe9ba0a487045b005366c075
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749479"
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Tworzenie języka specyficznego dla domeny opartego na formularzach systemu Windows
Formularze systemu Windows można użyć do wyświetlenia stanu modelu języka specyficznego dla domeny (DSL), zamiast DSL diagram. Ten temat przeprowadzi Cię przez powiązanie formularza systemu Windows z DSL, używając [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wizualizacji i modelowania zestawu SDK.

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png) wystąpienia A DSL, wyświetlanie interfejsu użytkownika formularza systemu Windows i Eksplorator modelu.

## <a name="creating-a-windows-forms-dsl"></a>Tworzenie formularzy systemu Windows DSL
 **Minimalnego projektanta formularza systemu Windows** DSL szablon tworzy minimalnego DSL, który można dostosować do swoich własnych wymagań.

#### <a name="to-create-a-minimal-winforms-dsl"></a>Aby utworzyć minimalnego DSL WinForms

1.  Utwórz DSL z **minimalnego projektanta formularza systemu Windows** szablonu.

     W tym przewodniku założono są następujące nazwy:

    |||
    |-|-|
    |Nazwa rozwiązania i DSL|FarmApp|
    |Przestrzeń nazw|Company.FarmApp|

2.  Poeksperymentuj z przykładem początkowej, który zawiera szablon:

    1.  Przekształć wszystkie szablony.

    2.  Skompiluj i uruchom próbkę (**CTRL + F5**).

    3.  Eksperymentalne wystąpienie programu Visual Studio, otwórz `Sample` plik debugowania projektu.

         Należy zauważyć, że jest wyświetlany w formancie formularzy systemu Windows.

         Można również sprawdzić elementy wyświetlane w Eksploratorze modelu.

         Dodaj niektóre elementy w formularzu lub Eksploratorze i zwróć uwagę, że pojawią się one w innych wyświetlania.

 W wystąpieniu głównego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], zwróć uwagę następujące kwestie dotyczące rozwiązania DSL:

-   `DslDefinition.dsl` nie zawiera żadnych elementów diagramu. Jest to spowodowane diagramy DSL nie będzie używać do wyświetlania wystąpienia modeli tego DSL. Zamiast tego formularza systemu Windows będzie powiązać modelu, a elementy na formularzu będzie wyświetlana modelu.

-   Oprócz `Dsl` i `DslPackage` projektów, rozwiązanie zawiera projekt trzeci o nazwie `UI.` **interfejsu użytkownika** projektu zawiera definicję formantu formularzy systemu Windows. `DslPackage` zależy od `UI`, i `UI` zależy od `Dsl`.

-   W `DslPackage` projektu, `UI\DocView.cs` zawiera kod, który wyświetla kontrolki formularza systemu Windows, który jest zdefiniowany w `UI` projektu.

-   `UI` Projekt zawiera przykładowe pracy powiązany DSL kontrolka formularza. Jednak nie będzie ona działać po definicji DSL zostały zmienione. `UI` Projekt zawiera:

    -   Klasa formularzy systemu Windows o nazwie `ModelViewControl`.

    -   Plik o nazwie `DataBinding.cs` zawierający dodatkowe częściową definicją `ModelViewControl`. Aby wyświetlić jego zawartość w **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku i wybierz polecenie **kod widoku**.

### <a name="about-the-ui-project"></a>O projekcie interfejsu użytkownika
 Podczas aktualizacji pliku definicji DSL do zdefiniowania własnych DSL, trzeba będzie zaktualizować formantu w `UI` projektu do wyświetlania Twojego DSL. W odróżnieniu od `Dsl` i `DslPackage` projektów próbki `UI` projektu nie jest generowana z `DslDefinitionl.dsl`. Możesz dodać .TT — pliki do generowania kodu, jeśli chcesz, mimo że nie pasuje w tym przewodniku.

## <a name="updating-the-dsl-definition"></a>Aktualizowanie definicji DSL
 Następujące definicji DSL jest używana w tym przewodniku.

 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png)

#### <a name="to-update-the-dsl-definition"></a>Aby zaktualizować definicję DSL

1.  Otwórz DslDefinition.dsl w Projektancie DSL.

2.  Usuń **ExampleElement**

3.  Zmień nazwę **ExampleModel** klasy domeny `Farm`.

     Nadaj właściwości dodatkowe domeny o nazwie `Size` typu **Int32**, i `IsOrganic` typu **logiczna**.

    > [!NOTE]
    >  Jeśli usunąć klasy głównym domeny, a następnie utwórz nowy katalog główny, trzeba będzie zresetować właściwości klasy głównym edytora. W **DSL Explorer**, wybierz pozycję **edytor**. Następnie w oknie właściwości ustaw **klasy głównym** do `Farm`.

4.  Użyj **klasy o nazwie domeny** narzędzia do tworzenia następujące klasy domeny:

    -   `Field` — Podać to właściwość dodatkowe domeny o nazwie `Size`.

    -   `Animal` — W oknie właściwości ustaw **modyfikator dziedziczenia** do **abstrakcyjny**.

5.  Użyj **klasy domeny** narzędzia do tworzenia następujące klasy:

    -   `Sheep`

    -   `Goat`

6.  Użyj **dziedziczenia** narzędzie do tworzenia `Goat` i `Sheep` dziedziczyć `Animal`.

7.  Użyj **Embedding** narzędzia do osadzenia `Field` i `Animal` w obszarze `Farm`.

8.  Możesz chcieć porządek na diagramie. Aby zmniejszyć liczbę zduplikowanych elementów, użyj **Przełącz poddrzewo tutaj** polecenia menu skrótów elementów typu liść.

9. **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań.

10. Tworzenie **Dsl** projektu.

    > [!NOTE]
    >  Na tym etapie innych projektów nie zostanie utworzona bez błędów. Jednak chcemy skompilować projekt Dsl, dzięki czemu jego zestaw jest dostępny dla Kreatora źródła danych.

## <a name="updating-the-ui-project"></a>Aktualizowanie projektu interfejsu użytkownika
 Teraz można utworzyć nowy formant użytkownika spowoduje wyświetlenie informacji, która jest przechowywana w modelu DSL. Najprostszym sposobem połączenia formantu użytkownika modelu jest za pośrednictwem powiązania danych. Powiązanie typu karty o nazwie danych **ModelingBindingSource** zaprojektowane specjalnie do nawiązania połączenia z systemem innym niż VMSDK interfejsów DSLs.

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>Aby zdefiniować modelu DSL jako źródła danych

1.  Na **danych** menu, wybierz **Pokaż źródeł danych**.

     **Źródeł danych** zostanie otwarte okno.

     Wybierz **Dodaj nowe źródło danych**. **Kreator konfiguracji źródła danych** otwiera.

2.  Wybierz **obiektu**, **dalej**.

     Rozwiń węzeł **Dsl**, **Company.FarmApp**i wybierz **farmy**, która jest klasy głównym modelu. Wybierz **Zakończ**.

     W Eksploratorze rozwiązań **interfejsu użytkownika** projektu zawiera teraz **Properties\DataSources\Farm.datasource**

     Właściwości i relacje klasy modelu są wyświetlane w oknie źródeł danych.

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png)

#### <a name="to-connect-your-model-to-a-form"></a>Aby połączyć modelu do formularza

1.  W **interfejsu użytkownika** projektu, Usuń wszystkie istniejące pliki CS.

2.  Dodaj nową **kontrolki użytkownika** plik o nazwie `FarmControl` do **interfejsu użytkownika** projektu.

3.  W **źródeł danych** okna, menu rozwijanego na **farmy**, wybierz **szczegóły**.

     Pozostaw ustawienia domyślne dla innych właściwości.

4.  Otwórz FarmControl.cs w widoku Projekt.

     Przeciągnij **farmy** z okna źródeł danych na FarmControl.

     Zestaw kontrolek pojawi się po jednej dla każdej właściwości. Właściwości relacji nie generują kontrolki.

5.  Usuń **farmBindingNavigator**. To jest automatycznie generowany w `FarmControl` projektanta, ale nie jest przydatne w przypadku tej aplikacji.

6.  Korzystanie z przybornika, Utwórz dwa wystąpienia **DataGridView**, nazwij je `AnimalGridView` i `FieldGridView`.

    > [!NOTE]
    >  Alternatywne krok polega na przeciągnięciu elementów zwierząt i pola z okna źródeł danych w formancie. Ta akcja tworzy automatycznie siatki danych i powiązania między widokiem siatki i źródła danych. Jednak tego powiązania nie działa poprawnie dla DSLs. Dlatego zaleca się tworzenie siatek danych i powiązania ręcznie.

7.  Jeśli nie zawiera przybornika **ModelingBindingSource** narzędzia, dodaj go. W menu skrótów **danych** , wybierz pozycję **wybierz elementy**. W **wybierz elementy przybornika** okno dialogowe, wybierz opcję **ModelingBindingSource** z **.NET Framework kartę**.

8.  Korzystanie z przybornika, Utwórz dwa wystąpienia **ModelingBindingSource**, nazwij je `AnimalBinding` i `FieldBinding`.

9. Ustaw **źródła danych** właściwości każdego **ModelingBindingSource** do **farmBindingSource**.

     Ustaw **DataMember** właściwości **zwierząt** lub **pola**.

10. Ustaw **źródła danych** właściwości `AnimalGridView` do `AnimalBinding`i `FieldGridView` do `FieldBinding`.

11. Dostosuj układ formantu użytkownika smak farmy.

 **ModelingBindingSource** jest karta wykonuje kilka funkcji, które są specyficzne dla DSLs:

-   W transakcji magazynu VMSDK jest zawijany aktualizacji.

     Na przykład gdy użytkownik usuwa wiersz z widoku siatki danych, prawidłowe powiązanie spowoduje wyjątek transakcji.

-   Zapewnia, że po wybraniu wiersza okna właściwości wyświetla właściwości odpowiadający mu element modelu, zamiast wiersza siatki danych.

 ![DslWpf4](../modeling/media/dslwpf4.png) schematu łącza między źródłami danych i widoków.

#### <a name="to-complete-the-bindings-to-the-dsl"></a>Aby ukończyć powiązania z DSL

1.  Dodaj następujący kod w osobnym pliku kodu w **interfejsu użytkownika** projektu:

    ```csharp
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace Company.FarmApp
    {
      partial class FarmControl
      {
        public IContainer Components { get { return components; } }

        /// <summary>Binds the WinForms data source to the DSL model.
        /// </summary>
        /// <param name="nodelRoot">The root element of the model.</param>
        public void DataBind(ModelElement modelRoot)
        {
          WinFormsDataBindingHelper.PreInitializeDataSources(this);
          this.farmBindingSource.DataSource = modelRoot;
          WinFormsDataBindingHelper.InitializeDataSources(this);
        }
      }
    }
    ```

2.  W **DslPackage** projekt, Edytuj **DslPackage\DocView.tt** do aktualizacji definicji następujących zmiennych:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="testing-the-dsl"></a>Testowanie DSL
 Rozwiązanie DSL teraz skompilować i uruchomić, mimo że można dodać dodatkowe ulepszenia później.

#### <a name="to-test-the-dsl"></a>Aby przetestować DSL

1.  Tworzenie i uruchamianie rozwiązania.

2.  Eksperymentalne wystąpienie programu Visual Studio, otwórz **próbki** pliku.

3.  W **FarmApp Explorer**, otwórz menu skrótów na **farmy** węzła głównego, a następnie wybierz pozycję **Dodaj nowe kóz**.

     `Goat1` zostanie wyświetlony w **zwierząt** widoku.

    > [!WARNING]
    >  Należy użyć menu skrótów na **farmy** węzła, nie **zwierząt** węzła.

4.  Wybierz **farmy** węzła głównego i wyświetlić jego właściwości.

     W widoku formularza, zmień **nazwa** lub **rozmiar** farmy.

     Po wyjściu z każdego pola w formularzu odpowiednie zmiany właściwości w oknie właściwości.

## <a name="enhancing-the-dsl"></a>Udoskonalanie DSL

#### <a name="to-make-the-properties-update-immediately"></a>Aby natychmiast zaktualizować właściwości

1.  W widoku Projekt FarmControl.cs wybierz pole proste, takie jak nazwa, rozmiaru lub IsOrganic.

2.  W oknie właściwości rozwiń **powiązania danych** , a następnie otwórz **(zaawansowane)**.

     W **formatowanie i zaawansowane powiązanie** okna dialogowego, w obszarze **trybu aktualizacji źródła danych**, wybierz **OnPropertyChanged**.

3.  Tworzenie i uruchamianie rozwiązania.

     Sprawdź, czy po zmianie zawartości pola odpowiadających im właściwości natychmiast zmiany modelu farmy.

#### <a name="to-provide-add-buttons"></a>Aby zapewnić dodawanie przycisków

1.  W widoku Projekt FarmControl.cs Użyj przybornika, aby utworzyć przycisk w formularzu.

     Edytuj nazwę i tekst przycisku, na przykład, aby `New Sheep`.

2.  Otwórz kodzie przycisku (np. przez dwukrotne kliknięcie).

     Edytuj w następujący sposób:

    ```csharp
    private void NewSheepButton_Click(object sender, EventArgs e)
    {
      using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
      {
        elementOperations.MergeElementGroup(farm,
          new ElementGroup(new Sheep(farm.Partition)));
        t.Commit();
      }
    }

    // The following code is shared with other add buttons:
    private ElementOperations operationsCache = null;
    private ElementOperations elementOperations
    {
      get
      {
        if (operationsCache == null)
        {
          operationsCache = new ElementOperations(farm.Store, farm.Partition);
        }
        return operationsCache;
      }
    }
    private Farm farm
    {
      get { return this.farmBindingSource.DataSource as Farm; }
    }

    ```

     Należy również Wstaw następujące dyrektywy:

    ```csharp

    using Microsoft.VisualStudio.Modeling;

    ```

3.  Dodawanie przycisków podobne kóz i pól.

4.  Tworzenie i uruchamianie rozwiązania.

5.  Sprawdź, czy przycisk Nowy dodaje element. Nowy element powinna pojawić się w Eksploratorze FarmApp i w widoku siatki odpowiednie dane.

     Można edytować nazwy elementu w widoku siatki danych. Można również usunąć z tego miejsca.

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Kod, aby dodać element — informacje
 Nowy element przycisków poniższy kod alternatywnych jest nieco prostsze.

```csharp
private void NewSheepButton_Click(object sender, EventArgs e)
{
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
  {
    farm.Animals.Add(new Sheep(farm.Partition)); ;
    t.Commit();
  }
}

```

 Jednak ten kod nie ustawia domyślną nazwę nowego elementu. Nie działa on żadnych niestandardowych scalania, może być zdefiniowany w **dyrektywy scalania Element** z DSL, i nie powoduje uruchomienia kodu niestandardowego scalania, który może być zdefiniowany.

 Dlatego zaleca się używanie <xref:Microsoft.VisualStudio.Modeling.ElementOperations> do tworzenia nowych elementów. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Element tworzenia i przepływu](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)