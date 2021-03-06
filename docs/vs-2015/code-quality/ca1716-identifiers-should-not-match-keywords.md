---
title: 'CA1716: Identyfikatory nie powinny odpowiadać słowom | Dokumentacja firmy Microsoft'
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
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c1a3affbecf7a39ee323fd64bc8a56d92e8a4d5e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900675"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Identyfikatory nie powinny odpowiadać słowom kluczowym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1716: identyfikatory nie powinny odpowiadać słowom](https://docs.microsoft.com/visualstudio/code-quality/ca1716-identifiers-should-not-match-keywords).

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa przestrzeni nazw, typu lub elementu członkowskiego viritual lub interfejs odpowiada zastrzeżonym słowem kluczowym w języku programowania.

## <a name="rule-description"></a>Opis reguły
 Identyfikatory przestrzeni nazw, typów, jak i wirtualnych i składowe interfejsu nie powinny odpowiadać słowom, które są definiowane przez języki przeznaczone dla środowiska uruchomieniowego języka wspólnego. W zależności od języka, który jest używany i słowo kluczowe błędy kompilatora i niejednoznaczności może utrudnić bibliotekę do użycia.

 Ta reguła sprawdza, czy przed słów kluczowych w następujących językach:

-   Visual Basic

-   C#

-   C++/CLI

 Porównanie bez uwzględniania wielkości liter jest używana do [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] słów kluczowych i porównywanie uwzględniające wielkość liter jest używana w innych językach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wybierz nazwę, która nie ma na liście słów kluczowych.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Ostrzeżenie od tej reguły można pominąć, jeśli są przekonane, że identyfikator nie należy mylić użytkowników interfejsu API i czy biblioteki można używać we wszystkich językach, które znajdują się w [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].



