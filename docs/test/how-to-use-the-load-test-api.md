---
title: Ładowanie API testu w programie Visual Studio
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
ms.openlocfilehash: 3a5204848c24a25514fc8eb30a81dbca704a77a3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-the-load-test-api"></a>Porady: korzystanie z API testu obciążenia

Program Visual Studio obsługuje obciążenia testu wtyczek, które można kontrolować lub zwiększenia testu obciążenia. Wtyczki testu obciążenia są zdefiniowane przez użytkownika klas implementujących <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> interfejsu znalezione w <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw. Wtyczki testu obciążenia pozwalają kontroli testu obciążenia niestandardowych, takich jak test obciążenia zostanie przerwany, po spełnieniu progu licznika lub błąd. Użyj właściwości na <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> kodu zdefiniowana klasa można pobrać lub ustawić parametry testu obciążenia od użytkownika. Używanie zdarzeń na <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> klasę, aby dołączyć delegatów dla powiadomień, gdy działa testu obciążenia.

> [!TIP]
> Użyj przeglądarki obiektów do sprawdzenia <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw. Edytory Visual C# i Visual Basic oferuje obsługę funkcji IntelliSense dla kodowania z klas w przestrzeni nazw.

Wtyczki można również utworzyć dla testów wydajności sieci Web. Aby uzyskać więcej informacji, zobacz [porady: tworzenie wtyczek testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md) i [porady: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Użycie tej przestrzeni nazw LoadTesting

1.  Otwórz testu wydajności i obciążenia sieci Web projektu zawierającego testu obciążenia.

2.  Dodaj Visual C# lub Visual Basic projektu biblioteki klas do rozwiązania testu.

3.  Dodaj odwołanie w projekcie testowym wydajności i obciążenia sieci Web do projektu biblioteki klas.

4.  Dodaj odwołanie do biblioteki DLL Microsoft.VisualStudio.QualityTools.LoadTestFramework projektu biblioteki klas.

5.  Plik klasy znajdujące się w projektu biblioteki klas, Dodaj `using` instrukcji dla <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw.

6.  Utwórz publiczny klasę, która implementuje <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> interfejsu.

7.  Skompiluj projekt.

8.  Dodaj wtyczkę, za pomocą edytora testu obciążenia nowego testu obciążenia:

    1.  Kliknij prawym przyciskiem myszy węzeł główny testu obciążenia, a następnie wybierz pozycję **Dodawanie wtyczek testu obciążenia**.

    2.  **Dodawanie wtyczek testu obciążenia** zostanie wyświetlone okno dialogowe.

    3.  W oknie właściwości dla wybranego okienka wtyczki ustawić wartości początkowe dla wtyczki do użycia w czasie wykonywania.

        > [!NOTE]
        > Mogą uwidaczniać tyle właściwości z wtyczki. Wystarczy ustawić je publiczne, można ustawić i typu podstawowego, takie jak liczba całkowita, wartość logiczna lub ciąg. Można również edytować właściwości wtyczki testu obciążenia później przy użyciu okna właściwości.

9. Uruchamianie testów obciążenia.

     Dla implementacji <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>, zobacz [porady: tworzenie wtyczek testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Porady: Korzystanie z API testu wydajności sieci Web](../test/how-to-use-the-web-performance-test-api.md)
- [Porady: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)