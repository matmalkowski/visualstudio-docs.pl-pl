---
title: 'CA1040: Unikaj pustych interfejsów | Dokumentacja firmy Microsoft'
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
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2a08764921bb917fee6118eaa1880a81d82753fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684899"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Unikaj pustych interfejsów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1040: Unikaj pustych interfejsów](https://docs.microsoft.com/visualstudio/code-quality/ca1040-avoid-empty-interfaces).  
  
Element TypeName | AvoidEmptyInterfaces |  
| CheckId | CA1040 |  
| Kategoria | Microsoft.Design|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Interfejs zadeklarować wszystkie elementy Członkowskie lub nie implementuje dwa lub więcej interfejsów.  
  
## <a name="rule-description"></a>Opis reguły  
 Interfejsy definiują elementy członkowskie, które zapewniają zachowanie lub użycie kontraktu. Funkcjonalność opisana przez interfejs może zostać przyjęta przez dowolny typ, niezależnie od tego, gdzie ten typ się pojawia w hierarchii dziedziczenia. Typ implementuje interfejs, dostarczając implementacje dla jego elementów członkowskich. Pusty interfejs nie definiuje żadnych elementów członkowskich. W związku z tym nie definiuje kontraktu, który może być implementowana.  
  
 Jeśli projekt zawiera pusty powinny implementować interfejsy, które typy, prawdopodobnie używasz interfejsu jako znacznik lub do identyfikowania grupy typów. Jeśli ten identyfikator będzie występować w czasie wykonywania, prawidłowym sposobem, aby osiągnąć ten cel jest używać atrybutu niestandardowego. Użyj obecności lub braku atrybutu lub właściwości atrybutu, aby zidentyfikować typów docelowych. Jeśli identyfikator musi wystąpić w czasie kompilacji, a następnie dopuszcza się użycia pusty interfejs.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Usuń interfejs lub dodać członków do niego. Jeśli pusty interfejs jest używany jako etykieta zestaw typów, Zamień niestandardowy atrybut interfejsu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli ten interfejs jest używany do identyfikowania zestaw typów w czasie kompilacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje pusty interfejs.  
  
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]



