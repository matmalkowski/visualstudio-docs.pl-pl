---
title: Dostosowywanie okna właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6ccd6e64b33bd83a7a67b0d04270d8a6802311c6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-the-properties-window"></a>Dostosowywanie okna właściwości
W języku specyficznego dla domeny (DSL) można dostosować wygląd i zachowanie okna właściwości w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. W definicję DSL można zdefiniować właściwości domeny w każdej klasie domeny. Domyślnie po wybraniu wystąpienia klasy w diagramie lub w Eksploratorze modelu, dla każdej właściwości domeny znajduje się w oknie właściwości. Dzięki temu można wyświetlić i edytować wartości właściwości domeny, nawet jeśli nie ma ich mapowane do pól kształt na diagramie.  
  
## <a name="names-descriptions-and-categories"></a>Nazwy, opisy i kategorie  
 **Nazwy i nazwy wyświetlanej**. W definicji właściwości domeny wyświetlana nazwa właściwości jest nazwa wyświetlana w czasie wykonywania w oknie właściwości. Z kolei nazwa jest używana podczas pisania kodu programu, aby zaktualizować właściwości. Nazwa musi być poprawną nazwę alfanumeryczne CLR, ale nazwa wyświetlana może zawierać spacji.  
  
 Jeśli nazwa właściwości w definicji DSL, jego nazwa wyświetlana automatycznie ma ustawioną kopię nazwy. Zapis nazwę cased Pascal, takie jak "FuelGauge", nazwa wyświetlana automatycznie zawiera spację: "Paliwa miernika". Jednak można ustawić nazwę wyświetlaną jawnie na inną wartość.  
  
 **Opis elementu**. Opis właściwości domeny pojawia się w dwóch miejscach:  
  
-   W dolnej części okna właściwości, jeśli użytkownik wybierze opcję Właściwości. Służy on do wyjaśnić użytkownikowi reprezentuje właściwość.  
  
-   W kodzie wygenerowanym programu. Użycie funkcji dokumentacji do wyodrębnienia dokumentacji interfejsu API, pojawi się jako opis tej właściwości w interfejsie API.  
  
 **Kategoria**. Kategoria jest pozycją w oknie właściwości.  
  
## <a name="exposing-style-features"></a>Udostępnianie w stylu funkcji  
 Niektóre funkcje dynamiczne elementy graficzne mogą być reprezentowane lub *widoczne* jako właściwości domeny. Funkcja, która została widoczne w ten sposób może być aktualizowany przez użytkownika i mogą łatwo można zaktualizowany przez kod programu.  
  
 Kliknij prawym przyciskiem myszy klasę kształtu w definicji DSL, wskaż pozycję **dodać widoczne**, a następnie wybierz pozycję funkcji.  
  
 Kształtów mogą uwidaczniać **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** i **FillGradientMode** właściwości. Na łączniki mogą uwidaczniać **kolor**`,`**TextColor**, **DashStyle**, i **grubość** właściwości. Na diagramach mogą uwidaczniać **FillColor** i **TextColor** właściwości.  
  
## <a name="forwarding-displaying-properties-of-related-elements"></a>Przekazywanie: Wyświetlanie właściwości powiązanych elementów  
 Gdy użytkownik sieci DSL wybiera element modelu, właściwości tego elementu są wyświetlane w oknie właściwości. Można jednak również wyświetlić właściwości określonych elementów pokrewnych. Jest to przydatne, jeżeli określono grupę elementów, który działa jednocześnie. Na przykład można zdefiniować elementu głównego i opcjonalny element wtyczki. Jeśli główny element jest zamapowany na kształt, a drugi nie, jest przydatne wyświetlić wszystkie ich właściwości, jak gdyby znajdowały się w jeden element.  
  
 W tym celu nosi nazwę *przekazywania właściwości*, i wykonywane automatycznie w kilku przypadkach. W pozostałych przypadkach można uzyskać właściwości przekazywania, definiując deskryptor typu domeny.  
  
### <a name="default-property-forwarding-cases"></a>Domyślna właściwość przekazywania przypadków  
 Po wybraniu przez użytkownika kształt lub łącznik lub elementu w Eksploratorze, następujące właściwości są wyświetlane w oknie właściwości:  
  
-   Właściwości domeny, które są zdefiniowane w klasie domeny element modelu, w tym te, które są zdefiniowane w klasach podstawowych. Wyjątkiem jest właściwości domeny, dla których wybrano **jest można przeglądać** do `False`.  
  
