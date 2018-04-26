---
title: 'CA2200: Należy zgłosić ponownie, aby zachować szczegóły stosu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 688c10802b144c619b22b06309cec6dee5efc52e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Należy zgłosić ponownie, aby zachować szczegóły stosu
|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wyjątek zgłoszony ponownie i wyjątek jest jawnie określonych w `throw` instrukcji.

## <a name="rule-description"></a>Opis reguły
 Wyjątek część informacji, który prowadzi po ślad stosu. Ślad stosu znajduje się lista hierarchii wywołania metody, który rozpoczyna się od metody, która zgłasza wyjątek i kończy metodę, która przechwytuje wyjątek. Jeśli jest zwracany wyjątek, ponownie, określając wyjątek w `throw` instrukcji, ślad stosu jest uruchamiany ponownie bieżącej metody i listę wywołań metody między oryginalnej metody, która zgłosiła wyjątek, a bieżąca metoda zostanie utracony. Aby zachować oryginalne informacje śledzenia stosu wyjątku, użyj `throw` instrukcji bez określenia wyjątku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, ponowne generowanie wyjątek bez jawne określenie wyjątek.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metodę, `CatchAndRethrowExplicitly`, który narusza regułę, a także metodę `CatchAndRethrowImplicitly`, które spełniają reguły.

 [!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]