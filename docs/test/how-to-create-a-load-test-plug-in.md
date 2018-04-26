---
title: Tworzenie wtyczki w programie Visual Studio testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 482336bca7c177b3c4fdcb0f16faf7ea96d6c34b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-load-test-plug-in"></a>Porady: tworzenie wtyczki testu obciążenia

Można utworzyć wtyczkę testu obciążeniowego służącą do uruchamiania kodu w różnych momentach podczas wykonywania testu. Celem utworzenia wtyczki jest rozszerzenie lub zmodyfikowanie wbudowanej funkcjonalności testu obciążeniowego. Można na przykład napisać kod wtyczki testu obciążeniowego, który będzie ustawiał lub modyfikował wzorzec testu obciążeniowego podczas wykonywania testu. W tym celu należy utworzyć klasę, która dziedziczy interfejs <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>. Klasa musi implementować metodę <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> tego interfejsu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>.

> [!NOTE]
> Wtyczki można również utworzyć dla testów wydajności sieci Web. Aby uzyskać więcej informacji, zobacz [porady: tworzenie wtyczek testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)

## <a name="to-create-a-load-test-plug-in-by-using-visual-c"></a>Aby utworzyć wtyczkę testu obciążenia przy użyciu programu Visual C#

1.  Otwórz projekt testów wydajności i testów obciążeniowych sieci Web zawierający test wydajności sieci Web.

2.  Dodaj do projektu test obciążeniowy i skonfiguruj go tak, aby wykonywał test wydajności sieci Web.

     Aby uzyskać więcej informacji, zobacz [Szybki Start: Tworzenie projektu testu obciążenia](../test/quickstart-create-a-load-test-project.md).

3.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Dodaj** , a następnie wybierz **nowy projekt**.

     **Dodawanie nowego projektu** zostanie wyświetlone okno dialogowe.

4.  W obszarze **zainstalowane szablony**, wybierz pozycję **Visual C#**.

5.  Na liście szablonów wybierz **biblioteki klas**.

6.  W **nazwa** polu tekstowym, wpisz nazwę klasy.

7.  Wybierz **OK**.

8.  Nowy projekt biblioteki klas zostanie dodany do Eksploratora rozwiązania, a nowa klasa pojawi się w Edytorze kodu.

9. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** folderu w nowej biblioteki klas i wybierz **Dodaj odwołanie**.

10. **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

11. Wybierz **.NET** , przewiń w dół, a następnie wybierz **Microsoft.VisualStudio.QualityTools.LoadTestFramework**.

12. Wybierz **OK**.

     Odwołanie do **Microsoft.VisualStudio.QualityTools.LoadTestFramework** jest dodawany do **odwołania** folder w Eksploratorze rozwiązań.

13. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy górny węzeł wydajności sieci Web i obciążenia projekt testowy, który zawiera testu obciążenia, do której chcesz dodać testu obciążenia wtyczki i wybierz pozycję **Dodaj odwołanie**.

14. **Zostanie wyświetlone okno dialogowe Dodaj odwołanie**.

15. Wybierz **projekty** i wybierz projektu biblioteki klas.

16. Wybierz **OK**.

17. W Edytorze kodu dodaj instrukcję `using` dla przestrzeni nazw <xref:Microsoft.VisualStudio.TestTools.LoadTesting>.

18. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> dla klasy, która została utworzona w projekcie Biblioteka klas. Przykładową implementację przedstawiono w następującej sekcji Przykład.

19. Po napisaniu kodu skompiluj nowy projekt.

20. Kliknij prawym przyciskiem myszy górny węzeł testu obciążenia, a następnie wybierz pozycję **Dodawanie wtyczek testu obciążenia**.

     **Dodawanie wtyczek testu obciążenia** zostanie wyświetlone okno dialogowe.

21. W obszarze **wtyczka jest wybierana**, wybierz klasy wtyczki testu obciążenia.

22. W **właściwości wybranych wtyczek** okienko, ustaw wartość początkową dla wtyczki do użycia w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Właściwości wtyczki testu wydajności sieci Web można również zmienić później, w oknie Właściwości.

23. Wybierz **OK**.

     Wtyczka jest dodawany do **wtyczki testu obciążenia** folderu.

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

Poniższy kod pokazuje wtyczkę testu obciążeniowego, która uruchamia niestandardowy kod po wystąpieniu zdarzenia LoadTestFinished. Jeśli kod jest uruchamiany na agencie testowym na zdalnym komputerze, a agent testowy nie ma usługi SMTP localhost, test obciążeniowy pozostanie w stanie „W toku”, ponieważ pojawi się okno komunikatu.

> [!NOTE]
> Poniższy kod wymaga, aby dodać odwołanie do przestrzeni nazw System.Windows.Forms.


```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

Z testem obciążeniowym jest skojarzonych osiem zdarzeń, których wtyczka testu obciążeniowego może używać do uruchamiania niestandardowego kodu podczas testu obciążeniowego. Poniżej znajduje się lista zdarzeń umożliwiających dostęp do różnych okresów przebiegu testu obciążeniowego:

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Porady: tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)