-   Nazwy elementów, które są połączone za pośrednictwem relacje, które mają liczebność od 0 do 1. Zapewnia to wygodna metoda została oglądania opcjonalnie połączone elementy, nawet jeśli nie zdefiniowano mapowania łącznika dla tej relacji.  
  
-   Właściwości domeny osadzania relacji, którego celem jest element. Ponieważ osadzania relacje zwykle nie są wyświetlane jawnie, dzięki temu użytkownik widzi ich właściwości.  
  
-   Właściwości domeny, które są zdefiniowane dla wybranego kształtu lub łącznika.  
  
### <a name="adding-property-forwarding"></a>Dodawanie właściwości przekazywania  
 Aby przesłać dalej właściwość, należy zdefiniować domeny deskryptor typu. Jeśli masz relacji domeny między dwiema klasami domeny służy deskryptor typu domeny można ustawić właściwości domeny w klasie pierwszej wartości właściwości domeny w klasie domeny drugiego. Na przykład, jeśli masz relację między **książki** klasy domeny i **autora** klasy domeny umożliwia deskryptor typu domeny należy **nazwa** właściwości Książki **autora** są wyświetlane w oknie właściwości, gdy użytkownik wybierze książce.  
  
> [!NOTE]
>  Przekazywanie właściwości ma wpływ na okno właściwości, gdy użytkownik edytuje modelu. Definiuje właściwości domeny na klasie odbierania. Jeśli chcesz uzyskać dostępu do właściwości domeny przekazywane w innych częściach definicji DSL lub w kodzie programu, możesz uzyskać dostęp element przekazywania.  
  
 W poniższej procedurze przyjęto, że utworzono DSL. Pierwsze kroki kilka Podsumowanie wymagań wstępnych.  
  
##### <a name="to-forward-a-property-from-another-element"></a>Przekazywanie właściwości z innego elementu  
  
1.  Utwórz [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] rozwiązania, który zawiera co najmniej dwie klasy, które w tym przykładzie są nazywane **książki** i **autora**. Powinien istnieć relacja dowolnego typu między **książki** i **autora**.  
  
     Liczebność roli źródłowej (rola w **książki** po stronie) powinna być od 0 do 1 lub 1.. 1, więc każdy **książki** ma jeden **autora**.  
  
2.  W **DSL Explorer**, kliknij prawym przyciskiem myszy **książki** klasy domeny, a następnie kliknij przycisk **Dodaj nowe DomainTypeDescriptor**.  
  
     Węzeł o nazwie **ścieżki niestandardowe właściwości deskryptory** jest wyświetlany w obszarze **deskryptora typu niestandardowego** węzła.  
  
3.  Kliknij prawym przyciskiem myszy **deskryptora typu niestandardowego** węzeł, a następnie kliknij przycisk **Dodaj nowe PropertyPath**.  
  
     Nowa ścieżka właściwości jest wyświetlana w obszarze **ścieżki niestandardowe właściwości deskryptory** węzła.  
  
4.  Wybierz nową ścieżkę właściwości oraz w **właściwości** ustaw **ścieżka do właściwości** do ścieżki elementu odpowiednie modelu.  
  
     Ścieżka w widoku drzewa można edytować, klikając strzałkę w dół na prawo od tej właściwości. Aby uzyskać więcej informacji na temat ścieżek domeny, zobacz [składnia ścieżki domeny](../modeling/domain-path-syntax.md). Po zakończeniu edycji go, ścieżka powinien wyglądać **BookReferencesAuthor.Author/! Autor**.  
  
5.  Ustaw **właściwości** do **nazwa** właściwość domeny **autora**.  
  
6.  Ustaw **Nazwa wyświetlana** do **nazwę autora**.  
  
7.  Przekształć wszystkie szablony, tworzenie i uruchamianie DSL.  
  
8.  Na diagramie modelu utworzyć książkę autora, a następnie połącz je przy użyciu relacji odwołania. Zaznacz element książki i w oknie właściwości powinny pojawić się nazwa autora oprócz właściwości książce. Zmień nazwę połączonego autora lub połączyć książce innego autora, a Sprawdź, czy nazwa autora książki zmiany.  
  
## <a name="custom-property-editors"></a>Edytory właściwości niestandardowej  
 W oknie właściwości zawiera domyślne odpowiednie dla każdej właściwości domeny typu edytowania. Na przykład dla typu wyliczeniowego, użytkownik zobaczy listy rozwijanej, a dla właściwości numerycznej, użytkownik może wprowadzić cyfr. Dotyczy to tylko typy wbudowane. Jeśli określisz typu zewnętrznego, użytkownik będzie mógł wyświetlić wartości właściwości, ale nie można go edytować.  
  
 Można jednak określić następujące edytory i typy:  
  
