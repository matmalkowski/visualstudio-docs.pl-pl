---
title: 'Wskazówki: Brak obiektów spowodowany cieniowaniem wierzchołków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b669962fe1a0668b42aec29745072f3451966323
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31482012"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Wskazówki: brak obiektów spowodowany cieniowaniem wierzchołków
W tym przewodniku przedstawiono sposób użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędziami diagnostyki grafiki do sprawdzania, czy obiekt, który nie istnieje ze względu na błąd występujący podczas etapu programu do cieniowania wierzchołków.  
  
 W tym przewodniku przedstawiono te zadania:  
  
-   Przy użyciu **listy zdarzeń grafiki** zlokalizować potencjalne źródła problemu.  
  
-   Przy użyciu **etapy potoku grafiki** okno, aby sprawdzić efekt skonfigurowania `DrawIndexed` wywołania interfejsu API programu Direct3D.  
  
-   Przy użyciu **debuger HLSL** do sprawdzenia programu do cieniowania wierzchołków.  
  
-   Przy użyciu **stosu wywołań zdarzeń grafiki** ułatwiają znajdowanie źródła Nieprawidłowa stała HLSL.  
  
## <a name="scenario"></a>Scenariusz  
 Jednego z typowych przyczyn brakuje obiektu w 3-w aplikacji występuje, gdy program do cieniowania wierzchołków przekształca obiektu wierzchołków w sposób zwrócenie — obiekt może na przykład skalować do bardzo mały rozmiar, lub przekształcone w taki sposób, że prawdopodobnie za aparatu , a nie przed nim.  
  
 W tym scenariuszu gdy aplikacja jest uruchamiana, aby ją przetestować, tło jest renderowane zgodnie z oczekiwaniami, ale nie ma jednego z tych obiektów. Przy użyciu diagnostyki grafiki, przechwytywania problem do dziennika grafiki, aby umożliwić debugowanie aplikacji. Problem wygląda następująco w aplikacji:  
  
 ![Obiekt nie może być widoczny. ] (media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")  
  
## <a name="investigation"></a>Badanie  
 Za pomocą narzędzia diagnostyki grafiki, można załadować pliku dziennika grafiki, aby sprawdzić ramek, które zostały przechwycone podczas testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby sprawdzić ramkę w dzienniku grafiki  
  
1.  W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], załadować dziennika grafiki, który zawiera ramkę, która wykazuje nieistniejącego obiektu. Na nowej karcie dziennika grafiki pojawia się w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W górnej części na tej karcie jest renderowanie danych wyjściowych zaznaczonej ramki. W dolnej części jest **listy ramek**, który będzie wyświetlany jako obraz miniatury każdego przechwyconej ramce.  
  
