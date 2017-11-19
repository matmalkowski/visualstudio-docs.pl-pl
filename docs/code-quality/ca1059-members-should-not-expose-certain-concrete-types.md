---
title: "CA1059: Elementy członkowskie nie powinny ujawniać niektórych typów konkretnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5b8b4a50ce23a7ed50f2e608334f9b438a0b090
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [CA1011: Należy rozważyć przekazywanie typów podstawowych jako parametrów](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)