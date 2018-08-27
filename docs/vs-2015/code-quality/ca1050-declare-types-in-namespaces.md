---
title: 'CA1050: Deklaruj typy w przestrzeniach nazw | Dokumentacja firmy Microsoft'
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
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ef0559cc727e7ffd667ee72ebe241a958fa57450
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900604"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Deklaruj typy w przestrzeni nazw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1050: deklaruj typy w przestrzeniach nazw](https://docs.microsoft.com/visualstudio/code-quality/ca1050-declare-types-in-namespaces).

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony jest zdefiniowana poza zakresem o nazwie przestrzeni nazw.

## <a name="rule-description"></a>Opis reguły
 Typy są deklarowane w przestrzeni nazw, aby zapobiec kolizjom nazw oraz jako sposób organizowania typów powiązanych w hierarchii obiektów. Typy, które wykraczają poza dowolnego obszaru nazw, o nazwie znajdują się w globalnej przestrzeni nazw, który nie można się odwoływać w kodzie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy umieścić w przestrzeni nazw typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Mimo, że masz nigdy nie Pomijaj ostrzeżeń dla tej reguły, jest bezpieczne to zrobić, gdy zestaw nigdy nie będzie używany wraz z innymi zestawami.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, biblioteki, która ma typ niepoprawnie zadeklarowanej na zewnątrz przestrzeni nazw i typ, który ma taką samą nazwę, zadeklarowany w przestrzeni nazw.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja używa biblioteki, która została zdefiniowana wcześniej. Należy pamiętać, czy typ, który jest zadeklarowana poza przestrzeni nazw jest tworzone, gdy nazwa `Test` nie jest kwalifikowana przez obszar nazw. Należy zauważyć, że dostęp do `Test` wpisać `Goodspace`, wymagane jest podanie nazwy przestrzeni nazw.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]



