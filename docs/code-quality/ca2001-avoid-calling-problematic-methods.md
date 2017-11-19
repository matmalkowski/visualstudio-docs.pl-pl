---
title: "CA2001: Unikaj wywoływania problematycznych metod | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ca28bc1fd6a76262b47800dcca466e8843d3271
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Unikaj wywoływania problematycznych metod
|||  
|-|-|  
|TypeName|AvoidCallingProblematicMethods|  
|CheckId|CA2001|  
|Kategoria|Microsoft.Reliability|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Element członkowski wywołuje potencjalnie niebezpieczną lub problematyczną metodę.  
  
## <a name="rule-description"></a>Opis reguły  
 Unikaj niepotrzebnych i potencjalnie niebezpiecznych wywołań.  
  
 Naruszenie tej reguły występuje, gdy element członkowski wymaga jednej z poniższych metod.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Wywoływanie GC. Zbierz może znacznie wpłynąć na wydajność aplikacji i jest rzadko niezbędne. Aby uzyskać więcej informacji, zobacz [Rico Mariani wydajności informacje o technologii](http://go.microsoft.com/fwlink/?LinkId=169256) wpis w blogu w witrynie MSDN.|  
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend i funkcji Thread.Resume są przestarzałe z powodu ich nieprzewidywalne zachowanie.  Korzystanie z innych klas w <xref:System.Threading> przestrzeni nazw, takich jak <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, <xref:System.Threading.Mutex>, i <xref:System.Threading.Semaphore> Aby zsynchronizować wątków lub ochrony zasobów.|  
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Metoda metody DangerousGetHandle stanowi zagrożenie bezpieczeństwa, ponieważ może on zwrócić uchwytu jest nieprawidłowy. Zobacz <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> i <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> metody, aby uzyskać więcej informacji o tym, jak bezpiecznie przy użyciu metody DangerousGetHandle metody.|  
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Te metody mogą ładować zestawów z nieoczekiwanych lokalizacjach. Na przykład, zobacz wpisach w blogu .NET CLR uwagi Suzanne Cooka [funkcję LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) i [Wybieranie kontekst powiązania](http://go.microsoft.com/fwlink/?LinkId=164451) informacji o metodach ładowanie zestawów w witrynie MSDN w sieci Web.|  
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|Do czasu zaczyna się kod użytkownika wykonywanych w procesie zarządzanych jest za późno niezawodnie wywołać CoSetProxyBlanket. Środowisko uruchomieniowe języka wspólnego (CLR) ma inicjowania akcje, które mogą uniemożliwiać pomyślne użytkowników P/Invoke.<br /><br /> Jeśli masz wywołania CoSetProxyBlanket dla aplikacji zarządzanej, zaleca się uruchomić proces, za pomocą pliku wykonywalnego kodu natywnego (C++), wywołania CoSetProxyBlanket w kodzie natywnym, a następnie uruchom aplikację kodu zarządzanego w procesie. (Należy określić numer wersji środowiska uruchomieniowego.)|  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, usuń lub Zastąp wywołanie metody niebezpiecznych lub powodować problemy.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Komunikaty z tej reguły ma pomijać tylko, jeśli nie alternatywne metody problemy nie są dostępne.  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenia niezawodności](../code-quality/reliability-warnings.md)