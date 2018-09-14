---
title: 'CA2153: Unikaj obsługiwania uszkodzonych wyjątków stanu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5043c8cb9cefb8ffdb600083ba2dc4bb49d5e3f5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547529"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Unikaj obsługiwania uszkodzonych wyjątków stanu

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

[Uszkodzony stan wyjątków (rozszerzenie klienta)](https://msdn.microsoft.com/magazine/dd419661.aspx) wskazać, że pamięć uszkodzenie istnieje w procesie. Przechwytywanie tych zamiast zezwalać awarię procesu może prowadzić do luk w zabezpieczeniach, jeśli osoba atakująca może wykorzystać do regionu pamięci uszkodzony.

## <a name="rule-description"></a>Opis reguły

Rozszerzenie klienta wskazuje, że stan procesu został uszkodzony i nie zgłoszony przez system. W tym scenariuszu uszkodzony ogólny program obsługi tylko przechwytuje wyjątek po oznaczeniu metodę poprawne `HandleProcessCorruptedStateExceptions` atrybutu. Domyślnie [środowiska uruchomieniowego języka wspólnego (CLR)](/dotnet/standard/clr) nie wywoła obsługi catch w przypadku rozszerzeń klienta.

Zezwolenie na proces awarii bez wychwytywanie tych rodzajów wyjątków jest najbezpieczniejsza opcja, jako nawet rejestrowania kodu może umożliwić atakującemu wykorzystać błędy uszkodzenia pamięci.

To ostrzeżenie uaktywnia Przechwytywanie rozszerzeń klienta za pomocą ogólny program obsługi, który przechwytuje wszystkie wyjątki, takie jak catch(exception) ani catch (bez określenia wyjątków).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby rozwiązać tego ostrzeżenia, wykonaj jedną z następujących czynności:

- Usuń `HandleProcessCorruptedStateExceptions` atrybutu. Przywraca domyślne zachowanie środowiska uruchomieniowego, gdzie rozszerzeń klienta nie zostaną przekazane do obsługi catch.

- Usuń procedurę obsługi catch ogólne, in preference of programów obsługi, które Przechwytuj typów wyjątków określonych. Może to obejmować rozszerzeń klienta, przy założeniu, że kod procedury obsługi bezpiecznie mógł je obsłużyć (rzadkiego).

- Zgłoś ponownie rozszerzenie klienta w obsłudze catch, która zapewnia wyjątku jest przekazywany do obiektu wywołującego i spowoduje zakończenie uruchomionego procesu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod

### <a name="violation"></a>Naruszenie zasad

Poniższy pseudo-kod przedstawiono wzorzec wykryte przez tę regułę.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method to handle and log CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
    }
}
```

### <a name="solution-1"></a>Rozwiązanie 1

Usuwanie atrybutu HandleProcessCorruptedExceptions gwarantuje, że wyjątki będą nie obsługiwane.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-2"></a>Rozwiązanie 2

Usuń procedurę obsługi catch ogólne i przechwytywać tylko typy określonego wyjątku.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-3"></a>Rozwiązanie 3

Zgłoś ponownie wyjątek.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
        throw;
    }
}
```