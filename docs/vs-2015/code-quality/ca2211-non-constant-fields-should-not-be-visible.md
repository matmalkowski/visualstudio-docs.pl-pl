---
title: 'CA2211: Niestałe pola nie powinny być widoczne | Dokumentacja firmy Microsoft'
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
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d6ad55a49d335f5f776ba7b75f8006559e0eb38
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902297"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Niestałe pola nie powinny być widoczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2211: niestałe pola nie powinny być widoczne](https://docs.microsoft.com/visualstudio/code-quality/ca2211-non-constant-fields-should-not-be-visible).

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Statyczne pole publiczne lub chronione nie jest stały, ani nie jest tylko do odczytu.

## <a name="rule-description"></a>Opis reguły
 Pola statyczne, które nie są ani stałe, ani tylko do odczytu, nie obsługują wielowątkowości. Dostęp do takich pól musi być starannie kontrolowany i wymaga zaawansowanych technik programowania do synchronizowania dostępu do obiektu klasy. Ponieważ są to trudne umiejętności, aby dowiedzieć się więcej i główny i testowania taki obiekt stanowi swój własny wyzwania, pola statyczne najlepiej są używane do przechowywania danych, która nie zmienia. Ta reguła ma zastosowanie do bibliotek; aplikacje nie powinny uwidaczniać żadnych pól.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy pole statyczne, stałe, lub tylko do odczytu. Jeśli nie jest to możliwe, należy ponownie zaprojektować typu do użycia alternatywny mechanizm, takie jak właściwość metodą o bezpiecznych wątkach, która zarządza dostępem wątków z polem. Należy pamiętać, że problemy, takie jak Rywalizacja o blokady i zakleszczenia mogą mieć wpływ na wydajność i zachowanie biblioteki.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne Pomijaj ostrzeżeń dla tej reguły, jeśli tworzysz aplikację i dlatego mają pełną kontrolę nad dostępem do typu, który zawiera pole statyczne. Projektanci biblioteki nie ma pomijać ostrzeżenie od tej reguły; za pomocą pola statyczne niestałe ułatwia korzystanie z biblioteki, które są trudne dla deweloperów, aby prawidłowo używać.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]



