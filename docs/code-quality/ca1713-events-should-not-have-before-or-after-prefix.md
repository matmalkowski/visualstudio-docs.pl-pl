---
title: CA1713 Zdarzenia nie powinny posiadać prefiksów Before ani After
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc6d8b78ff1b00d1c5e5a6c6a597855243ea12fb
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550729"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713 Zdarzenia nie powinny posiadać prefiksów Before ani After
|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa zdarzenia rozpoczyna się od "Before" lub "After".

## <a name="rule-description"></a>Opis reguły
 Nazwy zdarzeń powinna opisywać akcję, która wywołuje zdarzenie. Nazwa powiązanych zdarzeń, które są wywoływane w określonej kolejności, używa czasu teraźniejszego lub przeszłego, aby wskazać względne położenie akcji w sekwencji. Na przykład gdy nazewnictwa parę zdarzenia, które jest wywoływane, gdy zamyka zasobu, można nazwać ją 'Zamykania' i 'Zamknięty' zamiast "BeforeClose" i "AfterClose".

 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Usuń prefiks z nazwy zdarzeń i Rozważ zmianę nazwy do użycia obecny czasu teraźniejszego lub przeszłego zlecenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.