---
title: 'Porady: podział klas na klasy częściowe (Projektant klas) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 672f0c5a6170b169e9fcfff6332724e2e1bff62f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Porady: podział klas na klasy częściowe (Projektant klas)
Deklaracja klasy lub struktury między kilka deklaracji można podzielić przy użyciu `Partial` słów kluczowych w języku Visual Basic lub `partial` — słowo kluczowe języka C#. Możesz użyć dowolnej liczby częściowe deklaracje ma dowolną liczbę plików innego źródła można dowolnie lub jeden plik źródłowy. Jednak wszystkie deklaracje muszą być w tym samym zestawie i tego samego obszaru nazw.  
  
Klasy częściowe są przydatne w kilku sytuacjach. Na przykład podczas pracy w przypadku dużych projektów rozdzielić klasy więcej niż jeden plik umożliwia więcej niż jeden programisty pracę, w tym samym czasie. Podczas pracy z kodem, który generuje Visual Studio, można zmienić klasy bez konieczności ponownego tworzenia pliku źródłowego. (Przykłady kodu, który generuje Visual Studio obejmuje kod otoki formularzy systemu Windows i usługi sieci Web). W związku z tym można tworzyć kod, który używa automatycznie generowanej klasy bez konieczności modyfikowania pliku, który tworzy Visual Studio.  
  
Istnieją dwa rodzaje metod częściowych. W języku C# są one nazywane deklarowanie i wdrażanie; w języku Visual Basic są one nazywane deklaracji i implementacji.  
  
Projektant klas obsługuje klasy częściowe i metody. Typ kształtu na diagramie klas odwołuje się do lokalizacji Pojedyncza deklaracja klasy częściowej. Jeśli częściowej klasy jest zdefiniowany w wielu plikach, można określić lokalizację deklaracji, których projektant klas użyje przez ustawienie **nowej lokalizacji elementu członkowskiego** właściwości w **właściwości** okna. Oznacza to, po dwukrotnym kliknięciu kształtu Klasa przechodzi Projektant klas do pliku źródłowego, który zawiera deklarację klasy oznaczona **nowej lokalizacji elementu członkowskiego** właściwości. Po dwukrotnym kliknięciu metody częściowej w kształcie klasy projektanta klas prowadzi do deklaracji metody częściowej. W przypadku **właściwości** okna, **nazwę pliku** właściwość odwołuje się do lokalizacji deklaracji. Dla klas częściowych **nazwę pliku** zawiera listę wszystkich plików, które zawierają kod deklaracji i implementacji dla tej klasy. Niemniej jednak w przypadku metody częściowe **nazwę pliku** listę plików, który zawiera deklaracji metody częściowej.  
  
Poniższe przykłady dzielenie definicji klasy `Employee` do dwóch deklaracji, z których każdy definiuje innej procedury. Dwie definicje częściowe w przykładach można w jednym pliku źródłowym lub w dwóch plikach innego źródła.  
  
> [!NOTE]
>  Visual Basic używa definicje klas częściowego do oddzielania Visual Studio — wygenerowanego kodu z kodu utworzonymi przez użytkownika. Kod jest podzielone na osobne źródłowe pliki. Na przykład **projektanta formularzy systemu Windows** definiuje częściowej klasy formantów, takich jak `Form`. Wygenerowany kod w tych kontrolek nie należy modyfikować.  
  
Aby uzyskać więcej informacji na temat typów częściowych w języku Visual Basic, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## <a name="example"></a>Przykład  
Aby podzielić definicję klasy w Visual Basic, należy użyć `Partial` — słowo kluczowe, jak pokazano w poniższym przykładzie.  
  
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

## <a name="example"></a>Przykład  
Aby podzielić definicję klasy w języku C#, użyj `partial` — słowo kluczowe, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz także
[Klasy częściowe i metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
[Partial (typ)](/dotnet/csharp/language-reference/keywords/partial-type)   
[Partial — metoda () (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/partial-method)   
[Partial](/dotnet/visual-basic/language-reference/modifiers/partial)