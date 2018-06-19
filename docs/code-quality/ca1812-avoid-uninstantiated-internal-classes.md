---
title: 'CA1812: Unikaj wewnętrznych klas bez wystąpień'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2b59e9b0947c6d2b1cbb37cdc850a144976d495
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915600"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Unikaj wewnętrznych klas bez wystąpień
|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie.

## <a name="rule-description"></a>Opis reguły
 Ta zasada próbuje zlokalizować wywołania do jednego z konstruktorów typu i zgłasza naruszenie, jeśli połączenie nie zostanie znaleziony.

 Następujące typy nie są sprawdzane przez tę regułę:

-   Typy wartości

-   Typy abstrakcyjne

-   Wyliczenia

-   Delegaty

-   Typy tablic wysyłanego kompilatora

-   Typy, którego nie można utworzyć wystąpienia i definiującą `static` (`Shared` w języku Visual Basic) tylko metody.

 W przypadku zastosowania <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> do zestawu, który jest analizowana, ta reguła zostanie przeprowadzona na wszystkie konstruktory oznaczone jako `internal` , ponieważ nie można sprawdzić, czy pole jest używana przez inną `friend` zestawu.

 Mimo że nie można obejść to ograniczenie w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] analizy kodu zewnętrznego autonomiczna programu FxCop nastąpi na wewnętrzny konstruktorów Jeśli co `friend` zestawu znajduje się w analizy.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, Usuń typem lub Dodaj kod, który korzysta z niego. Jeśli typ zawiera tylko metody statyczne, Dodaj jedną z następujących do typu, aby zapobiec przez kompilator domyślnego konstruktora wystąpienia publicznego emitowanie:

-   Konstruktor prywatny dla typów obiektu docelowego [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] w wersjach 1.0 i 1.1.

-   `static` (`Shared` w języku Visual Basic) modyfikator typy kierowanych [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły. Firma Microsoft zaleca, aby pominąć to ostrzeżenie w następujących sytuacjach:

-   Klasa jest tworzony za pomocą odbicia z późnym wiązaniem metod takich jak <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

-   Klasa jest tworzona automatycznie przez środowisko uruchomieniowe lub [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Na przykład klasy, które implementują <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> lub <xref:System.Web.IHttpHandler?displayProperty=fullName>.

-   Klasa jest przekazywany jako parametru typu ogólnego, który ma nowego ograniczenia. Na przykład poniższy przykład zgłosi tej reguły.

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }
    // [...]
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

 W takich przypadkach zaleca się, że możesz pominąć to ostrzeżenie.

## <a name="related-rules"></a>Powiązanych reguł
 [CA1811: Unikaj niewywoływanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)