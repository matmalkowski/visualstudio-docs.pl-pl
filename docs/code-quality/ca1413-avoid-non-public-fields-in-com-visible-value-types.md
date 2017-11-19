---
title: "CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8dc7c435d9f853cfb67f7c45f5ec7116ff6fb8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)   
 [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)