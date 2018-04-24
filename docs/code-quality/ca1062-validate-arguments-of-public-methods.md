---
title: CA1062 Walidacja argumentów metod publicznych
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac6f150903c54c7bea6b5f092aa472a6b3a6e08e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062 Walidacja argumentów metod publicznych

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Widocznej zewnętrznie metodzie wyłuskań jeden z jego argumentów odniesienia bez sprawdzenia, czy ten argument jest `null` (`Nothing` w języku Visual Basic).

## <a name="rule-description"></a>Opis reguły

Wszystkie argumenty odwołania przekazane do widocznych zewnętrznie metod powinny zostać sprawdzone `null`. W razie potrzeby należy zgłosić <xref:System.ArgumentNullException> gdy argument jest `null`.

Jeśli metoda może zostać wywołana z nieznany zestawu, ponieważ jest on zadeklarowany jako public lub protected, należy sprawdzić, czy wszystkie parametry metody. Jeśli metoda jest przeznaczona do można wywołać tylko przez zestawy znane, należy wprowadzić metody wewnętrznej i zastosować <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu do zestawu zawierającego metodę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, sprawdź poprawność każdy argument odwołania, względem `null`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Ostrzeżenie od tej reguły można pominąć, jeśli masz pewność, że parametr wyłuskiwany została zweryfikowana przez inne wywołanie metody w funkcji.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono metodę, która narusza zasady i metody, która spełnia reguły.

 ```csharp
 using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Przykład

Kopiowanie konstruktorów, które wypełnić pola lub właściwości, które są obiektami odwołania również może naruszyć reguły CA1062. Naruszenie przyczyną może być skopiowany obiekt, który jest przekazywany do konstruktora kopiującego `null` (`Nothing` w języku Visual Basic). Aby rozwiązać naruszenia, użyj metody statyczne (Shared w języku Visual Basic), do sprawdzenia skopiowanego obiektu nie jest zerowa.

W następujących `Person` przykład klasy `other` obiekt, który jest przekazywany do `Person` może być Konstruktor kopiujący `null`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Przykład

W następujących zmian `Person` przykład `other` obiekt, który jest przekazywany do konstruktora kopiującego najpierw jest sprawdzany pod kątem null w `PassThroughNonNull` metody.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}

```