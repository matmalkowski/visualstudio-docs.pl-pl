---
title: "CA1414: Oznacz logiczne argumenty P Invoke za pomocą MarshalAs | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3ce70291bd59ef3211c9fea871c8155f1a3e7fed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Oznacz logiczne argumenty P/Invoke za pomocą MarshalAs
|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|Kategoria|Microsoft.Interoperability|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Platforma wywołania metody deklaracja zawiera <xref:System.Boolean?displayProperty=fullName> lub wartość zwrotną, ale <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> atrybut nie ma zastosowania do parametrów lub wartości zwracanej.  
  
## <a name="rule-description"></a>Opis reguły  
 Platforma wywołania metody uzyskuje dostęp do niezarządzanego kodu i jest definiowana za pomocą `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Określa zachowanie marshalingu, służący do konwersji typów danych między zarządzanymi i niezarządzanymi kodu. Wiele proste typy danych, na przykład <xref:System.Byte?displayProperty=fullName> i <xref:System.Int32?displayProperty=fullName>, ma reprezentacji w postaci jednego za pomocą kodu niezarządzanego i nie wymagają specyfikacji ich zachowanie marshalingu; środowisko uruchomieniowe języka wspólnego automatycznie dostarcza poprawne zachowanie.  
  
 <xref:System.Boolean> Typ danych ma wiele oświadczeń za pomocą kodu niezarządzanego. Gdy <xref:System.Runtime.InteropServices.MarshalAsAttribute> nie zostanie określony, domyślne zachowanie dla marshalingu <xref:System.Boolean> typ danych jest <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Jest to liczba całkowita 32-bitowy, który nie jest odpowiedni we wszystkich okolicznościach. Logiczna reprezentacja, wymagany przez metodę niezarządzane powinny być określone i dopasowane do odpowiedniego <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool jest typu Win32 BOOL, który jest zawsze 4 bajty. UnmanagedType.U1 powinien być używany dla języka C++ `bool` lub inne typy 1-bajtowego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, zastosuj <xref:System.Runtime.InteropServices.MarshalAsAttribute> do <xref:System.Boolean> parametrze lub wartości zwracanej. Ustaw wartość atrybutu do odpowiedniego <xref:System.Runtime.InteropServices.UnmanagedType>.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły. Nawet jeśli domyślne zachowanie marshalingu jest odpowiednie, kod łatwiej jest zachowywany w przypadku zachowanie jest jawnie określony.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono dwie platformy wywołania metody, które są oznaczone ikoną z odpowiednią <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutów.  
  
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1901: Deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101: Należy określić marshaling dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)