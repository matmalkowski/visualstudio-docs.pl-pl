---
title: "CA2118: Przegląd wykorzystania SuppressUnmanagedCodeSecurityAttribute | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a6c5e60ed84a79e6e81d4cd066d75b1270bdb71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: Przegląd wykorzystania SuppressUnmanagedCodeSecurityAttribute
|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Publiczne lub chronione typ lub element członkowski ma <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> atrybutu.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>Zmienia domyślne zachowanie systemu zabezpieczeń dla członków, których wykonanie kodu niezarządzanego, przy użyciu wywołania COM interop lub platformy. Ogólnie rzecz biorąc, system sprawia, że [dane i modelowanie](/dotnet/framework/data/index) dla uprawnień kodu niezarządzanego. To żądanie występuje w czasie wykonywania dla każdego wywołania elementu członkowskiego i sprawdza co wywołującego w stosie wywołań uprawnień. Gdy obecny jest atrybut zapewnia system [Linkdemand](/dotnet/framework/misc/link-demands) uprawnienia: uprawnienia bezpośredniego obiektu wywołującego są zaznaczone, gdy obiekt wywołujący jest kompilacji JIT.  
  
 Atrybut ten jest używany głównie w celu zwiększenia wydajności; jednak wzrost wydajności powoduje znaczące zagrożenia dla bezpieczeństwa. Jeśli umieścisz atrybutu na publiczne elementy członkowskie, które wywołują metod natywnych wywołań w stosie wywołań (inne niż bezpośredniego obiektu wywołującego) nie ma potrzeby kodu niezarządzanego uprawnienia do wykonywania kodu niezarządzanego. W zależności od publicznego elementu członkowskiego działania i obsługi danych wejściowych może mieć niezaufanym wywołań funkcji dostępu zazwyczaj ograniczone do zaufanego kodu.  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Zależy od kontroli zabezpieczeń, aby uniemożliwić obiekty wywołujące bezpośredni dostęp do przestrzeni adresowej bieżącego procesu. Omija normalne zabezpieczeń, ten atrybut kod stanowi poważne zagrożenie, jeśli może być używany do odczytu lub zapisu w pamięci procesu. Należy pamiętać, że ryzyko nie jest ograniczona do metody celowo zapewniające dostęp do pamięci; procesu również znajduje się w żadnym scenariuszu, gdzie złośliwego kodu można uzyskać dostępu w dowolny sposób na przykład, dostarczając danych wejściowych zaskakująco, źle sformułowany lub nieprawidłowy.  
  
 Domyślnych zasad zabezpieczeń nie powoduje przyznania uprawnień kodu niezarządzanego do zestawu, o ile jest wykonywane z komputera lokalnego lub nie jest członkiem jednej z następujących grup:  
  
-   Grupa kodów strefy Mój komputer  
  
-   Grupa kodów nazwy silnej firmy Microsoft  
  
-   Grupa kodów nazwy silnej ECMA  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Uważnie przejrzyj swój kod, aby upewnić się, że ten atrybut jest bezwzględnie konieczne. Jeśli masz doświadczenia w pracy z kodu zarządzanego zabezpieczeń lub nie rozumiesz konsekwencje zabezpieczeń przy użyciu tego atrybutu, należy go usunąć z kodu. Jeśli ten atrybut jest wymagany, należy się upewnić, że obiekty wywołujące nie mogą używać złośliwy kod. Jeśli w kodzie nie ma uprawnienia do wykonywania kodu niezarządzanego, ten atrybut nie ma wpływu i powinna zostać usunięta.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Aby bezpiecznie pominąć ostrzeżenie od tej reguły, pamiętaj, że kodu nie zawiera obiektów wywołujących dostępu do natywnych operacji lub zasobów, które mogą być używane w szkodliwy sposób.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład naruszają tę regułę.  
  
 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `DoWork` metody udostępnia ścieżkę publicznie kod do metody wywołania platformy `FormatHardDisk`.  
  
 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie metoda publiczna `DoDangerousThing` powoduje naruszenie. Aby rozwiązać naruszenie, `DoDangerousThing` należy prywatnej, a dostęp do niego powinna być za pośrednictwem publicznej metody zabezpieczone przez żądanie zabezpieczeń, jak pokazano `DoWork` — metoda.  
  
 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)   
 [Dane i modelowanie](/dotnet/framework/data/index)  
 [Żądania łączy](/dotnet/framework/misc/link-demands)  
  