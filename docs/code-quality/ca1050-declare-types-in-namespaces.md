---
title: 'CA1050: Deklaruj typy w przestrzeniach nazw | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c0aeaaf3531c45668b8804a6285be5df211c2754
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Deklaruj typy w przestrzeni nazw
|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typu publiczne lub chronione jest zdefiniowany poza zakresem nazwanych przestrzeni nazw.  
  
## <a name="rule-description"></a>Opis reguły  
 Typ został zadeklarowany w przestrzeni nazw, aby uniknąć konfliktów nazw, jak i sposób organizowania powiązanych typów w hierarchii obiektów. Typy, które są poza nazwanych przestrzeni nazw znajdują się w globalnej przestrzeni nazw, która nie może być przywoływany w kodzie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, umieść typ w przestrzeni nazw.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Chociaż nie trzeba pominąć ostrzeżenie od tej reguły, jest bezpieczne, gdy zestaw nigdy nie będzie można używać razem z innych zestawów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono biblioteki, która ma typ niepoprawnie zadeklarowany poza obszar nazw i typ, który ma taką samą nazwę zadeklarowana w przestrzeni nazw.  
  
 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## <a name="example"></a>Przykład  
 Biblioteka, która została zdefiniowana wcześniej aplikację. Należy pamiętać, że typ, który jest zadeklarowana poza przestrzeni nazw jest tworzone, gdy nazwa `Test` nie jest kwalifikowana przez przestrzeni nazw. Należy zauważyć, że dostęp do `Test` wpisz `Goodspace`, wymagana jest nazwa przestrzeni nazw.  
  
 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]