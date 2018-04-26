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
ms.openlocfilehash: 67d2e2790db4a3e8061dcd949b79c127e67f022d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Nie należy oznaczać obsługiwanych składników znacznikiem WebMethod
|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metody w typie, który dziedziczy z <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> jest oznaczony atrybutem <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Web.Services.WebMethodAttribute> ma zastosowanie do metod w ramach usługi XML sieci Web, które zostały utworzone przy użyciu platformy ASP.NET; Powoduje to dodanie metodę można wywołać z klientów zdalnych w sieci Web. Metoda i klasa musi być publiczny i wykonywania w aplikacji sieci Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> typy są obsługiwane przez aplikacje modelu COM + i korzystania z usług COM +. <xref:System.Web.Services.WebMethodAttribute> nie ma zastosowania do <xref:System.EnterpriseServices.ServicedComponent> typów, ponieważ nie są przeznaczone do tych samych operacji. W szczególności dodanie atrybutu do <xref:System.EnterpriseServices.ServicedComponent> — metoda nie powoduje metodę można wywołać z klientów zdalnych w sieci Web. Ponieważ <xref:System.Web.Services.WebMethodAttribute> i <xref:System.EnterpriseServices.ServicedComponent> metoda ma sprzeczne zachowania i wymagania dotyczące kontekstu i przepływu transakcji, zachowanie metody będą niepoprawne w niektórych scenariuszach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, usuń atrybut z <xref:System.EnterpriseServices.ServicedComponent> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Brak żadnych scenariuszy, w którym połączenie tych elementów jest poprawna.

## <a name="see-also"></a>Zobacz też
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName><xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>