---
title: 'CA1809: Unikaj nadmiernego używania zmiennych lokalnych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea0d1d27f583e86a62e9c0ff524d9d623253d007
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Unikaj nadmiernego używania zmiennych lokalnych
|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Element członkowski zawiera więcej niż 64 zmienne lokalne, niektóre z nich mogą być generowane przez kompilator.

## <a name="rule-description"></a>Opis reguły
 Typowe optymalizacji wydajności jest do przechowywania wartości rejestru procesora, zamiast w pamięci, co jest nazywane *rejestracja* wartość. Środowisko uruchomieniowe języka wspólnego uwzględnia maksymalnie 64 zmienne lokalne dla enregistration. Zmienne, które nie są w zarejestrowany są umieszczane na stosie i muszą zostać przeniesione do rejestru przed manipulowanie. Aby umożliwić prawdopodobieństwo że wszystkie zmienne lokalne uzyskać zarejestrowany, ograniczyć liczbę zmiennych lokalnych 64.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Refaktoryzuj implementacji, aby użyć więcej niż 64 zmienne lokalne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne, aby pominąć ostrzeżenie od tej reguły, lub można wyłączyć reguły, jeśli wydajność nie ma problemu.

## <a name="related-rules"></a>Powiązanych reguł
 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)