---
title: "Platforma kompilatora .NET (&quot;Roslyn&quot;) rozszerzalności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b292593c6a6c426bb184acd67a920b5e76e3a51f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Platforma kompilatora .NET (&quot;Roslyn&quot;) rozszerzalności
Misji podstawowej platformy kompilatora .NET ("Roslyn") jest otwarcia Kompilatory języka C# i Visual Basic, dzięki czemu narzędzia i deweloperom udostępnionej w programie kompilatory bogate informacje ma temat programów. Narzędzi analizy kodu podnoszenie jakości kodu i kodu generatory pomocy w konstrukcji aplikacji. Jak narzędzia uzyskać inteligentny, muszą uzyskać dostęp do coraz więcej wiedzy dokładnego kodu, który przetwarza tylko kompilatory. Zamiast nieprzezroczystości tłumaczy (kod źródłowy w i kod obiektu wychodzących), kompilatory Roslyn oferują interfejsów API, które służy do zadań związanych z kodu, narzędzi i aplikacji.  
  
 Najlepsze w to kompilatory Roslyn, ich interfejsów API, przykłady i wskazówki i rzeczywistych narzędzia, rozszerzający te interfejsy API pełni Otwórz źródło na [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Przejdź do witryny OSS, aby dowiedzieć się więcej i rozpoczynanie pracy z Roslyn. Można znaleźć łącza, aby uzyskać najnowsze C# i VB funkcje, których można użyć jako użytkownik końcowy, a także łącza, aby rozpocząć pracę jako Konstruktor narzędzia korzystania z interfejsów API Roslyn.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do analizatorów Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)