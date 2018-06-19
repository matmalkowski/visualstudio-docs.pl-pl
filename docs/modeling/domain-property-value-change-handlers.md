---
title: Programy obsługi zmiany wartości właściwości domeny w programie Visual Studio
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f1244bed2057de3e9a3dc3ddb7fd61a989e18ded
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950793"
---
# <a name="domain-property-value-change-handlers"></a>Obsługa zmiany wartości właściwości domeny

W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] języka specyficznego dla domeny, gdy wartość właściwości domeny, `OnValueChanging()` i `OnValueChanged()` metody są wywoływane w domenie obsłudze właściwości. Aby odpowiedzieć na zmianę, można zastąpić te metody.

## <a name="override-the-property-handler-methods"></a>Przesłaniaj metody obsługi właściwości

Każda właściwość domeny języka specyficznego dla domeny jest obsługiwany przez klasę, która jest zagnieżdżona w swojej klasie nadrzędnej domeny. Jego nazwę w formacie *PropertyName*PropertyHandler. Możesz sprawdzić klasy obsługi tej właściwości w pliku **Dsl\Generated Code\DomainClasses.cs**. W klasie `OnValueChanging()` jest wywoływana bezpośrednio przed zmianami wartości i `OnValueChanged()` jest wywoływana natychmiast po zmianie wartości.

Na przykład, załóżmy, że masz klasą domeny o nazwie `Comment` mający właściwość domeny ciągu o nazwie `Text` i właściwość typu integer o nazwie `TextLengthCount`. Powoduje `TextLengthCount` zawsze ma długość `Text` ciągu, można zapisać następujący kod w osobnym pliku w projekcie Dsl:

```csharp
// Domain Class "Comment":
public partial class Comment
{
  // Domain Property "Text":
  partial class TextPropertyHandler
  {
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)
    {
      base.OnValueChanging(element, oldValue, newValue);

      // To update values outside the Store, write code here.

      // Let the transaction manager handle undo:
      Store store = element.Store;
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;

      // Update values in the Store:
      this.TextLengthCount = newValue.Length;
    }
  }
}
```

Zwróć uwagę następujące kwestie dotyczące obsługi właściwości:

-   Właściwość metody procedury obsługi są nazywane zarówno po dokonaniu zmiany do właściwości domeny i po kodzie programu przypisuje inną wartość dla właściwości.

-   Metody są wywoływane tylko wtedy, gdy wartość faktycznie zostanie zmieniona. Program obsługi nie jest wywoływana, jeśli kod programu przypisuje wartość równą bieżącej wartości.

-   Magazyn obliczeniowej i niestandardowe właściwości domeny nie mają metod OnValueChanged i OnValueChanging.

-   Za pomocą obsługi zmiany nie można zmodyfikować nowej wartości. Jeśli chcesz to zrobić, na przykład ograniczyć wartość do określonego zakresu, zdefiniuj `ChangeRule`.

-   Nie można dodać obsługi zmiany do właściwości, która reprezentuje roli relacji. Zamiast tego należy zdefiniować `AddRule` i `DeleteRule` dla klasy relacji. Te reguły są wyzwalane po utworzeniu lub zmianie łącza. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Zmiany i Magazyn

Właściwość metody procedury obsługi są nazywane wewnątrz transakcji, który zainicjował zmianę. W związku z tym można wprowadzić więcej zmiany w magazynie bez konieczności otwierania nowych transakcji. Zmiany może spowodować wywołań obsługi dodatkowych.

Gdy cofnięcie transakcji ponowione lub wycofane, nie należy podejmować zmiany w magazynie, oznacza to, zmienia się na elementy modelu, relacje, kształtów, diagramy łączników lub ich właściwości.

Ponadto należy zwykle nie zaktualizować wartości podczas ładowania modelu z pliku.

W związku z tym powinny być chronione podobnie zmiany modelu w teście następująco:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Z kolei jeśli Twoje obsługi właściwości propaguje zmiany poza Sklepem, na przykład w pliku, bazy danych lub zmienne bez magazynu, następnie należy zawsze wprowadzania tych zmian, dzięki czemu zewnętrznych wartości są aktualizowane, gdy użytkownik wywoła cofania lub wykonaj ponownie.

