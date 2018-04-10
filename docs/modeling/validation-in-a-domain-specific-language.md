---
title: Sprawdzanie poprawności języka specyficznego dla domeny | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7eb2e734bd94608584ca700223fb75387eb484fb
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="validation-in-a-domain-specific-language"></a>Sprawdzanie poprawności w języku specyficznym dla domeny
Jako autor języka specyficznego dla domeny (DSL) można zdefiniować ograniczenia walidacji, aby sprawdzić, czy model utworzone przez użytkownika jest łatwy do rozpoznania. Na przykład jeśli Twoje DSL umożliwia użytkownikom rysowanie drzewa rodziny osób i ich elementów nadrzędnych, można zapisać ograniczenia, które gwarantuje, że elementy podrzędne daty urodzenia po ich elementów nadrzędnych.  
  
 Może mieć ograniczenia walidacji wykonać po zapisaniu modelu, gdy jest otwarta, a jeśli użytkownik jawnie uruchamia **weryfikacji** polecenia menu. Można również uruchomić sprawdzanie poprawności pod kontrolą programu. Na przykład można wykonać walidacji w odpowiedzi na zmianę wartości właściwości lub relacji.  
  
 Sprawdzanie poprawności jest szczególnie ważne podczas pisania szablonów tekstowych lub innych narzędzi, które przetwarzają modeli użytkowników. Sprawdzanie poprawności zapewnia, że modele spełniają warunki wstępne, przyjmowana przez te narzędzia.  
  
> [!WARNING]
>  Możesz również zezwolić ograniczenia sprawdzania poprawności określonych w oddzielnych rozszerzenia do Twojej DSL oraz polecenia menu rozszerzenia i obsługi gestów. Użytkownicy, można zainstalować te rozszerzenia, oprócz sieci DSL. Aby uzyskać więcej informacji, zobacz [rozszerzyć Twoje DSL przy użyciu MEF](../modeling/extend-your-dsl-by-using-mef.md).  
  
## <a name="running-validation"></a>Wykonywania sprawdzenia poprawności  
 Gdy użytkownik edytuje modelu, oznacza to, wystąpienie język specyficznego dla domeny następujące akcje można uruchomić sprawdzania poprawności:  
  
-   Kliknij prawym przyciskiem myszy diagram i wybierz **zweryfikować wszystkie**.  
  
-   Kliknij prawym przyciskiem myszy górny węzeł w Eksploratorze DSL i wybierz **Sprawdź poprawność wszystkich**  
  
-   Zapisz model.  
  
-   Otwórz model.  
  
-   Ponadto można napisać kod program, który jest uruchamiany weryfikacji, na przykład jako część polecenia menu lub w odpowiedzi na zmianę.  
  
 Wszystkie błędy weryfikacji będą wyświetlane w **listy błędów** okna. Użytkownik może kliknąć dwukrotnie komunikat o błędzie, aby wybrać elementy modelu, które są przyczyną tego błędu.  
  
## <a name="defining-validation-constraints"></a>Definiowanie ograniczeń walidacji  
 Należy zdefiniować ograniczenia sprawdzania poprawności przez dodanie metody sprawdzania poprawności do domeny klas lub relacji z DSL. Po uruchomieniu sprawdzania poprawności przez użytkownika lub pod kontrolą programu niektóre lub wszystkie metody weryfikacji są wykonywane. Każda metoda jest stosowana do każdego wystąpienia swojej klasy, a każda klasa może być kilka metod weryfikacji.  
  
 Każda metoda weryfikacji zgłasza błędy znalezione.  
  
