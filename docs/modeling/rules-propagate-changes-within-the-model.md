---
title: Reguły Propaguj zmiany w modelu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: af43a323676eb977b3e722dd4a677976790a8d5f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="rules-propagate-changes-within-the-model"></a>Reguły propagujące zmiany w modelu
Można utworzyć regułę magazynu propagację zmiany jednego elementu na inny wizualizacji i modelowania SDK (VMSDK). W przypadku zmiany do dowolnego elementu w magazynie, zasady nie zostały zaplanowane wykonywane zwykle, gdy peryferyjnych transakcja została przekazana. Istnieją różne typy reguł dla różnych rodzajów zdarzeń, takich jak dodawanie elementu, lub usunięcie go. Zasady można dołączyć do określonych typów elementów, kształtów lub diagramy. Wiele wbudowanych funkcji zdefiniowanych przez zasady: na przykład zasady upewnij się, że diagram został zaktualizowany po zmianie modelu. Języka specyficznego dla domeny można dostosować, dodając własnych reguł.  
  
 Reguły magazynu są szczególnie przydatne, propagowanie zmian w magazynie — to znaczy zmiany do elementów modelu, relacje kształtów lub łączników i ich domeny właściwości. Zasady nie działają, gdy użytkownik wywołuje poleceń Cofnij i ponów. Zamiast tego menedżera transakcji sprawdza, czy zawartość magazynu zostaną przywrócone nieprawidłowy stan. Jeśli chcesz propagujące zmiany do zasobów poza Sklepem, należy użyć przechowywania zdarzeń. Aby uzyskać więcej informacji, zobacz [obsługi Propaguj zmiany poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Załóżmy na przykład, że chcesz określić, czy zawsze, gdy użytkownik (lub kodu) tworzy nowy element typu ExampleDomainClass, dodatkowy element innego typu został utworzony w innej części modelu. Można zapisać AddRule i skojarzyć go z ExampleDomainClass. W regule można utworzyć dodatkowe elementu piszesz kodu.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  
  
    // Code here propagates change as required - for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  
  
```  
  
> [!NOTE]
>  Kod regułę, należy zmienić stan tylko elementy wewnątrz magazynu; oznacza to regułę, należy zmienić tylko elementy modelu, relacje, kształtów, łączniki, diagramy lub ich właściwości. Propagowanie zmian do zasobów poza Sklepem, należy zdefiniować przechowywania zdarzeń. Aby uzyskać więcej informacji, zobacz [obsługi Propaguj zmiany poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### <a name="to-define-a-rule"></a>Aby zdefiniować regułę  
  
1.  Zdefiniować regułę, zgodnie z prefiksem klasy `RuleOn` atrybutu. Atrybut kojarzy regułę z jednej domeny klas, relacji lub elementów diagramu. Reguła zostanie zastosowana do każdego wystąpienia tej klasy, która może być abstrakcyjny.  
  
2.  Zarejestruj reguły przez dodanie go do zestaw zwrócony przez `GetCustomDomainModelTypes()` w klasie modelu domeny.  
  
3.  Pochodzi z klasy regułę z jednej z klas abstrakcyjnych reguły i zapisać kod metody wykonywania.  
  
 W poniższych sekcjach opisano te kroki bardziej szczegółowo.  
  
### <a name="to-define-a-rule-on-a-domain-class"></a>Aby zdefiniować regułę dla klasy domeny  
  
-   W pliku kodu niestandardowego, Definiowanie klasy, a następnie poprzedzić go <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> atrybutu:  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value - but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   Typ tematu w pierwszym parametrze może być klasy domeny, relacji domeny, kształtu, łącznik lub diagram. Zazwyczaj należy zastosować zasady do klasy i relacje.  
  
     `FireTime` Jest zwykle `TopLevelCommit`. Dzięki temu, że reguła jest wykonywane tylko wtedy, gdy wszystkie zmiany głównej transakcji zostały wprowadzone. Alternatywami są wbudowane, który wykonuje regułę wkrótce po zmianie; i LocalCommit, który wykonuje regułę po zakończeniu bieżącej transakcji (który nie może być najbardziej zewnętrznego). Można również ustawić priorytet reguły wpływa na kolejności w kolejce, ale jest to metoda zawodnych osiągnięcia wyników, które są wymagane.  
  
-   Jako typ podmiotu można określić klasy abstrakcyjnej.  
  
-   Ta reguła ma zastosowanie do wszystkich wystąpień klasy podmiotu.  
  
-   Wartość domyślna dla `FireTime` jest TimeToFire.TopLevelCommit. Powoduje to, że reguła ma być wykonywana w przypadku najbardziej zewnętrznego transakcja została przekazana. Alternatywą jest TimeToFire.Inline. Powoduje to, że reguła ma być wykonywana wkrótce po wyzwalająca zdarzenia.  
  
### <a name="to-register-the-rule"></a>Aby zarejestrować reguły  
  
-   Dodaj regułę klasy do listy typów zwróconych przez `GetCustomDomainModelTypes` modelu domeny:  
  
    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  
  
    ```  
  
-   Jeśli nie masz pewności nazwy klasy modelu domeny, Szukaj w plik **Dsl\GeneratedCode\DomainModel.cs**  
  
-   Napisać ten kod w pliku kodu niestandardowego, w projekcie DSL.  
  
### <a name="to-write-the-code-of-the-rule"></a>Pisanie kodu reguły  
  
-   Pochodną klasy reguły jedna z następujących klas podstawowych:  
  
    |Klasa podstawowa|Wyzwalacz|  
    |----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Dodawany jest element link i kształtu.<br /><br /> Umożliwia to wykryć nowe relacje, oprócz nowych elementów.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|Wartość właściwości domeny została zmieniona. Argument metody zawiera starej i nowej wartości.<br /><br /> Kształtów, ta reguła jest wyzwalana, gdy wbudowane `AbsoluteBounds` zmiany właściwości, jeśli jest przesuwany.<br /><br /> W wielu przypadkach jest wygodniejsze do przesłonięcia `OnValueChanged` lub `OnValueChanging` w obsłudze właściwości. Te metody są wywoływane bezpośrednio przed i po zmianie. Z drugiej strony gdy zasada jest wykonywana zwykle na końcu transakcji. Aby uzyskać więcej informacji, zobacz [obsługi zmiany wartości właściwości domeny](../modeling/domain-property-value-change-handlers.md). **Uwaga:** ta zasada nie jest wyzwalane, gdy łącze zostało utworzone lub usunięte. Zamiast tego należy zapisać `AddRule` i `DeleteRule` dla relacji domeny.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Wyzwalane, gdy element lub łącze jest ma zostać usunięta. Właściwość ModelElement.IsDeleting ma wartość true, aż do zakończenia transakcji.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Wykonywane po usunięciu elementu lub łącza. Zasada jest wykonywana po zostały wykonane wszystkie inne zasady, w tym DeletingRules. ModelElement.IsDeleting ma wartość false, a ModelElement.IsDeleted ma wartość true. Aby umożliwić kolejnych cofania, element nie jest usuwany z pamięci, ale są one usuwane ze Store.ElementDirectory.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Element jest przenoszony z jednego magazynu partycji do innej.<br /><br /> (Należy zauważyć, że to nie jest powiązany z graficznego pozycji kształtu).|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Ta reguła dotyczy tylko relacji domeny. Wyzwalany jest jawnie przypisania elementu modelu na dowolnym jej końcu łącza.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Wyzwalane, gdy zostanie zmieniona kolejność łącza do lub z elementu, przy użyciu metod MoveBefore lub MoveToIndex łącze.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Należy wykonać po utworzeniu transakcji.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Wykonywać, gdy transakcja ma zostać zatwierdzone.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Wykonywać, gdy transakcja zostanie wycofana.|  
  
-   Każda klasa ma metodę można przesłonić. Typ `override` w klasie w celu odnalezienia. Parametr tej metody identyfikuje element, który został zmieniony.  
  
 Zwróć uwagę następujące kwestie dotyczące reguł:  
  
1.  Zestaw zmian w transakcji może wyzwolić wiele reguł. Zazwyczaj reguły są wykonywane, gdy peryferyjnych transakcja została przekazana. Są one wykonywane w nieokreślonej kolejności.  
  
2.  Reguła jest zawsze wykonywana wewnątrz transakcji. W związku z tym nie trzeba tworzyć nowej transakcji, aby wprowadzić zmiany.  
  
3.  Zasady nie są wykonywane, gdy transakcja zostanie wycofana, lub gdy wykonywane są operacje cofania lub ponownego wykonywania. Te operacje resetowania całą zawartość magazynu do jego poprzedniego stanu. W związku z tym jeśli reguła zmieni się stan niczego poza Sklepem, go może nie należy przechowywać w synchronism z magazynem zawartości. Aby zaktualizować stan poza Sklepem, zaleca się korzystanie ze zdarzeń. Aby uzyskać więcej informacji, zobacz [obsługi Propaguj zmiany poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Niektóre reguły są wykonywane, gdy model jest załadowanego z pliku. Aby określić, czy podczas ładowania lub zapisywania jest w toku, użyj `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Jeśli kod reguły tworzy więcej reguły wyzwalaczy, zostanie dodany na końcu listy uruchamiania i zostanie wykonane przed zakończeniem transakcji. DeletedRules są wykonywane po wszystkich pozostałych reguł. Jedna reguła można uruchomić wiele razy w transakcji, jeden raz dla każdej zmiany.  
  
6.  Do przekazywania informacji do i z reguł, można przechowywać informacje w `TransactionContext`. Jest to po prostu słownik jest obsługiwane podczas wykonywania tej transakcji. Jest on usunięty po zakończeniu transakcji. Argumenty zdarzenia w każdej regule zapewnić do niego dostęp. Należy pamiętać, zasady nie są wykonywane w przewidywalnej kolejności.  
  
7.  Użyj reguł po uwzględnieniu alternatywnych. Na przykład jeśli chcesz zaktualizować właściwości, gdy zostanie zmieniona wartość, należy rozważyć użycie obliczonej właściwości. Jeśli chcesz ograniczyć rozmiar lub lokalizacji kształtu, użyj `BoundsRule`. Aby odpowiedzieć na zmiany w wartości właściwości, należy dodać `OnValueChanged` obsługi do właściwości. Aby uzyskać więcej informacji, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład aktualizacji właściwości, gdy relacja domeny zostanie uruchomiony do łączenia dwóch elementów. Reguła zostanie wyzwolone nie tylko w przypadku, gdy użytkownik tworzy łącze na diagramie, ale także jeśli kod program tworzy łącze.  
  
 Do testowania w tym przykładzie, Utwórz DSL, przy użyciu szablonu rozwiązania przepływ zadań i Wstaw następujący kod w pliku w projekcie Dsl. Kompilacji i uruchomić rozwiązanie, a następnie otwórz przykładowy plik w projekcie debugowanie. Rysuj Linku komentarza między kształcie komentarza i elementu przepływu. Raportu w elemencie najbardziej aktualnych podłączonej do zmiany tekstu w komentarzu.  
  
 W praktyce zwykle piszesz DeleteRule dla każdego AddRule.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.TaskRuleExample  
{  
  
  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  
  
    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  
  
  }  
  
  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  
  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Propaguj zmiany poza modelu do obsługi zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules — ograniczenie lokalizacji i rozmiaru kształtu](../modeling/boundsrules-constrain-shape-location-and-size.md)