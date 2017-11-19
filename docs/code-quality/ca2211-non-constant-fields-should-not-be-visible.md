---
title: "CA2211: Niestałe pola nie powinny być widoczne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac9a04038ba1d80e8abba2efbbab19c9779c384a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Niestałe pola nie powinny być widoczne
|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Statyczne pole publiczne lub chronione nie jest stały, ani nie jest tylko do odczytu.  
  
## <a name="rule-description"></a>Opis reguły  
 Pola statyczne, które nie są ani stałe, ani tylko do odczytu, nie obsługują wielowątkowości. Dostęp do takiego pola muszą być dokładnie kontrolowane i wymaga zaawansowanych technik programowania dla synchronizacji dostępu do obiektu klasy. Ponieważ te są trudne umiejętności, aby dowiedzieć się więcej i wzorca i testowania takiego obiektu stanowi własne wyzwania, pola statyczne najlepiej są używane do przechowywania danych, który nie ulega zmianie. Ta reguła ma zastosowanie do bibliotek; aplikacje nie powinny ujawniać pól.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Napraw naruszenie tej reguły, aby pola statycznego stałej lub w trybie tylko do odczytu. Jeśli nie jest to możliwe, zmodyfikowanie typu użyć alternatywny mechanizm, takie jak właściwości wątkowo, która zarządza dostępem obsługującej wielowątkowość z polem. Należy pamiętać, że problemy, takie jak kolizje blokad oraz zakleszczenie może mieć wpływ na wydajność i zachowanie biblioteki.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, jeśli tworzysz aplikację i dlatego mają pełną kontrolę nad dostęp do typu, który zawiera pola statycznego. Projektanci biblioteki nie ma pomijać ostrzeżenie od tej reguły; za pomocą pola statyczne z systemem innym niż stała wprowadzić za pomocą biblioteki trudne dla deweloperów do używania poprawnie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza tę regułę.  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]