> [!NOTE]
>  Sprawdzanie poprawności metody raportów o błędach, ale nie należy zmieniać modelu. Jeśli chcesz dostosować lub uniemożliwić pewnych zmian, zobacz [alternatywy dla weryfikacji](#alternatives).  
  
#### <a name="to-define-a-validation-constraint"></a>Aby zdefiniować ograniczenie sprawdzania poprawności  
  
1.  Włącz sprawdzanie poprawności w **Editor\Validation** węzła:  
  
    1.  Open **Dsl\DslDefinition.dsl**.  
  
    2.  W Eksploratorze DSL rozwiń **edytor** a następnie wybierz węzeł **weryfikacji**.  
  
    3.  W oknie właściwości ustaw **używa** właściwości `true`. Jest najodpowiedniejszym ustawić te właściwości.  
  
    4.  Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań.  
  
2.  Zapis definicje klas częściowych dla co najmniej jednej klasy domeny i relacje domeny. Zapisywanie te definicje w pliku kodu w **Dsl** projektu.  
  
3.  Prefiks każdej klasy z tym atrybutem:  
  
    ```csharp  
    [ValidationState(ValidationState.Enabled)]  
    ```  
  
    -   Domyślnie ten atrybut umożliwi sprawdzania poprawności dla klas pochodnych. Jeśli chcesz wyłączyć sprawdzania poprawności dla określonej klasy pochodnej, możesz użyć `ValidationState.Disabled`.  
  
4.  Dodaj metody sprawdzania poprawności dla klasy. Każda metoda weryfikacji może mieć dowolną nazwę, ale mieć jeden parametr typu <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext>.  
  
     Musi być poprzedzona z co najmniej jednym `ValidationMethod` atrybuty:  
  
    ```csharp  
    [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]  
    ```  
  
     ValidationCategories Określ, kiedy metoda jest wykonywana.  
  
 Na przykład:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
  
// Allow validation methods in this class:  
[ValidationState(ValidationState.Enabled)]  
// In this DSL, ParentsHaveChildren is a domain relationship  
// from Person to Person:  
public partial class ParentsHaveChildren  
{  
  // Identify the method as a validation method:  
  [ValidationMethod  
  ( // Specify which events cause the method to be invoked:  
    ValidationCategories.Open // On file load.  
  | ValidationCategories.Save // On save to file.  
  | ValidationCategories.Menu // On user menu command.  
  )]  
  // This method is applied to each instance of the   
  // type (and its subtypes) in a model:   
  private void ValidateParentBirth(ValidationContext context)     
  {  
    // In this DSL, the role names of this relationship  
    // are "Child" and "Parent":   
     if (this.Child.BirthYear < this.Parent.BirthYear   
        // Allow user to leave the year unset:  
        && this.Child.BirthYear != 0)  
      {  
        context.LogError(  
             // Description:  
                       "Child must be born after Parent",  
             // Unique code for this error:  
                       "FAB001ParentBirthError",   
              // Objects to select when user double-clicks error:  
                       this.Child,   
                       this.Parent);  
    }  
  }  
```  
  
 Zwróć uwagę następujące kwestie dotyczące tego kodu:  
  
-   Metody sprawdzania poprawności można dodać do domeny klas lub relacji domeny. Kod dla tych typów znajduje się w **Dsl\Generated Code\Domain\*.cs**.  
  
-   Każda metoda sprawdzania poprawności jest stosowany do każde wystąpienie danej klasy i jej podklas. W przypadku relacji domeny każde wystąpienie jest połączenie między dwoma elementami modelu.  
  
-   Metody sprawdzania poprawności nie są stosowane w dowolnej kolejności, a każda metoda nie ma zastosowania do wystąpienia klasy jej w dowolnej kolejności wartości prognozowanych.  
  
-   Jest zwykle złe rozwiązanie dla metody weryfikacji zaktualizować zawartość magazynu, ponieważ może to prowadzić do niespójnych wyników. Zamiast tego raportu błędu przez wywołanie metody `context.LogError`, `LogWarning` lub `LogInfo`.  
  
-   W wywołaniu LogError musisz podać listę elementów modelu lub linki relacji, które można wybrać, gdy użytkownik kliknie dwukrotnie w komunikacie o błędzie.  
  
-   Aby uzyskać informacje o sposobie odczytywanie modelu w kodzie programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Przykład dotyczy następujących modelu domeny. Relacja ParentsHaveChildren ma ról, które są nazywane nadrzędnym a podrzędnym.  
  
 ![Diagram definicji DSL &#45; model drzewa rodziny](../modeling/media/familyt_person.png "FamilyT_Person")  
  
## <a name="validation-categories"></a>Sprawdzanie poprawności kategorii  
 W <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> atrybutu, należy określić, gdy metoda uwierzytelniania, które mają zostać wykonane.  
  
|Kategoria|Wykonanie|  
|--------------|---------------|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy użytkownik wywołuje polecenie menu weryfikacji.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Po otwarciu pliku modelu.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy plik jest zapisywany. Jeśli występują błędy sprawdzania poprawności, użytkownik będzie mógł skorzystać z opcji Zapisz anulowanie operacji.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy plik jest zapisywany. W przypadku błędów z metody w tej kategorii użytkownika jest ostrzeżenie, że może nie być możliwe ponownie otworzyć plik.<br /><br /> Ta kategoria dla metody weryfikacji, które test zduplikowane nazwy lub identyfikatory lub inne warunki, które mogą powodować błędy ładowania.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Gdy wywoływana jest metoda ValidateCustom. Sprawdzanie poprawności w tej kategorii można wywołać tylko w kodzie programu.<br /><br /> Aby uzyskać więcej informacji, zobacz [niestandardowe kategorie weryfikacji](#custom).|  
  
## <a name="where-to-place-validation-methods"></a>Gdzie umieścić metody sprawdzania poprawności  
 Często można osiągnąć ten sam efekt, umieszczając metodę sprawdzania poprawności na innego typu. Można na przykład dodać metodę do klasy osoby zamiast relacji ParentsHaveChildren i jego iterację łącza:  
  
```  
[ValidationState(ValidationState.Enabled)]  
public partial class Person  
{[ValidationMethod  
 ( ValidationCategories.Open   
 | ValidationCategories.Save  
 | ValidationCategories.Menu  
 )  
]  
  private void ValidateParentBirth(ValidationContext context)     
  {  
    // Iterate through ParentHasChildren links:  
    foreach (Person parent in this.Parents)  
    {  
        if (this.BirthYear <= parent.BirthYear)  
        { ...  
  
```  
  
 **Agregowanie ograniczenia sprawdzania poprawności.** Aby zastosować sprawdzanie poprawności w przewidywalnej kolejności, należy zdefiniować metodę sprawdzania poprawności pojedynczego w klasie właściciela, takiego elementu głównego modelu. Ta technika pozwala również skumulować wiele raportów o błędach w pojedynczym komunikacie.  
  
 Wady są czy łączona metoda jest mniej łatwiejsze w zarządzaniu i że ograniczenia musi wszystkie mają taki sam `ValidationCategories`. Dlatego zaleca się zachowanie każdego ograniczenia w oddzielnych metodach Jeśli to możliwe.  
  
 **Przekazywanie wartości w pamięci podręcznej kontekstu.** Parametr kontekstu ma słownika, w którym można umieszczać dowolne wartości. Słownik utrzymuje się przez cały okres istnienia uruchomienie sprawdzania poprawności. Metodę sprawdzania poprawności określonego można na przykład zachować liczba błędów w kontekście i umożliwia uniknąć przepełnienia okna błąd z powtarzane wiadomości. Na przykład:  
  
```csharp  
List<ParentsHaveChildren> erroneousLinks;  
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))  
erroneousLinks = new List<ParentsHaveChildren>();  
erroneousLinks.Add(this);  
context.SetCacheValue("erroneousLinks", erroneousLinks);  
if (erroneousLinks.Count < 5) { context.LogError( ... ); }  
  
```  
  
## <a name="validation-of-multiplicities"></a>Sprawdzanie poprawności liczebnościami powodującymi  
 Metody weryfikacji kontroli minimalna liczebności są generowane automatycznie dla użytkownika DSL. Kod jest zapisywany w **Dsl\Generated Code\MultiplicityValidation.cs**. Te metody obowiązywać po włączeniu weryfikacji w **Editor\Validation** węzła w Eksploratorze DSL.  
  
 Jeśli ustawisz Liczebność roli relacji domeny 1.. * lub 1..1, ale użytkownik nie tworzy łącze tę relację, pojawi się komunikat o błędzie weryfikacji.  
  
 Na przykład, jeśli Twoje DSL ma klas osoby i miejscowość i relacji PersonLivesInTown przy użyciu relacji **1..\***  w ramach roli miejscowość to dla każdej osoby, które ma nie odbędzie się komunikat o błędzie pojawi się.  
  
## <a name="running-validation-from-program-code"></a>Uruchamianie sprawdzania poprawności z kodu programu  
 Uzyskiwanie dostępu lub tworząc ValidationController można uruchomić sprawdzania poprawności. Jeśli chcesz błędów, który będzie wyświetlany użytkownikowi w oknie błędów, użyj ValidationController, który jest dołączony do danych dokumentu do diagramu. Na przykład, jeśli piszesz polecenia menu `CurrentDocData.ValidationController` jest dostępna w klasie zestaw poleceń:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
partial class MyLanguageCommandSet   
{  
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)   
  {   
   ValidationController controller = this.CurrentDocData.ValidationController;   
...  
  
```  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dodawanie polecenia do Menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
 Można również utworzyć kontroler oddzielne sprawdzania poprawności i samodzielnie zarządzać błędy. Na przykład:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
Store store = ...;  
VsValidationController validator = new VsValidationController(s);  
// Validate all elements in the Store:  
if (!validator.Validate(store, ValidationCategories.Save))  
{  
  // Deal with errors:  
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }  
}  
  
```  
  
## <a name="running-validation-when-a-change-occurs"></a>Wykonywania sprawdzenia poprawności w przypadku zmiany  
 Jeśli chcesz upewnić się, że użytkownik jest ostrzeżenie, natychmiast modelu staje się nieprawidłowy, można zdefiniować zdarzenie magazynu, które uruchamia sprawdzania poprawności. Aby uzyskać więcej informacji o zdarzeniach magazynu, zobacz [obsługi Propaguj zmiany poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Oprócz kodu walidacji dodać plik kodu niestandardowego do Twojej **DslPackage** projektu z zawartością podobny do poniższego przykładu. Ten kod zawiera `ValidationController` dołączona do dokumentu. Ten kontroler przedstawia błędy sprawdzania poprawności w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] listy błędów.  
  
```csharp  
using System;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
namespace Company.FamilyTree  
{  
  partial class FamilyTreeDocData // Change name to your DocData.  
  {  
    // Register the store event handler:   
    protected override void OnDocumentLoaded()  
    {  
      base.OnDocumentLoaded();  
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory  
         .FindDomainClass(typeof(ParentsHaveChildren));  
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory  
         .FindDomainClass(typeof(Person));  
      EventManagerDirectory events = this.Store.EventManagerDirectory;  
      events.ElementAdded  
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));  
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));  
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));  
    }  
    // Handler will be called after transaction that creates a link:  
    private void ParentLinkAddedHandler(object sender,  
                                ElementAddedEventArgs e)  
    {  
      this.ValidationController.Validate(e.ModelElement,  
           ValidationCategories.Save);  
    }  
    // Called when a link is deleted:  
    private void ParentLinkDeletedHandler(object sender,   
                                ElementDeletedEventArgs e)  
    {  
      // Don't apply validation to a deleted item!   
      // - Validate store to refresh the error list.  
      this.ValidationController.Validate(this.Store,  
           ValidationCategories.Save);  
    }  
    // Called when any property of a Person element changes:  
    private void BirthDateChangedHandler(object sender,  
                      ElementPropertyChangedEventArgs e)  
    {  
      Person person = e.ModelElement as Person;  
      // Not interested in changes in other properties:  
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)  
          return;  
  
      // Validate all parent links to and from the person:  
      this.ValidationController.Validate(  
        ParentsHaveChildren.GetLinksToParents(person)  
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))  
        , ValidationCategories.Save);  
    }  
  }  
}  
  
