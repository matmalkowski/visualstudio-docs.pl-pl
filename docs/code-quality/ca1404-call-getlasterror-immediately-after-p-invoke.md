---
title: "Ca1404: należy Wywołać GetLastError natychmiast po P Invoke | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 63cd84136861b80617285a5f7f03ff4767efddca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Należy wywołać GetLastError natychmiast po P/Invoke
|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|Kategoria|Microsoft.Interoperability|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Połączenie jest nawiązywane w przypadku <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> metody lub równoważne Win32 `GetLastError` funkcji i wywołanie, który pochodzi bezpośrednio przed nie jest to platforma wywołania metody.  
  
## <a name="rule-description"></a>Opis reguły  
 Platforma wywołania metody uzyskuje dostęp do niezarządzanego kodu i jest definiowana za pomocą `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybutu. Ogólnie rzecz biorąc, w przypadku awarii niezarządzanych funkcji wywołania Win32 `SetLastError` funkcji, aby ustawić kod błędu, który jest skojarzony z błędem. Element wywołujący funkcji zakończonych niepowodzeniem wywołania Win32 `GetLastError` funkcji, aby pobrać kod błędu i ustalić przyczynę niepowodzenia. Kod błędu jest przechowywany w zasadzie na wątek i jest zastępowany przy następnym wywołaniu `SetLastError`. Po wywołaniu platformy nie powiodło się wywołanie metody, przez wywołanie kodu zarządzanego można pobrać kod błędu: <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> metody. Ponieważ kod błędu mogą zostać zastąpione przez wywołania wewnętrznego z innych metod biblioteki zarządzanej klasy `GetLastError` lub <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> metoda powinna być wywoływana natychmiast po wywołania metody invoke platformy.  
  
 Reguła ignoruje wywołania dla następujących członków zarządzanych wystąpieniu między wywołanie platformy wywołania metody i wywołania w celu <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Elementy te nie należy zmieniać błąd kodu i są przydatne do określenia Powodzenie niektóre platformy wywołania metody invoke.  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Przenieś wywołanie <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> tak, aby natychmiast następującej po wywołaniu platformy wywołania metody.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Bezpiecznie pominąć ostrzeżenie od tej reguły, jeśli wywołanie metody invoke kodu od platformy i <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> wywołanie metody nie można jawnie lub niejawnie spowodować kod błędu zmienić.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metodę, która narusza zasady i metody, która spełnia reguły.  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1060: Przenieś P/Invokes do klasy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: Powinny istnieć punkty wejścia P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P/Invoke nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101: Należy określić marshaling dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205: Użyj zarządzanych odpowiedników funkcji Win32 API](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)