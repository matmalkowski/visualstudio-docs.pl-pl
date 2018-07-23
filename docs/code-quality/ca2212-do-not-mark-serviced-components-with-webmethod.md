---
title: 'CA2212: Nie należy oznaczać obsługiwanych składników znacznikiem WebMethod'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 88708fdcb41a43d3e8b3f78b4e66decb7211a4b4
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177425"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Nie należy oznaczać obsługiwanych składników znacznikiem WebMethod

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda w typie, który dziedziczy z <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> jest oznaczona za pomocą <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

<xref:System.Web.Services.WebMethodAttribute> ma zastosowanie do metody w ramach usługi sieci web XML, które zostały utworzone za pomocą programu ASP.NET; zapewnia metody wywoływane przez klientów sieci web do zdalnego. Metody i klasy musi być publiczny i wykonywanie w aplikacji sieci web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> typy są hostowane przez aplikacji modelu COM + i mogą używać usług COM +. <xref:System.Web.Services.WebMethodAttribute> nie ma zastosowania do <xref:System.EnterpriseServices.ServicedComponent> typów, ponieważ nie są przeznaczone dla tych samych scenariuszy. W szczególności Dodawanie atrybutu do <xref:System.EnterpriseServices.ServicedComponent> metody nie oznacza, że metody wywoływane przez klientów sieci web do zdalnego. Ponieważ <xref:System.Web.Services.WebMethodAttribute> i <xref:System.EnterpriseServices.ServicedComponent> metody mają konflikt zachowania i wymagania dotyczące kontekstu i przepływu transakcji, zachowanie metod będzie niepoprawne w niektórych scenariuszach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, usuń atrybut z <xref:System.EnterpriseServices.ServicedComponent> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Istnieje nie scenariuszy, w którym połączenie tych elementów jest poprawna.

## <a name="see-also"></a>Zobacz też

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>