1.  Inny edytor jest używany z typem standardowa. Na przykład można określić Edytor ścieżki plików dla właściwości ciągu.  
  
2.  Typ zewnętrznej dla właściwości domeny i edytor.  
  
3.  Edytor .NET, takich jak edytor ścieżki pliku, lub można utworzyć właściwości niestandardowej edytora.  
  
     Konwersja między typu zewnętrznego i typu, na przykład ciąg, który ma domyślny edytor.  
  
 W DSL *typu zewnętrznego* jest dowolnego typu, który nie jest jednym z typów prostych (na przykład wartość logiczna lub Int32) lub ciąg.  
  
#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Aby zdefiniować właściwości domeny, która ma typ zewnętrznej  
  
1.  W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu (DLL), który zawiera typ zewnętrznej w **Dsl** projektu.  
  
     Zestaw może być zestawem .NET lub zestawu dostarczone przez użytkownika.  
  
2.  Dodaj typ do **typów domeny** listy, o ile jeszcze zrobiono.  
  
    1.  Otwórz DslDefinition.dsl i w **DSL Explorer**, kliknij prawym przyciskiem myszy węzeł główny, a następnie kliknij przycisk **dodać nowy typ zewnętrznej**.  
  
         Nowy wpis jest wyświetlany w obszarze **typów domeny** węzła.  
  
        > [!WARNING]
        >  Element menu jest na węzeł główny DSL **typów domeny** węzła.  
  
    2.  W oknie właściwości można ustawić nazwy i przestrzeni nazw nowego typu.  
  
3.  Dodawanie właściwości domeny do klasy domeny w zwykły sposób.  
  
     W oknie właściwości, wybierz typ zewnętrznej z listy rozwijanej w **typu** pola.  
  
 Na tym etapie użytkownicy mogą wyświetlać wartości właściwości, ale nie można go edytować. Wyświetlane wartości są uzyskiwane z `ToString()` funkcji. Można napisać kod program, który ustawia wartości właściwości, na przykład w poleceniu lub reguły.  
  
### <a name="setting-a-property-editor"></a>Ustawienia edytora właściwości  
 Dodaj atrybut CLR dla właściwości domeny w następującej postaci:  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Ten atrybut zostanie ustawiony we właściwości, za pomocą **atrybut niestandardowy** wpis w oknie właściwości.  
  
 Typ `AnEditor` musi pochodzić z typu określonego w parametrze drugiego. Drugi parametr powinien być <xref:System.Drawing.Design.UITypeEditor> lub <xref:System.ComponentModel.ComponentEditor>. Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.EditorAttribute>.  
  
 Możesz określić własne Edytor lub podane w edytorze [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], takich jak <xref:System.Windows.Forms.Design.FileNameEditor> lub <xref:System.Drawing.Design.ImageEditor>. Na przykład można użyć poniższej procedury do właściwości, w którym użytkownik może wprowadzić nazwę pliku.  
  
##### <a name="to-define-a-file-name-domain-property"></a>Aby zdefiniować właściwości domeny nazwy pliku  
  
1.  Dodaj właściwość domeny do domeny klasy w definicji DSL.  
  
2.  Wybierz nową właściwość. W **atrybut niestandardowy** pola w oknie właściwości, należy wprowadzić następujące atrybutu. Aby wprowadzić ten atrybut, kliknij przycisk wielokropka **[...]**  , a następnie wprowadź nazwę atrybutu i parametrów oddzielnie:  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  Pozostaw typ właściwości domeny ustawień domyślnych **ciąg**.  
  
4.  Aby przetestować edytora, sprawdź, czy użytkownicy otworzyć edytora nazwy pliku do edycji właściwości użytkownika domeny.  
  
    1.  Naciśnij klawisze CTRL + F5 lub F5. W rozwiązaniu debugowania Otwórz plik testu. Utwórz element klasy domeny i zaznacz go.  
  
    2.  W oknie właściwości wybierz właściwość domeny. Pole wartości zawiera wielokropek **[...]** .  
  
    3.  Kliknij przycisk wielokropka. Zostanie wyświetlone okno dialogowe pliku. Wybierz plik i zamknij okno dialogowe. Ścieżka pliku jest teraz wartość właściwości domeny.  
  
