---
title: "Ostrzeżenia globalizacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aca9692b990df5b2612b04418729fec9cf59c256
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="globalization-warnings"></a>Globalizacja — Ostrzeżenia
Ostrzeżenia globalizacji obsługi bibliotek gotowe i aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Reguła|Opis|  
|----------|-----------------|  
|[CA1300: Określ MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|Aby poprawnie wyświetlić okno komunikatu dla kultur stosujących pismo od prawej do lewej, członkowie RightAlign i RtlReading wyliczenia MessageBoxOptions muszą być przekazani do metody Show.|  
|[CA1301: Należy unikać duplikowania akceleratorów](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Klucz dostępu, znany również jako akcelerator, umożliwia dostęp z klawiatury do formantu za pomocą klawisza ALT. Kiedy wiele formantów ma zduplikowany klucz dostępu, jego zachowanie nie jest dobrze zdefiniowane.|  
|[CA1302: Nie umieszczaj w kodzie ciągów specyficznych ustawień regionalnych](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Wyliczenie System.Environment.SpecialFolder zawiera elementy, które odwołują się do folderów specjalnych systemu. Lokalizacje tych folderów mogą mieć różne wartości w poszczególnych systemach operacyjnych; użytkownik może zmienić niektóre z tych lokalizacji; lokalizacje są zlokalizowane. Metoda Environment.GetFolderPath zwraca lokalizacje, które są skojarzone z wyliczeniem Environment.SpecialFolder, zlokalizowane i odpowiednie dla danego komputera.|  
|[CA1303: Nie należy przekazywać literałów jako zlokalizowanych parametrów](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Widocznej zewnętrznie metodzie przekazuje ciąg literału jako parametr do konstruktora lub metody w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] biblioteki klas i że powinien on być lokalizowalny.|  
|[CA1304: Określ CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)|Metoda lub konstruktor wywołuje członka mającego przeciążenie, które akceptuje parametr System.Globalization.CultureInfo i metodę lub konstruktor niewywołujący przeciążenia, które wymaga parametru CultureInfo. Kiedy obiekt CultureInfo lub System.IFormatProvider nie jest podany, domyślna wartość, która jest dostarczana przez członka przeciążonego, może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych.|  
|[CA1305: Określ IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|Metoda lub konstruktor wywołują jednego lub kilku członków, którzy mają przeciążenia akceptujące parametr System.IFormatProvider, i metody lub konstruktora, który nie wywołuje przeciążenia przyjmującego parametr IFormatProvider. Kiedy obiekt System.Globalization.CultureInfo lub IFormatProvider nie jest podany, domyślna wartość przekazywana przez członka przeciążonego może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych.|  
|[Ca1306: należy Ustawić ustawienia regionalne dla typów danych](../code-quality/ca1306-set-locale-for-data-types.md)|Ustawienia regionalne określą specyficzne dla kultur elementy prezentacji danych, takie jak formatowanie, które jest używane dla wartości liczbowych, symbole walut i porządek sortowania. Podczas tworzenia elementu DataTable lub DataSet należy jawnie ustawić ustawienia regionalne.|  
|[CA1307: Określ StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|Operacja porównania ciągu używa przeciążenia metody, które nie ustawia parametru StringComparison.|  
|[CA1308: Znormalizuj ciągi na wielkie litery](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Ciągi powinny być znormalizowane do użycia wielkich liter. Małe grupy znaków nie mogą wykonywać rund, gdy są one konwertowane na małe litery.|  
|[CA1309: Użyj porządkowego StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Operacja porównania ciągu, która jest nielingwistyczna, nie ustawia parametru StringComparison na Ordinal lub OrdinalIgnoreCase. Poprzez jawne ustawienie parametru na StringComparison.Ordinal lub StringComparison.OrdinalIgnoreCase kod często zaczyna działać szybciej, staje się bardziej poprawny i niezawodny.|  
|[CA2101: Należy określić marshaling dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Wywołanie platformy elementu członkowskiego umożliwia częściowo zaufanych wywołań ma parametr typu string, a nie jawnie kierować ten ciąg. Może to spowodować potencjalne luki w zabezpieczeniach.|