2.  W **listy ramek**, wybierz ramki, który pokazuje, że obiekt nie jest wyświetlany. Obiektu docelowego renderowania jest aktualizowana w celu odzwierciedlenia zaznaczonej ramki. W tym scenariuszu grafiki dziennika kartę wygląda następująco:  
  
     ![Grafika Rejestruj dokument w programie Visual Studio](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")  
  
 Po wybraniu ramki demonstrujący problem, można rozpocząć diagnozowanie go za pomocą **listy zdarzeń grafiki**. **Listy zdarzeń grafiki** zawiera każdego interfejsu API programu Direct3D wywołania wprowadzone do renderowania aktywną ramkę, na przykład wywołań interfejsu API, aby skonfigurować stanu urządzenia, aby tworzyć i aktualizować buforów i obiektów, które pojawiają się w ramce. Wiele rodzajów połączeń są interesujące, ponieważ często (ale nie zawsze) odpowiadającą jej zmianę w celu renderowania, kiedy aplikacja będzie działać zgodnie z oczekiwaniami, na przykład narysować, wysyłania, kopiowania lub wyczyść połączenia. Wywołań rysowania są zastosowanie szczególnie, ponieważ każda z nich reprezentuje geometry, który renderowany aplikacji (wywołań wysyłania można też renderować geometrii).  
  
 Ponieważ wiadomo, że brakuje obiektu jest nie jest wstawiany do elementu docelowego renderowania (w tym przypadku) — ale, że pozostała część sceny jest rysowany zgodnie z oczekiwaniami — można użyć **listy zdarzeń grafiki** razem z **potoku grafiki Etapy** narzędzia, aby sprawdzić, które rysowania wywołania odnosi się do nieistniejącego obiektu geometrycznego. **Etapy potoku grafiki** okno zawiera geometrię, która została wysłana do każdego wywołania rysunku, niezależnie od jego wpływ na obiektu docelowego renderowania. Podczas przenoszenia za pośrednictwem wywołania rysowania etapy potoku są zaktualizowane w celu wyświetlenia geometrię, która jest skojarzona z tym wywołaniem i renderowania danych wyjściowych jest aktualizowana w celu wyświetlenia stanu obiektu docelowego renderowania po wywołaniu.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Aby znaleźć wywołanie rysowania Brak geometrii  
  
1.  Otwórz **listy zdarzeń grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **listy zdarzeń**.  
  
2.  Otwórz **etapy potoku grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **etapy potoku**.  
  
3.  Podczas przeglądania przez każdego wywołania rysowania **listy zdarzeń grafiki** okna, watch **etapy potoku grafiki** okna dla nieistniejącego obiektu. Aby ułatwić, wprowadź "Rysuj" w **wyszukiwania** polu w prawym górnym rogu **listy zdarzeń grafiki** okna. Filtruje listę, tak aby zawierała tylko zdarzenia, które mają "Rysuj" w ich tytułów.  
  
     W **etapy potoku grafiki** okna, **asemblera wprowadzania** etap pokazuje obiektu geometrii przed jego przekształcone i **programu do cieniowania wierzchołków** etap zawiera takie same obiekt po jest on przekształcany. W tym scenariuszu, wiadomo, że uda Ci się znaleźć nieistniejącego obiektu wyświetlanym w **asemblera danych wejściowych** etapu i nic nie jest wyświetlana w **programu do cieniowania wierzchołków** etapu.  
  
    > [!NOTE]
    >  Jeśli pozostałe etapy geometrii — na przykład cieniowania powłoki, cieniowania domeny lub cieniowania geometrycznego etapach — przetworzyć obiektu, mogą one być przyczyną tego problemu. Zazwyczaj problem dotyczy najwcześniejszym etapie w którym wynik nie jest wyświetlany lub jest wyświetlany w nieoczekiwany sposób.  
  
4.  Przerwij po przejściu wywołanie rysowania, która odnosi się do nieistniejącego obiektu. W tym scenariuszu **etapy potoku grafiki** okno oznacza, że geometrii został wystawiony dla procesora GPU (wskazywanym przez miniatur asemblera dane wejściowe), ale nie ma obiektu docelowego renderowania, ponieważ wystąpił błąd podczas etapu programu do cieniowania wierzchołków (wskazywanym przez program do cieniowania wierzchołków miniatur):  
  
     ![Zdarzenie DrawIndexed i jego wpływ na potok](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")  
  
 Po zakończeniu upewnij się, czy aplikacja wystawiony wywołanie rysowania nieistniejącego obiektu geometrii i odnajdywanie, że ten problem będzie się działo podczas etapu programu do cieniowania wierzchołków, służy do badania programu do cieniowania wierzchołków i dowiedzieć się, co się stało z obiektu, który debuger HLSL. Można użyć debuger HLSL sprawdzać stan HLSL zmienne w czasie wykonywania kroków kodu HLSL i ustaw punkty przerwania, aby zdiagnozować problem.  
  
#### <a name="to-examine-the-vertex-shader"></a>Aby sprawdzić programu do cieniowania wierzchołków  
  
1.  Uruchom profilowanie etapu programu do cieniowania wierzchołków. W **etapy potoku grafiki** okna, w obszarze **programu do cieniowania wierzchołków** etap, wybierz **Rozpocznij debugowanie** przycisku.  
  
2.  Ponieważ **asemblera wprowadzania** etap powinien zapewniać danych do programu do cieniowania wierzchołków i **programu do cieniowania wierzchołków** etap pojawi się wygenerowało żadnych danych wyjściowych, aby zbadać dane wyjściowe programu do cieniowania wierzchołków struktury, `output`. Jak można wykonywać krokowo kodu HLSL, należy wykonać dokładniejszą podczas wyszukiwania `output` jest modyfikowany.  
  
3.  Przy pierwszej `output` jest modyfikowany, element członkowski `worldPos` są zapisywane.  
  
     ![Wartość "output.worldPos" pojawia się uzasadnione](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")  
  
     Ponieważ wartość wydaje się być uzasadnione, w przypadku kontynuowania krokowe wykonywanie kodu aż do następnego wiersza, który modyfikuje `output`.  
  
4.  Przy następnym `output` jest modyfikowany, element członkowski `pos` są zapisywane.  
  
     ![Wyzerowanie wartość "output.pos"](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")  
  
     Teraz, wartość `pos` elementu członkowskiego — same zera — podejrzane. Następnie chcesz określić sposób `output.pos` pochodzi będzie mieć wartość z samych zer.  
  
5.  Można zauważyć, że `output.pos` przyjmuje wartość zmiennej o nazwie `temp`. W poprzednim wierszu, zobaczysz, że wartość `temp` jest wynikiem mnożenia poprzedniej wartości przez stałą o nazwie `projection`. Zachodzi podejrzenie, że `temp`przez wartość podejrzane wynika z tego mnożenia. Po umieszczeniu wskaźnika myszy na `projection`, można zauważyć, że jego wartość jest również same zera.  
  
     ![Projekcja macierz nie zawiera nieprawidłowych transformacji](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")  
  
     W tym scenariuszu badanie wykaże, że `temp`na podejrzane wartość to najprawdopodobniej spowodowane przez jego mnożenia przez `projection`i dlatego `projection` jest stałą, który ma zawierać macierzy projekcji, wiadomo, nie powinien zawiera same zera.  
  
 Po ustaleniu, że stała HLSL `projection`— przekazywane do programu do cieniowania przez aplikację — jest prawdopodobnie źródło problemu, następnym krokiem jest aby znaleźć lokalizację w kodzie źródłowym aplikacji, gdzie jest wypełniony stałego buforu. Można użyć **stosu wywołań zdarzeń grafiki** można znaleźć w tej lokalizacji.  
  
#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Aby znaleźć, gdzie stała jest ustawiana w kodzie źródłowym aplikacji  
  
1.  Otwórz **stosu wywołań zdarzeń grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **stosu wywołań zdarzeń grafiki**.  
  
2.  Przejdź do kodu źródłowego aplikacji w górę stosu wywołań W **stosu wywołań zdarzeń grafiki** okna, wybierz wywołania najwyższy, aby zobaczyć, czy stały bufor jest wypełniany. Jeśli nie, nadal górę stosu wywołań do momentu znalezienia, gdzie jest wypełniany. W tym scenariuszu użytkownik stwierdzi, że stały bufor jest wypełniony — za pomocą `UpdateSubresource` interfejsu API programu Direct3D — dalsze górę stosu wywołań funkcji o nazwie `MarbleMaze::Render`, oraz że jego wartość pochodzi z obiektu stałego buforu o nazwie `m_marbleConstantBufferData` :  
  
     ![Kod, który ustawia obiektu stałego buforu](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")  
  
    > [!TIP]
    >  Jeśli jednocześnie debugowania aplikacji, można ustawić punktu przerwania w tej lokalizacji i zostanie uruchomiona podczas renderowania następnej ramki. Następnie możesz sprawdzić członków `m_marbleConstantBufferData` potwierdzić, że wartość `projection` elementu członkowskiego jest ustawiona na same zera, gdy stały bufor jest wypełnione.  
  
 Po Znajdź lokalizację, w którym wypełniany jest stały bufor i czy jego wartości pochodzą z zmiennej odnajdywanie `m_marbleConstantBufferData`, następnym krokiem jest, aby dowiedzieć się, gdzie `m_marbleConstantBufferData.projection` elementu członkowskiego jest ustawiona na same zera. Można użyć **Znajdź wszystkie odwołania** do szybkiego skanowania w poszukiwaniu kod, który zmienia wartość `m_marbleConstantBufferData.projection`.  
  
#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Aby dowiedzieć się, których projekcji element członkowski ma wartość w kodzie źródłowym aplikacji  
  
1.  Znajdź odwołania do `m_marbleConstantBufferData.projection`. Otwórz menu skrótów dla zmiennej `m_marbleConstantBufferData`, a następnie wybierz pozycję **Znajdź wszystkie odwołania**.  
  
2.  Aby przejść do lokalizacji linii w kodzie źródłowym aplikacji gdzie `projection` elementu członkowskiego jest modyfikowany, wybierz polecenie tego wiersza w **wyniki Znajdź Symbol** okna. Ponieważ pierwszego wyniku, który modyfikuje projekcji element członkowski nie może być przyczyną tego problemu, należy sprawdzić kilka obszarów kodu źródłowego aplikacji.  
  
 Po znalezieniu lokalizację gdzie `m_marbleConstantBufferData.projection` jest ustawiona, można sprawdzić otaczającego je kodu źródłowego w celu określenia pochodzenia niepoprawną wartość. W tym scenariuszu użytkownik stwierdza, że wartość `m_marbleConstantBufferData.projection` ma ustawioną wartość zmiennej lokalnej o nazwie `projection` przed zainicjowano wartość, która jest określany przez kod `m_camera->GetProjection(&projection);` w następnym wierszu.  
  
 ![Projekcja Marmur jest ustawiony przed zainicjowaniem](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")  
  
 Aby rozwiązać ten problem, Przenieś wiersz kodu, która ustawia wartości `m_marbleConstantBufferData.projection` po wierszu, który inicjuje wartość zmiennej lokalnej `projection`.  
  
 ![Poprawiony C&#43; &#43; kod źródłowy](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")  
  
 Po rozwiązaniu kodu można skompilować go ponownie i uruchomić aplikację ponownie, aby dowiedzieć się, że rozwiązanie jest problem renderowania:  
  
 ![Obiekt, w obecnie wyświetlane. ] (media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")