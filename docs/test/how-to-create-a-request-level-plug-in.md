---
title: Utwórz żądanie poziomie wtyczek dla testów wydajności sieci web w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ac50f956ed45f42f77638146c1340c0ed90f68fa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974034"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Porady: tworzenie wtyczki na poziomie żądania

*Żądania* są deklaratywne instrukcji, które stanowią testów wydajności sieci Web. Test wydajności sieci Web niego dodatki plug-in umożliwiają odizolowania i ponowne użycie kodu poza głównym deklaratywne instrukcje w teście wydajności sieci Web. Można tworzyć dodatki plug-in i dodaj je do pojedynczej żądania również do testu wydajności sieci Web, która go zawiera. Dostosowany *wtyczkę żądania* umożliwia wywołanie kodu, zgodnie z określonym żądaniem jest uruchamiana w teście wydajności sieci Web.

Wtyczka każde żądanie testu wydajności sieci Web ma PreRequest — metoda i metodę PostRequest. Po dołączeniu wtyczkę żądania do żądania http określonej PreRequest zdarzenie zostanie wyzwolone przed wygenerowania żądania i PostRequest uruchamiany po odebraniu odpowiedzi.

Można utworzyć dostosowane żądania testu wydajności sieci Web wtyczki wyprowadzanie klasy z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> klasy podstawowej.

Niestandardowe sieci Web wydajności testu żądania dodatki plug-in można użyć z testów wydajności sieci Web, które zostały zarejestrowane. Dostosowane wydajności sieci Web testów żądania umożliwia włączenie dodatki plug-in do zapisu niewielkiej ilości kod, aby osiągnąć większy poziom kontroli nad testów wydajności sieci Web. Jednak umożliwia także je z kodowane testy wydajności sieci Web. Zobacz [Generowanie i Uruchamianie testów wydajności sieci web kodowane](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>Aby utworzyć wtyczki na poziomie żądania

1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie. Wybierz **Dodaj** , a następnie wybierz **nowy projekt**.

     **Dodawanie nowego projektu** zostanie wyświetlone okno dialogowe.

2.  W obszarze **zainstalowane szablony**, wybierz pozycję **Visual C#**.

3.  Na liście szablonów wybierz **biblioteki klas**.

4.  W **nazwa** polu tekstowym, wpisz nazwę dla klasy i wybierz **OK**.

     Nowy projekt biblioteki klas zostanie dodany do Eksploratora rozwiązania, a nowa klasa pojawi się w Edytorze kodu.

5.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** folderu w nowej biblioteki klas i wybierz **Dodaj odwołanie**.

     **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

6.  Wybierz **.NET** , przewiń w dół, a następnie wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework** , a następnie wybierz **OK**

     Odwołanie do **Microsoft.VisualStudio.QualityTools.WebTestFramework** jest dodawany do **odwołania** folder w Eksploratorze rozwiązań.

7.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy górny węzeł wydajności sieci Web i obciążenia projekt testowy, który zawiera testu obciążenia, do której chcesz dodać wydajności testu żądania wtyczkę testu sieci Web. Wybierz **Dodaj odwołanie**.

     **Zostanie wyświetlone okno dialogowe Dodaj odwołanie**.

8.  Wybierz **projekty** karcie Wybierz projektu biblioteki klas, a następnie wybierz pozycję **OK** .

9. W edytorze kodu napisać kod użytkownika dodatku plug-in. Najpierw utwórz nową klasę publicznego pochodzącego od <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

10. Implementowanie kodu wewnątrz jednego lub obu z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> i <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> procedury obsługi zdarzeń. Przykładową implementację przedstawiono w następującej sekcji Przykład.

11. Po napisaniu kodu skompiluj nowy projekt.

12. Otwórz testu wydajności sieci Web, do której chcesz dodać wtyczkę żądania.

13. Kliknij prawym przyciskiem myszy żądania, do której chcesz dodać żądania wtyczki i wybierz pozycję **Dodawanie wtyczek żądania**.

     **Dodawanie wtyczek żądań testu sieci Web** zostanie wyświetlone okno dialogowe.

14. W obszarze **wtyczka jest wybierana**, wybierz nowego dodatku plug-in.

15. W **właściwości wybranych wtyczek** okienko, ustaw wartość początkową dla wtyczki do użycia w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Właściwości wtyczki testu wydajności sieci Web można również zmienić później, w oknie Właściwości.

16. Wybierz **OK**.

     Wtyczka jest dodawany do **żądania dodatków plug-in** folder, który jest folder podrzędny żądania HTTP.

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

Poniższy kod służy do tworzenia dostosowanych testów wydajności sieci Web wtyczki wyświetlający dwóch okien dialogowych. W oknie dialogowym pole zawiera adres URL, który jest skojarzony z tym żądaniem, do którego dołączyć dodatku żądania. Drugie okno dialogowe wyświetla nazwę komputera dla agenta.

> [!NOTE]
> Poniższy kod wymaga, aby dodać odwołanie do przestrzeni nazw System.Windows.Forms.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Kodowanie niestandardowej reguły wyodrębniania dla testów wydajności sieci web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodowanie niestandardowej reguły walidacji dla testów wydajności sieci web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Porady: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i Uruchamianie testów wydajności sieci web kodowane](../test/generate-and-run-a-coded-web-performance-test.md)