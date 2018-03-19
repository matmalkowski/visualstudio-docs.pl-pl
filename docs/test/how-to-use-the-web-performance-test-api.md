---
title: "Sieci Web API testu wydajności w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 0662f81fe7b26a2da0164c19e9dedb4e0c971f41
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-the-web-performance-test-api"></a>Porady: korzystanie z API testu wydajności sieci Web

Można napisać kod dla testów wydajności sieci Web. Testu wydajności sieci Web interfejsu API jest używany do tworzenia zakodowanych testów wydajności sieci Web, testu wydajności sieci Web niego dodatki plug-in, wtyczki żądania, żądania, reguły wyodrębniania i reguł sprawdzania poprawności. Klasy, które tworzą te typy są podstawowe klasy w tym interfejsie API. Inne typy w tym interfejsie API są używane do obsługi tworzenia <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>, i <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> obiektów. Możesz użyć <xref:Microsoft.VisualStudio.TestTools.WebTesting> przestrzeni nazw, aby utworzyć dostosowany testów wydajności sieci Web.

 Aby programowo utworzyć i zapisać deklaratywne testów wydajności sieci Web umożliwia także interfejsu API testu wydajności sieci Web. Aby to zrobić, użyj <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> i <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer> klasy.

> [!TIP]
>  Użyj przeglądarki obiektów do sprawdzenia <xref:Microsoft.VisualStudio.TestTools.WebTesting> przestrzeni nazw. Edytory Visual C# i Visual Basic oferuje obsługę funkcji IntelliSense dla kodowania z klas w przestrzeni nazw.

 Można również utworzyć wtyczek dla testów obciążenia. Aby uzyskać więcej informacji, zobacz [porady: za pomocą interfejsu API Test obciążenia](../test/how-to-use-the-load-test-api.md) i [porady: tworzenie wtyczek testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Użycie tej przestrzeni nazw WebTesting

1.  Otwórz projekt testów wydajności i testów obciążeniowych sieci Web zawierający test wydajności sieci Web.

2.  Dodaj Visual C# lub Visual Basic projektu biblioteki klas do rozwiązania testu.

3.  Dodaj odwołanie w projekcie testowym wydajności i obciążenia sieci Web do projektu biblioteki klas.

4.  Dodaj odwołanie do biblioteki DLL Microsoft.VisualStudio.QualityTools.WebTestFramework w projektu biblioteki klas.

5.  W pliku klasy, które znajdują się w temacie projektu biblioteki klas, Dodaj `using` instrukcji dla <xref:Microsoft.VisualStudio.TestTools.WebTesting> przestrzeni nazw.

6.  Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> interfejsu.

7.  Skompiluj projekt.

8.  Dodaj wtyczkę testu wydajności nowej sieci Web za pomocą edytora testu wydajności sieci Web:

    1.  Wybierz **Dodawanie wtyczek testu sieci Web** na pasku narzędzi.

         **Dodawanie wtyczek testu sieci Web** zostanie wyświetlone okno dialogowe.

    2.  W obszarze **wtyczka jest wybierana**, wybierz klasy wtyczki testu wydajności sieci Web.

    3.  W **właściwości wybranych wtyczek** okienko, ustaw wartość początkową dla wtyczki do użycia w czasie wykonywania.

        > [!NOTE]
        > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Właściwości wtyczki testu wydajności sieci Web można również edytować później przy użyciu okna właściwości.

    4.  Wybierz **OK**.

9. Wykonaj test wydajności sieci Web.

     Na przykład stosowania <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, zobacz [porady: tworzenie wtyczek testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Porady: Korzystanie z API testu obciążenia](../test/how-to-use-the-load-test-api.md)
- [Porady: tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)