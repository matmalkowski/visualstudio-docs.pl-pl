---
title: 'CA1059: Elementy członkowskie nie powinny uwidaczniać pewnych typów konkretnych'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ed4ca74da92aebd26d70191121ec8f259fc4011
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Elementy członkowskie nie powinny uwidaczniać pewnych typów konkretnych
|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Widoczne na zewnątrz elementu członkowskiego jest określonego typu konkretnego lub przedstawia niektórych typów konkretnych za pomocą jednego z jego parametrów ani zwracanej wartości. Obecnie ta zasada zgłasza narażenia następujących typów konkretnych:

-   Typ pochodny <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Konkretny typ jest typem posiadającym pełną implementację i dlatego może zostać utworzone jego wystąpienie. Aby umożliwić powszechnego użycia elementu członkowskiego, Zastąp konkretnego typu sugerowane interfejsu. Umożliwia to element członkowski zaakceptować dowolnego typu, który implementuje interfejs lub można użyć, gdzie oczekiwany jest typ, który implementuje interfejs.

 W poniższej tabeli wymieniono docelowe konkretne typy i ich sugerowane zamiany.

|Konkretnego typu|Zastąpienie|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Przy użyciu interfejsu oddziela element członkowski z określonej implementacji źródła danych XML.|

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć naruszenie tej reguły, należy zmienić typu konkretnego sugerowane interfejsu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć komunikat od tej reguły, jeśli określone funkcje zapewniane przez konkretny typ jest wymagany.

## <a name="related-rules"></a>Powiązanych reguł
 [CA1011: Rozważ przekazanie typów podstawowych jako parametrów](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)