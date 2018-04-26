---
title: 'CA1304: Określ CultureInfo'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64bbe0d710b720eab7a6fbb90d5dff67ae5cbb0d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Określ CultureInfo
|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metody lub konstruktora wywołuje element członkowski, który ma przeciążenia, które akceptuje <xref:System.Globalization.CultureInfo?displayProperty=fullName> parametru i metody lub konstruktora nie mogą wywoływać przeciążenia, które przyjmuje <xref:System.Globalization.CultureInfo> parametru. Ta zasada powoduje ignorowanie wywołania do następujących metod:

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 Gdy <xref:System.Globalization.CultureInfo> lub <xref:System.IFormatProvider?displayProperty=fullName> obiektu nie jest podany, wartością domyślną, która jest dostarczana przez przeciążonego elementu członkowskiego może nie mieć wpływ na wszystkich ustawień regionalnych. Ponadto [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] członków wybierz domyślną kulturę i formatowania w oparciu o założenia, które mogą nie być poprawne dla tego kodu. Aby upewnić się, że kod działa zgodnie z oczekiwaniami dla scenariuszy, należy podać informacje specyficzne dla kultury zgodnie z poniższymi wytycznymi:

-   Jeśli wartość będzie widoczny dla użytkownika, należy użyć bieżącej kultury. Zobacz <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

-   Jeśli wartości są przechowywane i używane przez oprogramowanie, oznacza to, utrwalone do pliku lub bazy danych, użyj Niezmienna kultura. Zobacz <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

-   Jeśli nie znasz docelowego wartości danych użytkownika lub dostawcy określenia kultury.

 Należy pamiętać, że <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> służy tylko do pobrania zlokalizowanych zasobów przy użyciu wystąpienia <xref:System.Resources.ResourceManager?displayProperty=fullName> klasy.

 Nawet jeśli domyślne zachowanie przeciążonego elementu członkowskiego jest odpowiednie do potrzeb, lepiej jest jawnie wywołać przeciążenia specyficzne dla kultury, dzięki czemu kod jest automatycznie dokumentowane i łatwiej utrzymywana.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, użyj przeciążenia, które przyjmuje <xref:System.Globalization.CultureInfo> lub <xref:System.IFormatProvider> i określić argument zgodnie z wytycznymi, które zostały wymienione wcześniej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy jest pewność, że kultury/format domyślny dostawca jest poprawny wybór, a utrzymanie kodu nie jest ważne programowanie priorytet.

## <a name="example"></a>Przykład
 W poniższym przykładzie `BadMethod` powoduje, że dwa naruszeń tej reguły. `GoodMethod` poprawia pierwszy naruszenie przez przekazanie Niezmienna kultura do System.String.Compare i usuwa drugi naruszenie przez przekazanie do bieżącej kultury <xref:System.String.ToLower%2A> ponieważ `string3` jest wyświetlana użytkownikowi.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono wpływ bieżącej kultury na domyślnym <xref:System.IFormatProvider> wybranego przez <xref:System.DateTime> typu.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

 W tym przykładzie tworzy następujące dane wyjściowe.

 **6/4/1900 12:15:12: 00**
**06-04-1900 12:15:12**
## <a name="related-rules"></a>Powiązanych reguł
 [CA1305: Określ interfejs IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Zobacz też
[Używanie klasy CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)