```  
  
 Programy obsługi są również nazywane po cofania lub ponownego wykonywania operacji, które mają wpływ na łącza lub elementów.  
  
##  <a name="custom"></a> Kategorie walidacji niestandardowej  
 Oprócz kategorie weryfikacji standardowe, takie jak Menu i otworzyć można definiować własne kategorie. Można wywołać tych kategorii w kodzie programu. Użytkownik nie może wywołać je bezpośrednio.  
  
 Typowym zastosowaniem niestandardowe kategorie jest zdefiniowanie kategorię, która sprawdza, czy model spełnia warunki wstępne określonego narzędzia.  
  
 Aby dodać metodę sprawdzania poprawności do określonej kategorii, należy poprzedzić go z atrybutem następująco:  
  
```csharp  
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]  
[ValidationMethod(ValidationCategory.Menu)]   
private void TestForCircularLinks(ValidationContext context)   
{...}  
  
```  
  
> [!NOTE]
>  Można prefiksu metody z dowolną liczbę `[ValidationMethod()]` atrybuty żądanej. Metoda można dodać do standardowych i niestandardowych kategorii.  
  
 Aby wywołać niestandardowego sprawdzania poprawności:  
  
```csharp  
  
// Invoke all validation methods in a custom category:   
validationController.ValidateCustom  
  (store, // or a list of model elements  
   "PreconditionsForGeneratePartsList");  
