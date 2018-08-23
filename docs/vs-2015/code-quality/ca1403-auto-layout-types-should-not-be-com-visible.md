---
title: 'CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM | Dokumentacja firmy Microsoft'
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
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b3d84ec8e8ff9c8771bf18e6d4a05462d760d88c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679542"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1403: typy automatycznego układu nie powinny być widoczne dla modelu COM](https://docs.microsoft.com/visualstudio/code-quality/ca1403-auto-layout-types-should-not-be-com-visible).  
  
Element TypeName | AutoLayoutTypesShouldNotBeComVisible |  
| CheckId | CA1403 |  
| Kategoria | Microsoft.Interoperability|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Typ wartości widocznych Component Object Model (COM) jest oznaczony za pomocą <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> ustawioną wartość atrybutu <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.Runtime.InteropServices.LayoutKind> typy układu są zarządzane przez środowisko uruchomieniowe języka wspólnego. Układ tych typów może się zmieniać między wersjami programu .NET Framework, które spowodują przerwanie klientów COM, które oczekują określonego układu. Należy pamiętać, że jeśli <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut nie jest określony, C#, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], a następnie określ Kompilatory języka C++ <xref:System.Runtime.InteropServices.LayoutKind> układu dla typów wartości.  
  
 O ile nie jest oznaczony jako inaczej, wszystkie typy nierodzajowymi publiczne są widoczne dla modelu COM; wszystkie typy niepublicznych i ogólny są niewidoczne dla modelu COM. Aby zmniejszyć liczbę fałszywych alarmów, ta reguła wymaga jednak widoczność COM typu, który ma być jawnie określony; muszą być oznaczone zawierające zestaw <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> równa `false` i typ musi być oznaczony przez <xref:System.Runtime.InteropServices.ComVisibleAttribute> równa `true`.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, należy zmienić wartość <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu <xref:System.Runtime.InteropServices.LayoutKind> lub <xref:System.Runtime.InteropServices.LayoutKind>, lub ukrywanie typu modelu COM.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, typ, który narusza regułę i typ, który spełnia reguły.  
  
 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1408: Nie używaj wartości ClassInterfaceType dla elementu AutoDual](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie interfejsu klasy](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Kwalifikowanie typów .NET do międzyoperacyjności](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)   
 [Współdziałanie z kodem niezarządzanym](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



