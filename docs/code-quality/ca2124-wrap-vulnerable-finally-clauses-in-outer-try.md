---
title: 'CA2124: Kodowanie wrażliwych klauzul finally w zewnętrznym try'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d46bc7bcfa8c1918091fabbbd759172259ea9ba6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Kodowanie wrażliwych klauzul finally w zewnętrznym try
|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 W wersjach 1.0 i 1.1 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], zawiera metodę publiczną lub chronioną `try` / `catch` / `finally` bloku. `finally` Blok pojawia się Resetowanie stanu zabezpieczeń i nie jest ujęta w `finally` bloku.

## <a name="rule-description"></a>Opis reguły
 Ta zasada lokalizuje `try` / `finally` bloki w kodzie, przeznaczonego dla wersji 1.0, 1.1 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] co może być narażony na filtry wyjątków złośliwego obecne w stosie wywołań. Jeśli poufnych operacje takie jak personifikacji są wykonywane w bloku try, a jest zgłaszany wyjątek, filtr może zostać uruchomiony przed `finally` bloku. Na przykład personifikacji oznacza to, że filtr jest wykonywany jak nazwa personifikowanego użytkownika. Filtry są obecnie implementable tylko w języku Visual Basic.

> [!WARNING]
>  **Uwaga** w wersji 2.0 lub nowszej [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], środowisko uruchomieniowe automatycznie chroni `try` / `catch` /  `finally` blokować z filtry wyjątków złośliwe, jeśli występuje resetowania bezpośrednio w metodzie zawierający bloku wyjątków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Umieść odkodowany `try` / `finally` w zewnętrzny blok try. Zobacz drugi przykład poniżej. Dzięki temu `finally` do uruchomienia przed kod filtru.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod

### <a name="description"></a>Opis
 Poniższy pseudo-kod przedstawia wzorzec wykryte przez tę regułę.

### <a name="code"></a>Kod

```
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

## <a name="example"></a>Przykład
 Poniższy pseudo-kod przedstawia wzorzec, w której można zabezpieczyć kod i spełniają tej reguły.

```
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```