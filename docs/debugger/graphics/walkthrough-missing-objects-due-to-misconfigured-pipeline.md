---
title: 'Wskazówki: Brak obiektów spowodowany błędnie skonfigurowanym potokiem | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2833c3ae2a8f03b69314db9e3723a640c4327587
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481882"
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>Wskazówki: brak obiektów spowodowany błędnie skonfigurowanym potokiem
W tym przewodniku przedstawiono sposób użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędziami diagnostyki grafiki do sprawdzania, czy obiekt, który jest nieobecnego z powodu programu do cieniowania pikseli unset.  
  
 W tym przewodniku przedstawiono te zadania:  
  
-   Przy użyciu **listy zdarzeń grafiki** zlokalizować potencjalne źródła problemu.  
  
-   Przy użyciu **etapy potoku grafiki** okno, aby sprawdzić efekt `DrawIndexed` wywołanie interfejsu API programu Direct3D.  
  
-   Sprawdzanie kontekst urządzenia, aby upewnić się, że nie ustawiono etapu programu do cieniowania.  
  
-   Przy użyciu **etapy potoku grafiki** okna razem z **stosu wywołań zdarzeń grafiki** ułatwiają znajdowanie źródła programu do cieniowania pikseli unset.  
  
## <a name="scenario"></a>Scenariusz  
 Gdy obiekt jest w 3-app, czasami jest ponieważ jeden z etapów programu do cieniowania nie została ustawiona przed renderowaniem obiektu. W aplikacji, które mają potrzeby renderowania proste źródło tego błędu jest zazwyczaj znajduje się gdzieś w stosie wywołań wywołania rysowania obiektu. Jednak do optymalizacji niektórych aplikacji partii razem obiektów, które mają programów do cieniowania, tekstury lub innych danych w celu zminimalizowania — zmiana stanu obciążenie. W tych aplikacjach źródła błędu może być ukryty w systemie przetwarzanie wsadowe, a nie znajduje się w stosie wywołań wywołania rysowania. Scenariusz, w tym przewodniku przedstawiono aplikację, która ma prosty renderowania potrzeb, a źródła błędu można znaleźć w stosie wywołań.  
  
 W tym scenariuszu gdy aplikacja jest uruchamiana, aby ją przetestować, tło jest renderowane zgodnie z oczekiwaniami, ale nie pojawia się jeden z obiektów. Przy użyciu diagnostyki grafiki, przechwytywania problem do dziennika grafiki, aby umożliwić debugowanie aplikacji. Problem wygląda następująco w aplikacji:  
  
 ![Obiekt nie może być widoczny](media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx_diag_demo_misconfigured_pipeline_problem")  
  
## <a name="investigation"></a>Badanie  
 Za pomocą narzędzia diagnostyki grafiki, można załadować dokument dziennika grafiki, aby sprawdzić ramek, które zostały przechwycone podczas testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby sprawdzić ramkę w dzienniku grafiki  
  
1.  W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], załadować dokument dziennika grafiki, który zawiera ramki, który wykazuje nieistniejącego obiektu. Na nowej karcie dziennika grafiki pojawia się w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W górnej części na tej karcie jest renderowanie danych wyjściowych zaznaczonej ramki. W dolnej części jest **listy ramek**, który będzie wyświetlany jako obraz miniatury każdego przechwyconej ramce.  
  
