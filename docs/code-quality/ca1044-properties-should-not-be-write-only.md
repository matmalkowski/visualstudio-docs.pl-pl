---
title: "CA1044: Właściwości nie powinny być tylko do zapisu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cdb3ac5479193236b146c7c2607e5a27727695a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Właściwości nie powinny być tylko do zapisu
|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Właściwości publiczne lub chronione ma metodą dostępu set, ale nie ma metody dostępu get.  
  
## <a name="rule-description"></a>Opis reguły  
 Pobierz akcesorów zapewniają dostęp do odczytu do właściwości i metody dostępu set zapewniają dostęp do zapisu. Chociaż posiadanie właściwości tylko do odczytu jest dopuszczalne i często konieczne, wytyczne projektowania zabraniają używania właściwości tylko do zapisu. Jest to spowodowane przez użytkownika, ustaw wartość, a następnie uniemożliwia użytkownikowi wyświetlanie wartości nie zapewnia żadnych zabezpieczeń. Poza tym bez dostępu do odczytu nie można przeglądać stanu obiektów udostępnionych, co ogranicza ich przydatność.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Dodaj metodę dostępu get właściwości. Alternatywnie Jeśli konieczne jest zachowanie właściwości tylko do zapisu, należy wziąć pod uwagę konwertowanie tej właściwości na metodę.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Zdecydowanie zaleca się Pomijaj ostrzeżenia od tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `BadClassWithWriteOnlyProperty` jest typem z właściwością tylko do zapisu. `GoodClassWithReadWriteProperty`zawiera kod poprawiony.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]