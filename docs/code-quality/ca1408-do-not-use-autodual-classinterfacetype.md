---
title: "CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ad19c3fa245998d57542a5dfe1b9da0c61984626
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Nie używać AutoDual ClassInterfaceType
|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|Kategoria|Microsoft.Interoperability|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Składnik modelu COM (Object) typu widoczny jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> ustawić atrybutu `AutoDual` wartość <xref:System.Runtime.InteropServices.ClassInterfaceType>.  
  
## <a name="rule-description"></a>Opis reguły  
 Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie jeśli <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut nie jest określony, używany jest interfejs tylko do wysyłania.  
  
 O ile nie jest oznaczony jako inaczej, wszystkie typy nierodzajowe publiczne są widoczne dla modelu COM; wszystkie typy niepubliczne i rodzajowy nie są widoczne dla modelu COM.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, zmień wartość <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutu `None` wartość <xref:System.Runtime.InteropServices.ClassInterfaceType> i jawnie definiować interfejsu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły, jeśli nie ma pewności, czy układ typu i jego typów podstawowych nie zmieni się w przyszłych wersjach.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono klasę, która narusza regułę i ponownej deklaracji klasy, aby użyć jawnego interfejsu.  
  
 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: Oznacz interfejsy ComSource jako interfejsy IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)