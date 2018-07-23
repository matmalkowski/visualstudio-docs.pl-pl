---
title: Ładowanie testowego interfejsu API w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9533083410af061ed8b2958349009cb5234ff251
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176248"
---
# <a name="how-to-use-the-load-test-api"></a>Porady: korzystanie z API testu obciążenia

Program Visual Studio obsługuje obciążenia wtyczki testu które mogą kontrolować lub zwiększ testu obciążeniowego. Wtyczki testu obciążenia są zdefiniowane przez użytkownika klas które implementują <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> interfejsu znaleziony w <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw. Wtyczki testu obciążenia umożliwiają kontrolę testu obciążenia niestandardowe, takie jak przerywanie testu obciążeniowego, po osiągnięciu progu licznika lub błąd. Użyj właściwości na <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> klasy, aby pobrać lub ustawić parametry testu obciążenia użytkownika zdefiniowane kodu. Używanie zdarzeń na <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> klasy, aby dołączyć delegatów dla powiadomień, gdy uruchomiony jest test obciążeniowy.

> [!TIP]
> Używanie przeglądarki obiektów do zbadania <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw. Edytory zarówno Visual C# i Visual Basic oferuje obsługę funkcji IntelliSense na kodowanie przy użyciu klas w przestrzeni nazw.

Można również utworzyć wtyczek dla testów wydajności sieci web. Aby uzyskać więcej informacji, zobacz [porady: tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md) i [porady: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Użycie tej przestrzeni nazw LoadTesting

1.  Otwórz test wydajności i obciążenia sieci web projektu, który zawiera test obciążenia.

2.  Dodaj Visual C# lub projekt biblioteki klas języka Visual Basic do rozwiązania testu.

3.  Dodaj odwołanie w projekcie testu wydajności i obciążenia sieci web do projektu biblioteki klas.

4.  Dodaj odwołanie do biblioteki DLL Microsoft.VisualStudio.QualityTools.LoadTestFramework w projekcie biblioteki klas.

5.  Plik klasy znajduje się w projekcie biblioteki klas, Dodaj `using` poufności informacji dotyczące <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw.

6.  Utwórz klasę publicznej, która implementuje <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> interfejsu.

7.  Skompiluj projekt.

8.  Dodaj nowy test obciążeniowy wtyczki, za pomocą edytora testu obciążenia:

    1.  Kliknij prawym przyciskiem myszy węzeł główny testu obciążeniowego, a następnie wybierz **Dodaj wtyczkę testu obciążeniowego**.

    2.  **Dodaj wtyczkę testu obciążenia** zostanie wyświetlone okno dialogowe.

    3.  W oknie właściwości dla wybranej wtyczki okienka Ustaw wartości początkowe dla wtyczki do użycia w czasie wykonywania.

        > [!NOTE]
        > Aby udostępnić dowolną liczbę właściwości dowolną z wtyczki. Wystarczy tylko ustawić je publiczne, można ustawić i typ podstawowy, np. Integer, Boolean lub String. Można również edytować właściwości wtyczki testu obciążenia, później za pomocą okna właściwości.

9. Uruchom test obciążenia.

     Na implementację <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>, zobacz [jak: utworzyć wtyczkę testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Porady: Korzystanie z API testu wydajności sieci Web](../test/how-to-use-the-web-performance-test-api.md)
- [Porady: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)