### <a name="defining-your-own-property-editor"></a>Definiowanie edytora właściwości  
 Możesz definiować własne edytora. Należy to pozwala użytkownikom, aby edytować typu, który został zdefiniowany lub do edytowania typu standardowe w specjalny sposób. Można na przykład umożliwiają użytkownikom wprowadź ciąg reprezentujący formuły.  
  
 Zdefiniuj edytora pisząc klasę, która jest pochodną <xref:System.Drawing.Design.UITypeEditor>. Przesłonięcie klasy:  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, do interakcji z użytkownikiem i zaktualizuj wartość właściwości.  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, aby określić, czy edytor będzie Otwórz okno dialogowe lub Zapewnij menu rozwijanego.  
  
 Można też podać graficzna reprezentacja wartości właściwości, który będzie wyświetlany w siatce właściwości. Aby to zrobić, należy zastąpić `GetPaintValueSupported`, i `PaintValue`.  Aby uzyskać więcej informacji, zobacz <xref:System.Drawing.Design.UITypeEditor>.  
  
> [!NOTE]
>  Dodaj kod w osobnym pliku kodu w **Dsl** projektu.  
  
 Na przykład:  
  
```  
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor  
{  
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)  
  {  
    base.InitializeDialog(openFileDialog);  
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";  
    openFileDialog.Title = "Select a text file";  
  }  
}  
  
```  
  
 Aby używać tego edytora, ustaw **atrybut niestandardowy** właściwości domeny na:  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Drawing.Design.UITypeEditor>.  
  
## <a name="providing-a-drop-down-list-of-values"></a>Zapewnianie rozwijalna lista wartości  
 Można podać listę wartości dla użytkownika do wyboru.  
  
> [!NOTE]
>  Ta technika zawiera listę wartości, które można zmienić w czasie wykonywania. Jeśli chcesz podać listy, który nie ulega zmianie, zamiast tego rozważ przy użyciu Typ wyliczany jako typ właściwości użytkownika domeny.  
  
 Aby zdefiniować listę wartości domyślnych, należy dodać do Twojej domeny właściwości atrybutu CLR, która ma następujący format:  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 Definiowanie klasy, która jest pochodną <xref:System.ComponentModel.TypeConverter>. Dodaj kod w osobnym pliku w **Dsl** projektu. Na przykład:  
  
```csharp  
/// <summary>  
/// Type converter that provides a list of values   
/// to be displayed in the property grid.  
/// </summary>  
/// <remarks>This type converter returns a list   
/// of the names of all "ExampleElements" in the   
/// current store.</remarks>  
public class MyTypeConverter : System.ComponentModel.TypeConverter  
{  
  /// <summary>  
  /// Return true to indicate that we return a list of values to choose from  
  /// </summary>  
  /// <param name="context"></param>  
  public override bool GetStandardValuesSupported  
    (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Returns true to indicate that the user has   
  /// to select a value from the list  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>If we returned false, the user would   
  /// be able to either select a value from   
  /// the list or type in a value that is not in the list.</returns>  
  public override bool GetStandardValuesExclusive  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Return a list of the values to display in the grid  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>A list of values the user can choose from</returns>  
  public override StandardValuesCollection GetStandardValues  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    // Try to get a store from the current context  
    // "context.Instance"  returns the element(s) that   
    // are currently selected i.e. whose values are being  
    // shown in the property grid.   
    // Note that the user could have selected multiple objects,   
    // in which case context.Instance will be an array.  
    Store store = GetStore(context.Instance);  
  
    List<string> values = new List<string>();  
  
    if (store != null)  
    {  
      values.AddRange(store.ElementDirectory  
        .FindElements<ExampleElement>()  
        .Select<ExampleElement, string>(e =>   
      {  
        return e.Name;  
      }));  
    }  
    return new StandardValuesCollection(values);  
  }  
  
  /// <summary>  
  /// Attempts to get to a store from the currently selected object(s)  
  /// in the property grid.  
  /// </summary>  
  private Store GetStore(object gridSelection)  
  {  
    // We assume that "instance" will either be a single model element, or   
    // an array of model elements (if multiple items are selected).  
  
    ModelElement currentElement = null;  
  
    object[] objects = gridSelection as object[];  
    if (objects != null && objects.Length > 0)  
    {  
      currentElement = objects[0] as ModelElement;  
    }  
    else  
    {  
        currentElement = gridSelection as ModelElement;  
    }  
  
    return (currentElement == null) ? null : currentElement.Store;  
  }  
  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)