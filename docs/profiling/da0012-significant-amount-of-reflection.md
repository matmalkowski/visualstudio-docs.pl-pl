---
title: ': Da0012 znaczne odbicie | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 203de647342affb9d81f0a57d0bcd44ac983f307
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Znaczne odbicie
|||  
|-|-|  
|Identyfikator reguły|DA0012|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Pobierania próbek|  
|Komunikat|Użytkownik może być nadmiernie używasz odbicia. Jest kosztowna operacja.|  
|Typ reguły|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Wywołania do metody System.Reflection, takie jak element InvokeMember i GetMember lub metody typu, takich jak MemberInvoke są znaczna część danych profilowania. Jeśli to możliwe, należy wziąć pod uwagę zastępuje tych metod z wczesnym powiązaniem, które metody zestawów zależnych.  
  
## <a name="rule-description"></a>Opis reguły  
 Odbicie jest elastyczne funkcje .NET Framework, który może służyć do wykonywania późne wiązanie aplikacji zależnych zestaw czasu wykonywania, lub do tworzenia i dynamicznie wykonania nowych typów w czasie wykonywania. Jednak te techniki może obniżyć wydajność, jeśli są często używane lub w ścisłej pętle.  
  
 Aby uzyskać więcej informacji, zobacz [odbicie i późne wiązanie](http://go.microsoft.com/fwlink/?LinkId=177826) sekcji rozdziału 5 — poprawy zarządzane działania kodu poprawy wydajności aplikacji .NET i skalowalność wielkości Microsoft Patterns and Practices Biblioteka w witrynie MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widok szczegółów funkcji](../profiling/function-details-view.md) danych profilowania. Sprawdź funkcje wywoływania metody System.Type lub System.Reflection można znaleźć w sekcji programów Najczęściej korzystanie z interfejsów API odbicia platformy .NET. Unikaj używania metody, które zwracają metadanych. Wydajność aplikacji jest szczególnie ważne, należy unikać późne wiązanie i tworzenie typów dynamicznie w czasie wykonywania.