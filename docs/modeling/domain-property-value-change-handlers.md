---
title: "Obsługa zmiany wartości właściwości domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, overriding event handlers
ms.assetid: 96d8f392-045e-4bc5-b165-fbaa470a3e16
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: effe18c4b4d363bd7fa4cbed29ddf254c85aac31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="domain-property-value-change-handlers"></a>Obsługa zmian wartości właściwości domeny
W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] języka specyficznego dla domeny, gdy wartość właściwości domeny, `OnValueChanging()` i `OnValueChanged()` metody są wywoływane w domenie obsłudze właściwości. Aby odpowiedzieć na zmianę, można zastąpić te metody.  
  
## <a name="overriding-the-property-handler-methods"></a>Zastępowanie metod obsługi właściwości  
 Każda właściwość domeny języka specyficznego dla domeny jest obsługiwany przez klasę, która jest zagnieżdżona w swojej klasie nadrzędnej domeny. Jego nazwę w formacie *PropertyName*PropertyHandler. Możesz sprawdzić klasy obsługi tej właściwości w pliku **Dsl\Generated Code\DomainClasses.cs**. W klasie `OnValueChanging()` jest wywoływana bezpośrednio przed zmianami wartości i `OnValueChanged()` jest wywoływana natychmiast po zmianie wartości.  
  
 Na przykład, załóżmy, że masz klasą domeny o nazwie `Comment` mający właściwość domeny ciągu o nazwie `Text` i właściwość typu integer o nazwie `TextLengthCount`. Powoduje `TextLengthCount` zawsze ma długość `Text` ciągu, można zapisać następujący kod w osobnym pliku w projekcie Dsl:  
  
```  
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
  
```  
if (!store.InUndoRedoOrRollback   
         && !store. InSerializationTransaction)  
{ this.TextLength = ...; // in-store changes   
}  
```  
  
 Z kolei jeśli Twoje obsługi właściwości propaguje zmiany poza Sklepem, na przykład w pliku, bazy danych lub zmienne bez magazynu, następnie należy zawsze wprowadzania tych zmian, dzięki czemu zewnętrznych wartości są aktualizowane, gdy użytkownik wywoła cofania lub wykonaj ponownie.  
  
### <a name="canceling-a-change"></a>Anuluje zmiany  
 Jeśli chcesz uniemożliwić zmianę, musisz można wycofać bieżącej transakcji. Na przykład możesz chcieć upewnij się, że właściwość jest nadal w określonym zakresie.  
  
```  
if (newValue > 10)   
{ store.TransactionManager.CurrentTransaction.Rollback();  
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
>  Jeśli reguła dokonuje zmian w zawartości Sklepu, mogły zostać wyzwolone inne reguły i obsługi właściwości. Zmiana właściwości, która wyzwoliła go, reguła zostanie ponownie wywołany. Należy się upewnić, że do definicji reguły nie spowoduje wyzwolenie nieskończone.  
  
```  
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
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanged%2A>   
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanging%2A>