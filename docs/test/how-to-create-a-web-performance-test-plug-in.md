---
title: Tworzenie wtyczki testu wydajności sieci Web dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: d7cb0eea7c6ebb32d0de4317a92fb83a8f7f2f10
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Porady: tworzenie wtyczki testu wydajności sieci Web

Testy wydajności sieci Web niego dodatki plug-in umożliwiają odizolowania i ponowne użycie kodu poza głównym deklaratywne instrukcje w teście wydajności sieci Web. Dostosowane testów wydajności sieci Web wtyczki daje możliwość wywołania kodu jako jest uruchomienie testu wydajności sieci Web. Wtyczki testu wydajności sieci Web jest uruchomić jeden raz dla każdej iteracji testu. Ponadto jeśli zastąpienie metody PreRequest lub PostRequest w wtyczkę testu, te wtyczki żądania zostanie uruchomiony przed lub po każdym żądaniu odpowiednio.

Można utworzyć dostosowane testu wydajności sieci Web wtyczki wyprowadzanie klasy z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> klasy podstawowej.

Korzystania dostosowane Web wydajności testu dodatków plug-in z testów wydajności sieci Web, które zostały zarejestrowane, co pozwala na zapis do minimum kodu w celu uzyskania większej liczby kontrolę nad testów wydajności sieci Web. Jednak umożliwia także je z kodowane testy wydajności sieci Web. Aby uzyskać więcej informacji, zobacz [Generowanie i Uruchamianie testów wydajności sieci web kodowane](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Można również utworzyć wtyczki testu obciążenia. Zobacz [porady: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Aby utworzyć niestandardowe testu wydajności sieci Web dodatku plug-in

1.  Otwórz projekt testów wydajności i testów obciążeniowych sieci Web zawierający test wydajności sieci Web.

2.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Dodaj** , a następnie wybierz **nowy projekt**.

     **Dodawanie nowego projektu** zostanie wyświetlone okno dialogowe.

3.  W obszarze **zainstalowane szablony**, wybierz pozycję **Visual C#**.

4.  Na liście szablonów wybierz **biblioteki klas**.

5.  W **nazwa** polu tekstowym, wpisz nazwę klasy.

6.  Wybierz **OK**.

7.  Nowy projekt biblioteki klas zostanie dodany do Eksploratora rozwiązania, a nowa klasa pojawi się w Edytorze kodu.

8.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** folderu w nowej biblioteki klas i wybierz **Dodaj odwołanie**.

9. **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

10. Wybierz **.NET** , przewiń w dół i wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework**

11. Wybierz **OK**.

     Odwołanie do **Microsoft.VisualStudio.QualityTools.WebTestFramework** jest dodawany do **odwołania** folder w Eksploratorze rozwiązań.

12. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy górny węzeł wydajności sieci Web i obciążenia projekt testowy, który zawiera testu obciążenia, do której chcesz dodać testu wydajności sieci Web wtyczki i wybierz pozycję **Dodaj odwołanie**.

13. **Zostanie wyświetlone okno dialogowe Dodaj odwołanie**.

14. Wybierz **projekty** i wybierz projektu biblioteki klas.

15. Wybierz **OK**.

16. W edytorze kodu napisać kod użytkownika dodatku plug-in. Najpierw utwórz nową klasę publicznego pochodzącego od <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

17. Implementuje kodu wewnątrz co najmniej jednego z programów obsługi zdarzeń. Przykładową implementację przedstawiono w następującej sekcji Przykład.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

18. Po napisaniu kodu skompiluj nowy projekt.

19. Otwórz testu wydajności sieci Web.

20. Aby dodać wtyczkę testu wydajności sieci Web, wybierz **Dodawanie wtyczek testu sieci Web** na pasku narzędzi.

     **Dodawanie wtyczek testu sieci Web** zostanie wyświetlone okno dialogowe.

21. W obszarze **wtyczka jest wybierana**, wybierz klasy wtyczki testu wydajności sieci Web.

22. W **właściwości wybranych wtyczek** okienko, ustaw wartość początkową dla wtyczki do użycia w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Właściwości wtyczki testu wydajności sieci Web można również zmienić później, w oknie Właściwości.

23. Wybierz **OK**.

     Wtyczka jest dodawany do **wtyczki testu sieci Web** folderu.

    > [!WARNING]
    > Po uruchomieniu testu wydajności sieci Web lub testu obciążenia, który korzysta z dodatku wystąpił błąd może uzyskać podobny do następującego:
    >
    > **Żądanie nie powiodło się: wyjątek w \<wtyczki > zdarzeń: nie można załadować pliku lub zestawu "\<pliku dll"Nazwa wtyczki">, wersja =\<n.n.n.n >, Culture = neutral, PublicKeyToken = null" lub jednej z jego zależności. System nie może odnaleźć określonego pliku.**
    >
    > Jest to spowodowane Jeśli dokonać zmian w kodzie wszelkie wtyczki i utworzyć nową wersję biblioteki DLL **(wersja = 0.0.0.0)**, ale wtyczki nadal odwołuje się do oryginalnej wersji dodatku plug-in. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1.  W wydajności sieci Web i obciążenia projekt testowy zostanie wyświetlone ostrzeżenie w odwołaniach. Usuń i ponownie dodać odwołanie do biblioteki DLL dodatku plug-in.
    > 2.  Usuń wtyczki z testu lub odpowiednią lokalizację, a następnie dodaj ją ponownie.

## <a name="example"></a>Przykład

Poniższy kod tworzy dostosowane testów wydajności sieci Web dodatku, który dodaje element do <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> reprezentujący iterację testu.

Po uruchomieniu testu wydajności sieci Web, korzystając z tej wtyczki widać dodanego elementu o nazwie **TestIteratnionNumber** w **kontekstu** tab podglądu wyników wydajności sieci Web.

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleRules
{
    [Description("This plugin can be used to set the ParseDependentsRequests property for each request")]
    public class SampleWebTestPlugin : WebTestPlugin
    {
        private bool m_parseDependents = true;

        public override void PreWebTest(object sender, PreWebTestEventArgs e)
        {
            // TODO: Add code to execute before the test.
        }

        public override void PostWebTest(object sender, PostWebTestEventArgs e)
        {
            // TODO: Add code to execute after the test.
        }

        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            // Code to execute before each request.
            // Set the ParseDependentsRequests value on the request
            e.Request.ParseDependentRequests = m_parseDependents;
        }

        // Properties for the plugin.
        [DefaultValue(true)]
        [Description("All requests will have their ParseDependentsRequests property set to this value")]
        public bool ParseDependents
        {
            get
            {
                return m_parseDependents;
            }
            set
            {
                m_parseDependents = value;
            }
        }
    }
}
```

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Porady: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)
- [Kodowanie niestandardowej reguły wyodrębniania dla testów wydajności sieci web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodowanie niestandardowej reguły walidacji dla testów wydajności sieci web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Porady: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i Uruchamianie testów wydajności sieci web kodowane](../test/generate-and-run-a-coded-web-performance-test.md)