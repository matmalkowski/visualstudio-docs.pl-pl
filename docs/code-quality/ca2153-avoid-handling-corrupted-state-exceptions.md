---
title: 'CA2153: Unikaj Obsługa wyjątków stan uszkodzony'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 035c68feddafffbb7e1502a07db47ab80eac61c5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Unikaj Obsługa wyjątków stan uszkodzony

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

[Uszkodzony rozszerzenie stanu wyjątków (klienta)](https://msdn.microsoft.com/magazine/dd419661.aspx) wskazać, że pamięć uszkodzenie istnieje w procesie. Przechwytywanie tych zamiast zezwolenia na awarii procesu może prowadzić do luk w zabezpieczeniach, jeśli osoba atakująca może wykorzystać do obszaru uszkodzenia pamięci.

## <a name="rule-description"></a>Opis reguły
 Rozszerzenie klienta wskazuje, że stan procesu został uszkodzony i nie przechwycono przez system. W scenariuszu uszkodzony ogólne obsługi tylko przechwytuje wyjątek po zaznaczeniu metodę poprawne `HandleProcessCorruptedStateExceptions` atrybutu. Domyślnie [środowiska uruchomieniowego języka wspólnego (CLR)](/dotnet/standard/clr) nie wywoła obsługi catch w przypadku rozszerzeń klienta.

 Stosowanie się, że proces awarii bez Przechwytywanie rodzaju wyjątki jest najbezpieczniejsza opcja, jako nawet rejestrowania kodu może umożliwić atakującemu wykorzystać usterki uszkodzenie pamięci.

 To ostrzeżenie jest wyzwalane po Przechwytywanie rozszerzeń klienta z ogólny program obsługi, który przechwytuje wszystkie wyjątki, takie jak catch(exception) lub catch (Brak specyfikacji wyjątku).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać to ostrzeżenie powinien wykonaj jedną z następujących czynności:

 1. Usuń `HandleProcessCorruptedStateExceptions` atrybutu. Przywraca domyślne zachowanie środowiska uruchomieniowego, gdzie rozszerzeń klienta nie są przekazywane do obsługi catch.

 2. Usuń program obsługi catch ogólne in preference of obsługi, które Przechwytuj typów określony wyjątek.  Może to obejmować rozszerzeń klienta, przy założeniu, że kod obsługi można bezpiecznie obsługiwać je (bardzo rzadko).

 3. Ponowne generowanie rozszerzenie klienta programu obsługi catch, który zapewnia wyjątek jest przekazywany do obiektu wywołującego i spowoduje zakończenie uruchomionego procesu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod

### <a name="violation"></a>Naruszenie
 Poniższy pseudo-kod przedstawia wzorzec wykryte przez tę regułę.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Rozwiązanie 1
 Usuwanie atrybutu HandleProcessCorruptedExceptions gwarantuje, że wyjątki będą nie obsługiwane.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Rozwiązanie 2
 Usuń obsługi catch ogólne i catch tylko typów określonych wyjątków.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Rozwiązanie 3
 Ponowne zgłoszenie wyjątku.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```