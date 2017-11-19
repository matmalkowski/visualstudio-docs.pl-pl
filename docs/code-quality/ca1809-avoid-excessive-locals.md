---
title: 'CA1809: Unikaj nadmiernego zmienne lokalne | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0a96616d1ee0f7c63e8f36f56a18f234fa27a173
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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