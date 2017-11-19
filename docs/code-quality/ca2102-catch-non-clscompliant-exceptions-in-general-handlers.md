---
title: "CA2102: Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords: CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a27054ef8732b96d5d71cbc22d567f4509877886
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Przechwytuj wyjątki inne niż CLSCompliant w ogólnej obsłudze wyjątków
|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Element członkowski zestawu, który nie jest oznaczony atrybutem <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> lub jest oznaczone jako `RuntimeCompatibility(WrapNonExceptionThrows = false)` zawiera blok catch, która obsługuje <xref:System.Exception?displayProperty=fullName> i nie zawiera bezpośrednio po bloku catch ogólne. Ta zasada powoduje ignorowanie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zestawów.  
  
## <a name="rule-description"></a>Opis reguły  
 Blok catch, która obsługuje <xref:System.Exception> przechwytuje wszystkie wyjątki zgodne specyfikacja języka wspólnego (CLS). Jednak nie przechwytuje wyjątków zgodne niezgodny ze specyfikacją CLS. CLS nie może zostać wygenerowany wyjątki zgodne z kodu natywnego lub zarządzanego kodu, który został wygenerowany przez Microsoft pośredniego (MSIL) języka asemblera. Zwróć uwagę, że C# i [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatory nie zezwalaj na niezgodny ze specyfikacją CLS wyjątki zgodne, zostanie wygenerowany i [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nie przechwytuje wyjątków zgodne niezgodny ze specyfikacją CLS. Jeśli celem użycia bloku catch można obsłużyć wszystkie wyjątki, należy użyć następującej składni bloku catch ogólne.  
  
-   C#:`catch {}`  
  
-   C++: `catch(...) {}` lub`catch(Object^) {}`  
  
 Nieobsługiwany system inny niż — wyjątek niezgodny z CLS staje się problem z zabezpieczeniami, usunięcie wcześniej dozwolone uprawnienia w bloku catch. Ponieważ wyjątki zgodne niezgodny ze specyfikacją CLS nie są przechwytywane, złośliwy metodę, która zgłasza wyjątek zgodne z systemem innym niż CLS można uruchomić z podwyższonym poziomem uprawnień.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, jeśli celem jest przechwytywać wszystkie wyjątki, Zastąp lub Dodaj blok catch ogólne lub Oznacz zestaw `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Jeśli uprawnienia zostaną usunięte w bloku catch, zduplikowany funkcji w ogólne blok catch. Jeśli nie jest celem obsłużyć wszystkie wyjątki, Zastąp bloku catch, która obsługuje <xref:System.Exception> z bloków catch obsługi typów określonych wyjątków.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli blok try nie zawiera żadnych instrukcji, które mogą generować wyjątek niezgodny ze specyfikacją CLS. Ponieważ żadnego kodu natywnego lub zarządzanego może zgłosić wyjątek z systemem innym niż CLS, wymaga wiedzy całego kodu, który może zostać wykonany w wszystkie ścieżki kodu wewnątrz bloku try. Należy zauważyć, że wyjątki zgodne niezgodny ze specyfikacją CLS nie są zgłaszane przez środowisko uruchomieniowe języka wspólnego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono klasę MSIL, która zgłasza wyjątek niezgodny ze specyfikacją CLS.  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metodę, która zawiera blok catch ogólne spełniająca reguły.  
  
 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Skompiluj następujący poprzednich przykładach.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1031: Nie Przechwytuj wyjątków typów ogólnych](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wyjątki i obsługa wyjątków](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe (asembler IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)   
 [Zastępowanie kontroli zabezpieczeń](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Niezależność od języka i elementy niezależne od języka](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)