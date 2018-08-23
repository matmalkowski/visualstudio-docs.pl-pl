---
title: 'CA1809: Unikaj zbyt wielu zmiennych lokalnych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e5dbd1ffc9a427994d923fda695a8dab0c37dda0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684666"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Unikaj nadmiernego używania zmiennych lokalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1809: Unikaj zbyt wielu zmiennych lokalnych](https://docs.microsoft.com/visualstudio/code-quality/ca1809-avoid-excessive-locals).  
  
Element TypeName | AvoidExcessiveLocals |  
| CheckId | CA1809 |  
| Kategoria | Microsoft.Performance|  
| Zmiana powodująca niezgodność | Bez podziału |  
  
## <a name="cause"></a>Przyczyna  
 Element członkowski zawiera więcej niż 64 zmienne lokalne, niektóre z nich mogą być generowane przez kompilator.  
  
## <a name="rule-description"></a>Opis reguły  
 Typowa Optymalizacja wydajności jest do przechowywania wartości w rejestrze procesora zamiast w pamięci, co jest nazywane *rejestrowanie* wartość. Środowisko uruchomieniowe języka wspólnego uwzględnia maksymalnie 64 zmienne lokalne dla enregistration. Zmienne, które nie są przechowywane w rejestrze procesora są umieszczane na stosie i należy przenieść do rejestru przed manipulacji. Aby zezwolić na ryzyko, wszystkie zmienne lokalne uzyskać przechowywane w rejestrze procesora, ograniczyć liczbę zmiennych lokalnych do 64.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, refaktoryzować implementacji, aby używać nie więcej niż 64 zmienne lokalne.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne, aby pominąć ostrzeżenie od tej reguły lub wyłączyć regułę, jeśli wydajność nie ma problemu.  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)



