---
title: 'CA1064: Wyjątki powinny być publiczne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b60127eee3ea333e324c656961eaf383a6ef409f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Wyjątki powinny być publiczne
|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wyjątek niepublicznych pochodzi bezpośrednio z <xref:System.Exception>, <xref:System.SystemException>, lub <xref:System.ApplicationException>.

## <a name="rule-description"></a>Opis reguły
 Wystąpił wyjątek wewnętrzny jest widoczna tylko wewnątrz własnego wewnętrznego zakresu. W przypadku wystąpienia wyjątku poza zakresem wewnętrznym tylko wyjątek podstawowy może zostać użyty do jego przechwycenia. Jeśli wewnętrzny wyjątek pochodzi z <xref:System.Exception>, <xref:System.SystemException>, lub <xref:System.ApplicationException>, kod zewnętrzny nie ma wystarczającej ilości informacji, aby dowiedzieć się, co należy zrobić z wyjątkiem.

 Jednak jeśli kod ma publiczny wyjątek, który później jest używana jako podstawa dla wewnętrznego wyjątku, jest uzasadnione przyjęto założenie, że kodu limit będą mogli czymś inteligentnego z wyjątkiem podstawowej. Publiczny wyjątek będzie zawierać więcej informacji niż dostarczanych przez <xref:System.Exception>, <xref:System.SystemException>, lub <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Udostępnić wyjątek lub pochodzi z wewnętrznego wyjątku z publicznego wyjątek, który nie jest <xref:System.Exception>, <xref:System.SystemException>, lub <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń komunikat od tej reguły, gdy we wszystkich przypadkach, że prywatnej wyjątek zostanie przechwycony wewnętrzny zakres.

## <a name="example"></a>Przykład
 Na przykład metody pierwszy, FirstCustomException generowane tej reguły, ponieważ klasa wyjątków pochodzi bezpośrednio z wyjątków i wewnętrzny. Reguła nie zostanie wywołane w klasie SecondCustomException, ponieważ mimo że klasa również pochodzi bezpośrednio z wyjątków, klasa jest zadeklarowany jako publiczny. Klasa innych również nie uruchomi reguły, ponieważ nie pochodzi bezpośrednio z <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, lub <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