### <a name="cancel-a-change"></a>Anuluj zmiany

Jeśli chcesz uniemożliwić zmianę, musisz można wycofać bieżącej transakcji. Na przykład możesz chcieć upewnij się, że właściwość jest nadal w określonym zakresie.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Alternatywna metoda: obliczone właściwości

W poprzednim przykładzie przedstawiono, jak można OnValueChanged() propagację wartości z właściwości jednej domeny do innej. Każda właściwość ma własną przechowywanej wartości.

Zamiast tego rozważ zdefiniowanie jako właściwość obliczona właściwość dziedziczona. W tym przypadku właściwości ma Brak magazynu własnych i jest zdefiniowanie obliczeniu zawsze, gdy jego wartość jest wymagana. Aby uzyskać więcej informacji, zobacz [obliczona i właściwości magazynu niestandardowe](../modeling/calculated-and-custom-storage-properties.md).

Zamiast poprzedni przykład, można ustawić **rodzaj** pole `TextLengthCount` jako **obliczona** w definicji DSL. Czy podać własne **uzyskać** metody dla tej właściwości domeny. **Uzyskać** metoda zwróci Bieżąca długość `Text` ciągu.

Potencjalną wadą obliczeniowej właściwości jest jednak, że wyrażenie jest obliczane za każdym razem, gdy jest używana wartość, która może być problem z wydajnością. Ponadto istnieje nie OnValueChanging() i OnValueChanged() na obliczonej właściwości.

### <a name="alternative-technique-change-rules"></a>Alternatywna metoda: Zmień reguły

Po zdefiniowaniu ChangeRule jest wykonywany po zakończeniu transakcji, w którym wartość właściwości zostanie zmieniona.  Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

W przypadku kilku zmian w jednej transakcji, ChangeRule wykonuje po ich wszystkich. Przez kontrast, OnValue... metody są wykonywane, gdy niektóre zmiany nie została wykonana. W zależności od tego, co chcesz osiągnąć to może spowodować ChangeRule bardziej odpowiednie.

Umożliwia także ChangeRule aby dopasować nowej wartości właściwości należy do określonego zakresu.

> [!WARNING]
> Jeśli reguła dokonuje zmian w zawartości Sklepu, mogły zostać wyzwolone inne reguły i obsługi właściwości. Zmiana właściwości, która wyzwoliła go, reguła zostanie ponownie wywołany. Należy się upewnić, że do definicji reguły nie spowoduje wyzwolenie nieskończone.

```csharp
using Microsoft.VisualStudio.Modeling;
...
// Change rule on the domain class Comment:
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]
class MyCommentTrimRule : ChangeRule
{
  public override void
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)
  {
    base.ElementPropertyChanged(e);
    Comment comment = e.ModelElement as Comment;

    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))
      comment.Text = comment.Text.Trim();
    // If changed, rule will trigger again.
  }
}

// Register the rule:
public partial class MyDomainModel
{
 protected override Type[] GetCustomDomainModelTypes()
 { return new Type[] { typeof(MyCommentTrimRule) };
 }
}
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład powoduje zastąpienie obsługi właściwości z właściwością domeny i powiadamia użytkownika, gdy właściwość `ExampleElement` klasy domeny została zmieniona.

### <a name="code"></a>Kod

```csharp
using DslModeling = global::Microsoft.VisualStudio.Modeling;
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;

namespace msft.FieldChangeSample
{
  public partial class ExampleElement
  {
    internal sealed partial class NamePropertyHandler
    {
      protected override void OnValueChanged(ExampleElement element,
         string oldValue, string newValue)
      {
        if (!this.Store.InUndoRedoOrRollback)
        {
           // make in-store changes here...
        }
        // This part is called even in undo:
        System.Windows.Forms.MessageBox.Show("Value Has Changed");
        base.OnValueChanged(element, oldValue, newValue);
      }
    }
  }
}
```