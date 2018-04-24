---
title: 'DA0007: Unikaj używania wyjątków do przepływu sterowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c70ddc12b2c790a360f5124e7deeb8e99189742c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Unikaj używania wyjątków do przepływu sterowania
|||  
|-|-|  
|Identyfikator reguły|DA0007|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Wszystkie|  
|Komunikat|Stale jest zgłaszana wysoka liczba wyjątków. Rozważ ograniczenie użycia wyjątków w logice programu.|  
|Typ komunikatu|Ostrzeżenie|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 25 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Wysoki współczynnik programów obsługi wyjątków .NET Framework zostały wywołane w danych profilowania. Należy rozważyć użycie innych logika przepływu sterowania, aby zmniejszyć liczbę wyjątków, które są generowane.  
  
## <a name="rule-description"></a>Opis reguły  
 Korzystanie z obsługi wyjątków, aby wykryć błędów oraz inne zdarzenia, które zakłócać działanie programu jest dobrym rozwiązaniem, korzystanie z obsługi wyjątków jako część logiki wykonywania regularnych program może być kosztowne i należy unikać. W większości przypadków wyjątki powinny można użyć tylko w przypadku okoliczności, które są rzadko i nie powinny... Wyjątki nie powinny umożliwia zwracanie wartości jako część przepływu typowego programu. W wielu przypadkach można uniknąć występowanie wyjątków sprawdzania poprawności wartości i używając logikę warunkową wstrzymania wykonywania instrukcji, które powodują problemu.  
  
 Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami](http://go.microsoft.com/fwlink/?LinkID=177825) sekcji **rozdział 5 — poprawę wydajności kodu zarządzanego** w **poprawy wydajności aplikacji .NET i skalowalności** woluminu **Microsoft Patterns and Practices** biblioteki w witrynie MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do widoku znaczniki. Znajdź kolumnę, która zawiera **wyjątki środowiska CLR platformy .NET (@ProcessInstance)\\liczba wyrzuconych / sekundę** pomiarów. Określa, czy określone fazy wykonywania programu obsługi wyjątków w przypadku częściej niż innych. Przy użyciu profil próbkowania, spróbuj zidentyfikować Instrukcje throw i bloki generujących częste wyjątków try/catch. W razie potrzeby dodaj logikę bloki ułatwią zrozumienie wyjątki, które są najczęściej obsługiwane catch. Jeśli to możliwe, instrukcje throw Zamień często wykonywane lub bloki catch z przepływem proste kontrolować kod logiki lub sprawdzania poprawności.  
  
 Na przykład w gdyby okazać, że aplikacja została obsługa częste wyjątków dividebyzeroexception —, dodanie logiki do programu, aby wyszukać mianownikach z wartościami zerowymi poprawi wydajność aplikacji.