---
title: 'CA1824: Oznacz zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute | Dokumentacja firmy Microsoft'
ms.date: 03/29/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fb5b7665cedde698dd03a5e58adb4c4a72d0f461
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Oznacz zestawy za pomocą NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Zestaw zawiera **ResX**— na podstawie zasobów, ale nie ma <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> zastosować dla niego.

## <a name="rule-description"></a>Opis reguły

<xref:System.Resources.NeutralResourcesLanguageAttribute> Atrybut informuje Menedżera zasobów dla kultury domyślnej aplikacji. Jeśli domyślną kulturę zasoby osadzone w zestawie głównym aplikacji, a <xref:System.Resources.ResourceManager> musi pobrać zasobów, które należą do tej samej kultury kultury domyślnej <xref:System.Resources.ResourceManager> automatycznie używa zasobów znajdujących się w zestawie głównym zamiast wyszukiwanie zestawu satelickiego. Pomija sondowania zwykle zestawu, zwiększa wydajność wyszukiwania dla pierwszego zasobu obciążenia i może zmniejszyć zestaw roboczy.

> [!TIP]
> Zobacz [opakowanie i wdrażanie zasobów](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) procesu który <xref:System.Resources.ResourceManager> używa do sondowania dla plików zasobów.

## <a name="fix-violations"></a>Usuń naruszeń

Aby rozwiązać naruszenie tej reguły, Dodaj atrybut do zestawu i określ język zasobów kultury neutralnej.

### <a name="to-specify-the-neutral-language-for-resources"></a>Określa neutralny język zasobów

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **właściwości**.

2. Wybierz **aplikacji** , a następnie wybierz **informacji o zestawie**.

   > [!NOTE]
   > Jeśli Twój projekt jest projektem platformy .NET Standard lub .NET Core, wybierz **pakietu** kartę.

3. Wybierz język z **niezależnym od języka** lub **niezależnym od języka zestawu** listy rozwijanej.

4. Wybierz **OK**.

## <a name="when-to-suppress-warnings"></a>Kiedy pomijanie ostrzeżeń

Jest dozwolone w celu pominięcia ostrzeżenia od tej reguły. Jednak może zostać obniżona wydajność uruchamiania.

## <a name="see-also"></a>Zobacz także

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Zasoby w aplikacjach klasycznych (.NET)](/dotnet/framework/resources/)
- [CA1703 - ciągów zasobów powinna być poprawna](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701 - ciągu zasobu, który wyrazy złożone powinien mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)