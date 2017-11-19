---
title: "CA2200: Rethrow, aby zachować szczegóły stosu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca2e6e61b88d4d8aaccd4784e1b521e0cbb48bd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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