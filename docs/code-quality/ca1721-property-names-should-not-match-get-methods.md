---
title: "CA1721: Nazwy właściwości nie powinny odpowiadać metody get | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb0a1b45276e6563ab645100377dec25a9060e06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Nazwy właściwości nie powinny odpowiadać metodom Get
|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa elementu członkowskiego publiczne lub chronione rozpoczyna się od "Get" i w przeciwnym razie jest zgodna z nazwą właściwości publiczne lub chronione. Na przykład typ, który zawiera metodę o nazwie "GetColor" i właściwość o nazwie "Color" narusza tę regułę.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody GET i właściwości powinny mieć wyraźnie rozróżniające ich funkcji.  
  
 Konwencje nazewnictwa Podaj wygląd wspólnej dla bibliotek przeznaczonych środowisko uruchomieniowe języka wspólnego. Powoduje to skrócenie czasu, jest wymagany, aby dowiedzieć się więcej nowej biblioteki oprogramowania, którą można tworzyć bardziej niezawodne klienta, czy biblioteka został opracowany przez osobę, która ma doświadczenia w rozwijającym się kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmień nazwę, aby nie były zgodne nazwę metody, która jest prefiksem "Get".  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
> [!NOTE]
>  To ostrzeżenie można wykluczyć, jeżeli jest spowodowany implementowania interfejsu IExtenderProvider metody Get.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera metody i właściwości, które naruszają tę regułę.  
  
 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1024: Używaj właściwości wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)