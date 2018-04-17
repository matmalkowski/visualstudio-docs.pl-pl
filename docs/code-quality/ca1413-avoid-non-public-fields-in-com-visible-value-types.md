---
title: 'CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e68f29fed3a1f25eb2a80b1b6acf09827e8ee18f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Unikaj pól niepublicznych w typach wartościowych widocznych dla modelu COM
|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|Kategoria|Microsoft.Interoperability|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typ wartości, w szczególności oznaczony jako widoczna do składnika modelu COM (Object) deklaruje on pole niepubliczne wystąpienia.  
  
## <a name="rule-description"></a>Opis reguły  
 Pola niepubliczne wystąpień typów wartości widocznych dla modelu COM są widoczne dla klientów COM. Przejrzyj zawartość pola informacji, które nie powinny zostać ujawnione lub będą mieć efektu niezamierzone projekt lub zabezpieczeń.  
  
 Domyślnie wszystkie typy publiczne wartości są widoczne dla modelu COM. Aby ograniczyć liczbę fałszywych alarmów, ta zasada wymaga widoczność modelu COM typu, który ma być jasno określone. Muszą być oznaczone zestawu zawierającego <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ustawioną `false` i typ musi być oznaczone <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną `true`.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły i zachować pola ukryte, Zmień typ wartości na typ referencyjny lub usuń <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybutu typu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, jeśli ujawnienia pola jest dopuszczalna.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza zasady.  
  
 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1407: Unikaj składowych statycznych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)   
 [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)