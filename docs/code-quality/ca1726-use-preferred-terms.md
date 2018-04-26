---
title: 'CA1726: Używaj preferowanych terminów'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4f83e7754bcb96de05eac3273133cabbc8b8f61
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Używaj preferowanych terminów
|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Dzielenie — po zestawów<br /><br /> Dzielenie non - po w parametrach typu|

## <a name="cause"></a>Przyczyna
 Nazwa widocznego na zewnątrz identyfikatora zawiera termin, dla którego istnieje alternatywny, preferowany zamiennik. Nazwa zawiera również termin flagi lub flagi.

## <a name="rule-description"></a>Opis reguły
 Ta zasada analizuje identyfikator na tokeny. Każdego pojedynczego token i ciągłe kombinacja podwójną tokenu jest porównywany terminów, które są wbudowane w regule i w sekcji uznane za przestarzałe żadnych niestandardowych słowników. W poniższej tabeli przedstawiono warunki, które są wbudowane w zasady i ich preferowanego alternatyw.

|Przestarzałe termin|Preferowany termin|
|-------------------|--------------------|
|nie są|AreNot|
|Anulowane|Anulowane|
|Nie można|Nie można|
|ComPlus|EnterpriseServices|
|Couldnt|CouldNot|
|Didnt|DidNot|
|Numer nie|Nie|
|Nie|Nie|
|Flaga lub flagi|Nie ma żadnego warunku zastąpienia. Nie używać.|
|nie|HadNot|
|Nie|HasNot|
|nie zostało to jeszcze|HaveNot|
|Indeksy|Indeksy|
|nie jest|IsNot|
|Logowanie|Logowanie|
|Wyloguj|Wyloguj|
|Shouldnt|ShouldNot|
|Logować|Logowanie|
|Wyrejestrowanie|Wyloguj się|
|Wasnt|WasNot|
|nie zostały|WereNot|
|Nie można|Iść|
|Wouldnt|WouldNot|
|Zapisywalne|Zapisywalny|

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zamień termin na preferowany termin alternatywny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie od tej zasady tylko wtedy, gdy nazwa identyfikatora jest zamierzone i dotyczy w szczególności pierwotny termin zamiast preferowanych terminów.

## <a name="related-rules"></a>Powiązanych reguł
 [Ostrzeżenia dotyczące nazewnictwa](../code-quality/naming-warnings.md)