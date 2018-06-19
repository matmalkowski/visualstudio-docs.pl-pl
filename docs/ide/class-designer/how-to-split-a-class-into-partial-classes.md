---
title: 'Porady: podział klas na klasy częściowe (Projektant klas)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: da7a14d781f4af79d6d1d68141c3d5de1c08d304
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957830"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Porady: podział klas na klasy częściowe w Projektancie klas

Można użyć `partial` — słowo kluczowe (`Partial` w języku Visual Basic) do dzielenia deklaracji klasy lub struktury między kilka deklaracji. Możesz użyć dowolnej liczby częściowe deklaracje.

Deklaracje można w jednym lub wielu plików źródłowych. Wszystkie deklaracje muszą być w tym samym zestawie i tego samego obszaru nazw.

Klasy częściowe są przydatne w kilku sytuacjach. Na dużego projektu na przykład rozdzielić wiele plików klasy umożliwia więcej niż jeden programisty do pracy nad projektem w tym samym czasie. Podczas pracy z kodem, który generuje Visual Studio, można zmienić klasy bez konieczności ponownego tworzenia pliku źródłowego. (Przykłady kodu, który generuje Visual Studio obejmuje kod otoki formularzy systemu Windows i usługi sieci Web). W związku z tym można tworzyć kod, który używa automatycznie generowanej klasy bez konieczności modyfikowania pliku, który tworzy Visual Studio.

Istnieją dwa rodzaje metod częściowych. W języku C# są one nazywane deklarowanie i wdrażanie; w języku Visual Basic są one nazywane deklaracji i implementacji.

**Projektant klas** obsługuje klasy częściowe i metody. Typ kształtu na diagramie klas odwołuje się do lokalizacji Pojedyncza deklaracja klasy częściowej. Jeśli częściowej klasy jest zdefiniowany w wielu plikach, można określić, które lokalizacji deklaracji **Projektant klas** użyje przez ustawienie **nowej lokalizacji elementu członkowskiego** właściwości w **właściwości**  okna. Oznacza to, kliknij dwukrotnie kształt klasy **Projektant klas** zbliża się do pliku źródłowego, który zawiera deklarację klasy oznaczona **nowej lokalizacji elementu członkowskiego** właściwości. Po dwukrotnym kliknięciu metody częściowej w kształcie klasy **Projektant klas** przechodzi do deklaracji metody częściowej. W przypadku **właściwości** okna, **nazwę pliku** właściwość odwołuje się do lokalizacji deklaracji. Dla klas częściowych **nazwę pliku** zawiera listę wszystkich plików, które zawierają kod deklaracji i implementacji dla tej klasy. Niemniej jednak w przypadku metody częściowe **nazwę pliku** listę plików, który zawiera deklaracji metody częściowej.

Poniższe przykłady dzielenie definicji klasy `Employee` do dwóch deklaracji, z których każdy definiuje innej procedury. Dwie definicje częściowe w przykładach można w jednym pliku źródłowym lub w dwóch plikach innego źródła.

> [!NOTE]
> Visual Basic używa definicje klas częściowego do oddzielania Visual Studio — wygenerowanego kodu z kodu utworzonymi przez użytkownika. Kod jest podzielone na osobne źródłowe pliki. Na przykład **projektanta formularzy systemu Windows** definiuje częściowej klasy formantów, takich jak `Form`. Wygenerowany kod w tych kontrolek nie należy modyfikować.

Aby uzyskać więcej informacji na temat typów częściowych w języku Visual Basic, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Przykład

Aby podzielić definicję klasy, należy użyć `partial` — słowo kluczowe (`Partial` w języku Visual Basic), jak pokazano w poniższym przykładzie:

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="see-also"></a>Zobacz także

- [Klasy częściowe i metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [Partial (typ) (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/partial-type)
- [Partial — metoda () (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)