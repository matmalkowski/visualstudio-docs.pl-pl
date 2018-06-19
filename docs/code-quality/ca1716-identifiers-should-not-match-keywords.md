---
title: 'CA1716: Identyfikatory nie powinny odpowiadać słowom kluczowym'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 514a062429168592fe46112ad008d0d1f4e60a28
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914787"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Identyfikatory nie powinny odpowiadać słowom kluczowym
|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa przestrzeni nazw, typu lub viritual lub interfejsu elementu członkowskiego odpowiada zastrzeżonym słowem kluczowym języka programowania.

## <a name="rule-description"></a>Opis reguły
 Identyfikatory dla przestrzeni nazw, typów, jak i wirtualnych i elementy członkowskie interfejsu nie powinny odpowiadać słów kluczowych, które są definiowane przez języków, których miejscem docelowym jest środowisko uruchomieniowe języka wspólnego. W zależności od języka, który jest używany i słowo kluczowe błędy kompilatora i niejednoznaczności może utrudnić bibliotekę do użycia.

 Ta reguła sprawdza przed słów kluczowych w następujących językach:

-   Visual Basic

-   C#

-   C++/CLI

 Porównania bez uwzględniania wielkości liter służy do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] słów kluczowych i porównania z uwzględnieniem wielkości liter, jest używany dla innych języków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wybierz nazwę, która nie ma na liście słów kluczowych.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Ostrzeżenie od tej reguły można pominąć, jeśli są przekonaniu, że identyfikator nie należy mylić użytkowników interfejsu API i że biblioteka jest można używać we wszystkich językach dostępne w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].