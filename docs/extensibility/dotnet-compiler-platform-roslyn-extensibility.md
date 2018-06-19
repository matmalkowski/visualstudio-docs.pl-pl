---
title: Platforma kompilatora .NET (&quot;Roslyn&quot;) rozszerzalności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 09287c48285bfcdc32b1a7d558d44f9d212f1b41
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126939"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Platforma kompilatora .NET (&quot;Roslyn&quot;) rozszerzalności
Misji podstawowej platformy kompilatora .NET ("Roslyn") jest otwarcia Kompilatory języka C# i Visual Basic, dzięki czemu narzędzia i deweloperom udostępnionej w programie kompilatory bogate informacje ma temat programów. Narzędzi analizy kodu podnoszenie jakości kodu i kodu generatory pomocy w konstrukcji aplikacji. Jak narzędzia uzyskać inteligentny, muszą uzyskać dostęp do coraz więcej wiedzy dokładnego kodu, który przetwarza tylko kompilatory. Zamiast nieprzezroczystości tłumaczy (kod źródłowy w i kod obiektu wychodzących), kompilatory Roslyn oferują interfejsów API, które służy do zadań związanych z kodu, narzędzi i aplikacji.  
  
 Najlepsze w to kompilatory Roslyn, ich interfejsów API, przykłady i wskazówki i rzeczywistych narzędzia, rozszerzający te interfejsy API pełni Otwórz źródło na [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Przejdź do witryny OSS, aby dowiedzieć się więcej i rozpoczynanie pracy z Roslyn. Można znaleźć łącza, aby uzyskać najnowsze C# i VB funkcje, których można użyć jako użytkownik końcowy, a także łącza, aby rozpocząć pracę jako Konstruktor narzędzia korzystania z interfejsów API Roslyn.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do analizatorów Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)