```  
  
##  <a name="alternatives"></a> Alternatywy dla weryfikacji  
 Ograniczenia walidacji raportów o błędach, ale nie należy zmieniać modelu. Jeśli jednak chcesz zapobiec modelu staje się nieprawidłowy, można użyć innych technik.  
  
 Jednak nie zaleca się skorzystanie z tych metod. Zazwyczaj najlepiej zezwala użytkownikowi na określenie, jak poprawić nieprawidłowy model.  
  
 **Dostosuj zmiany, aby przywrócić modelu ważności.** Na przykład właściwość powyżej maksymalną dozwoloną liczbę ustawiony przez użytkownika, można zresetować właściwości wartości maksymalnej. Aby to zrobić, należy zdefiniować regułę. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
 **Wycofaj tę transakcję próbie nieprawidłowe zmiany.** W tym celu można również zdefiniować regułę, ale w niektórych przypadkach można zastąpić właściwości program obsługi jest **OnValueChanging()**, lub aby zastąpić metody, takie jak `OnDeleted().` można wycofać transakcji, użyj `this.Store.TransactionManager.CurrentTransaction.Rollback().` Aby uzyskać więcej informacji informacje, zobacz [obsługi zmiany wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md).  
  
> [!WARNING]
>  Upewnij się, że użytkownik wie, że zmiana została dostosowana lub wycofana. Na przykład użyć `System.Windows.Forms.MessageBox.Show("message").`  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Programy obsługi zdarzeń propagujące zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md)