2.  W **listy ramek**, wybierz ramki, który pokazuje, że obiekt nie jest wyświetlany. Obiektu docelowego renderowania jest aktualizowana w celu odzwierciedlenia zaznaczonej ramki. W tym scenariuszu grafiki dziennika kartę wygląda następująco:  
  
     ![Grafika Rejestruj dokument w programie Visual Studio](media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx_diag_demo_misconfigured_pipeline_step_1")  
  
 Po wybraniu ramki demonstrujący problem, można rozpocząć diagnozowanie go za pomocą **listy zdarzeń grafiki**. **Listy zdarzeń grafiki** zawiera każdego wywołania interfejsu API programu Direct3D, wprowadzone do renderowania aktywną ramkę — na przykład, aby skonfigurować stanu urządzenia, aby tworzyć i aktualizować buforów i obiektów, które pojawiają się w ramce. Wiele rodzajów wywołań — na przykład rysowania, wysyłania, kopiowania lub wyczyść połączenia — są interesujące, ponieważ często (ale nie zawsze) odpowiadającą jej zmianę w celu renderowania, kiedy aplikacja będzie działać zgodnie z oczekiwaniami. Wywołań rysowania są zastosowanie szczególnie, ponieważ każda z nich reprezentuje geometry, który renderowany aplikacji.  
  
 Ponieważ wiadomo, że nie zawiera obiektu docelowego renderowania brakujący obiekt, ale także że wydaje się być inne błędy, możesz użyć **listy zdarzeń grafiki** razem z **etapy potoku grafiki**narzędzia, aby sprawdzić, które rysowania wywołania odnosi się do nieistniejącego obiektu geometrycznego. **Etapy potoku grafiki** okno zawiera geometrię, która została wysłana do każdego wywołania rysunku, niezależnie od jego wpływ na obiektu docelowego renderowania. Podczas przenoszenia za pośrednictwem wywołania rysowania etapy potoku są zaktualizowane w celu wyświetlenia geometrię, która jest skojarzona z każdego wywołania, ponieważ przechodzi ona przez każdego etapu włączone i renderowania danych wyjściowych jest aktualizowana w celu wyświetlenia stanu obiektu docelowego renderowania po zakończeniu wywołania.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Aby znaleźć wywołanie rysowania Brak geometrii  
  
1.  Otwórz **listy zdarzeń grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **listy zdarzeń**.  
  
2.  Otwórz **etapy potoku grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **etapy potoku**.  
  
3.  Podczas przeglądania przez każdego wywołania rysowania **listy zdarzeń grafiki** okna, watch **etapy potoku grafiki** okna dla nieistniejącego obiektu. Aby ułatwić, wprowadź "Rysuj" w **wyszukiwania** polu w prawym górnym rogu **listy zdarzeń grafiki** okna. Filtruje listę, tak aby zawierała tylko zdarzenia, które mają "Rysuj" w ich tytułów.  
  
     W **etapy potoku grafiki** okna, **asemblera wprowadzania** etap wyświetlana obiektu, który przed jest przekształcane i **programu do cieniowania wierzchołków** etap zawiera takie same obiekt po jest on przekształcany. W tym scenariuszu należy zauważyć, że **etapy potoku grafiki** Pokazuje okno **asemblera wprowadzania** i **programu do cieniowania wierzchołków** etapy, ale nie **programu do cieniowania pikseli**  etapu dla jednej z tych wywołań rysowania.  
  
    > [!NOTE]
    >  Jeśli inne etapy potoku — na przykład cieniowania powłoki, cieniowania domeny lub etapach programu do cieniowania geometrycznego — przetworzyć obiektu, z nich może być przyczyną tego problemu. Zazwyczaj problem dotyczy najwcześniejszym etapie w którym wynik nie jest wyświetlany lub jest wyświetlany w nieoczekiwany sposób.  
  
4.  Przerwij po przejściu wywołanie rysowania, która odnosi się do nieistniejącego obiektu. W tym scenariuszu **etapy potoku grafiki** okno oznacza, że geometrii został wystawiony dla procesora GPU (wskazywanym przez obecności **asemblera danych wejściowych** etap) i przekształcony (wskazywanym przez  **Program do cieniowania wierzchołków** etap), ale nie ma obiektu docelowego renderowania, ponieważ wygląda na to być programu do cieniowania pikseli active (wskazywanym przez braku **programu do cieniowania pikseli** etapu). W tym scenariuszu można nawet Zobacz nakładające brakuje obiektu w **połączenia danych wyjściowych** etap:  
  
     ![Zdarzenie DrawIndexed i jego wpływ na potok](media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx_diag_demo_misconfigured_pipeline_step_2")  
  
 Po upewnij się, czy aplikacja wystawiony wywołanie rysowania nieistniejącego obiektu geometrii i odnajdywanie, że etapu programu do cieniowania pikseli był nieaktywny, można zbadać stanu urządzenia, aby potwierdzić ustalenia. Można użyć **tabeli obiektów grafiki** zbadać kontekst urządzenia i inne dane obiektu Direct3D.  
  
#### <a name="to-examine-device-context"></a>Aby zbadać kontekst urządzenia  
  
1.  Otwórz **kontekstu urządzenia d3d11**. W **etapy potoku grafiki** okna, wybierz **ID3D11DeviceContext** łącza, który jest częścią `DrawIndexed` wywołaniu, które są wyświetlane u góry okna.  
  
2.  Sprawdź stan urządzenia, która jest wyświetlana w **kontekstu urządzenia d3d11** kartę, aby potwierdzić, że nie programu do cieniowania pikseli active podczas wywołania rysunku. W tym scenariuszu **ogólne informacje programu do cieniowania**— wyświetlane w obszarze **stan programu do cieniowania pikseli**— wskazuje, że programu do cieniowania jest **NULL**:  
  
     ![Kontekst urządzenia D3D 11 pokazuje stan programu do cieniowania pikseli](media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx_diag_demo_misconfigured_pipeline_step_4")  
  
 Po upewnieniu się, że program do cieniowania pikseli została ustawiona wartość null przez aplikację, następnym krokiem jest aby znaleźć lokalizację w kodzie źródłowym aplikacji którym ustawiono programu do cieniowania. Można użyć **listy zdarzeń grafiki** razem z **stosu wywołań zdarzeń grafiki** można znaleźć w tej lokalizacji.  
  
#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Aby dowiedzieć się, gdy program do cieniowania pikseli jest ustawiona w kodzie źródłowym aplikacji  
  
1.  Znajdź `PSSetShader` wywołanie, która odnosi się do nieistniejącego obiektu. W **listy zdarzeń grafiki** okna, wprowadź "Rysowanie; PSSetShader"w **wyszukiwania** polu w prawym górnym rogu **listy zdarzeń grafiki** okna. Filtruje listę, tak aby zawierało tylko zdarzenia "PSSetShader" i zdarzenia, które mają "Rysuj" w ich tytułów. Wybierz pierwsze `PSSetShader` wywołania wyświetlany przed wywołanie rysowania Brak obiektu.  
  
    > [!NOTE]
    >  `PSSetShader` nie będzie dłużej wyświetlane w **listy zdarzeń grafiki** okna, jeśli nie została ustawiona podczas tej ramki. Zazwyczaj dzieje się tak tylko, jeśli program do cieniowania pikseli tylko w jednym jest używana dla wszystkich obiektów lub `PSSetShader` wywołania przypadkowo został pominięty w trakcie tej ramki. W obu przypadkach zaleca się, że wyszukiwanie kodu źródłowego aplikacji dla `PSSetShader` wywołania i użyj tradycyjnych debugowania technik w celu badania zachowanie tych wywołań.  
  
2.  Otwórz **stosu wywołań zdarzeń grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **stosu wywołań zdarzeń grafiki**.  
  
3.  Użyj stos wywołań, aby zlokalizować `PSSetShader` wywołań w kodzie źródłowym aplikacji. W **stosu wywołań zdarzeń grafiki** okna, wybierz wywołania najwyższy i sprawdź, czy wartość jest ustawiana programu do cieniowania pikseli. Program do cieniowania pikseli może być ustawiony bezpośrednio na null lub wartość null, wartość mogą wystąpić z powodu argumentu przekazanego do funkcji lub inny stan. Jeśli go nie ustawiono bezpośrednio, można zlokalizować źródła wartości null gdzieś w górę stosu wywołań. W tym scenariuszu użytkownik stwierdzi, że program do cieniowania pikseli jest ustawiany bezpośrednio do `nullptr` w funkcji najwyższy, który nosi nazwę `CubeRenderer::Render`:  
  
     ![Kod, który nie zainicjować programu do cieniowania pikseli](media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx_diag_demo_misconfigured_pipeline_step_5")  
  
    > [!NOTE]
    >  Jeśli tak, sprawdzając stosu wywołań można zlokalizować źródła o wartości null, zaleca się ustawić punkt przerwania warunkowego na `PSSetShader` wywołań w taki sposób, że wykonywanie programu dzieli podczas programu do cieniowania pikseli zostanie ustawiona na wartość null. Następnie uruchom ponownie aplikację w trybie debugowania i użyć tradycyjnych metod debugowania w celu znalezienia źródła o wartości null.  
  
 Aby rozwiązać ten problem, należy przypisać programu do cieniowania pikseli poprawne za pomocą pierwszego parametru metody `ID3D11DeviceContext::PSSetShader` wywołanie interfejsu API.  
  
 ![Poprawiony C&#43; &#43; kod źródłowy](media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx_diag_demo_misconfigured_pipeline_step_6")  
  
 Po rozwiązaniu kodu można skompilować go ponownie i uruchomić aplikację ponownie, aby sprawdzić, czy renderowanie problem został rozwiązany:  
  
 ![Obiekt jest teraz wyświetlany](media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")