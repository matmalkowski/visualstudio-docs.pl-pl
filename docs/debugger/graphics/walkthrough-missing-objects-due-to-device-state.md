---
title: "Wskazówki: Brak obiektów spowodowany stanem urządzenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eed52d6408f7fd624e1d9c00d3fce95e4fb66c96
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>Wskazówki: brak obiektów spowodowany stanem urządzenia
W tym przewodniku przedstawiono sposób użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostyki grafiki do sprawdzania, czy obiekt, który nie istnieje ze względu na nieprawidłowo skonfigurowany stan urządzenia.  
  
 W tym przewodniku pokazano, jak:  
  
-   Użyj **listy zdarzeń grafiki** zlokalizować potencjalne źródła problemu.  
  
-   Użyj **etapy potoku grafiki** okno, aby sprawdzić efekt skonfigurowania `DrawIndexed` wywołania interfejsu API programu Direct3D.  
  
-   Użyj **Historia pikseli grafiki** okno, aby zlokalizować problem bardziej szczegółowo.  
  
-   Sprawdź stan urządzenia potencjalnych problemów lub błędy konfiguracji.  
  
## <a name="scenario"></a>Scenariusz  
 Jedną z przyczyn obiekty nie mogą być wyświetlane, gdzie jest oczekiwany w aplikacji 3-się błędnej konfiguracji urządzenia grafiki, które obiekty mają być wykluczone z renderowaniem — na przykład gdy kolejność zawijania powoduje trójkąty uboju, z błędami , lub kiedy funkcja test głębi powoduje, że wszystkie piksele w obiekcie odrzucono.  
  
 W scenariuszu, który jest opisany w tym przewodniku osiągnięto tylko pierwszy punkt kontrolny do tworzenia aplikacji 3- i rozpocząć testowanie go po raz pierwszy. Po uruchomieniu aplikacji tylko w interfejsie użytkownika jest renderowany na ekranie. Przy użyciu diagnostyki grafiki, przechwytywania problem z plikiem dziennika grafiki, aby umożliwić debugowanie aplikacji. Problem wygląda następująco w aplikacji:  
  
 ![Aplikacji przed problemu](media/vsg_walkthru1_firstview.png "vsg_walkthru1_firstview")  
  
 Aby uzyskać informacje o sposobie przechwytywania grafiki problemy w dzienniku grafiki, zobacz [przechwytywanie informacji graficznych](capturing-graphics-information.md).  
  
## <a name="investigation"></a>Badanie  
 Za pomocą narzędzia diagnostyki grafiki, można załadować pliku dziennika grafiki, aby sprawdzić ramek, które zostały przechwycone podczas testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby sprawdzić ramkę w dzienniku grafiki  
  
1.  W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], załadować dziennika grafiki, który zawiera ramkę, która wykazuje Brak modelu. Na nowej karcie diagnostyki grafiki jest wyświetlana w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W górnej części na tej karcie jest renderowanie danych wyjściowych zaznaczonej ramki. W dolnej części jest **listy ramek**, który będzie wyświetlany jako obraz miniatury każdego przechwyconej ramce.  
  
2.  W **listy ramek**, wybierz ramki, który pokazuje, że model nie jest wyświetlany. Obiektu docelowego renderowania jest aktualizowana w celu odzwierciedlenia zaznaczonej ramki. W tym scenariuszu grafiki dziennika kartę wygląda następująco:  
  
     ![.Vsglog kartę obiektu Podgląd i ramki listy](media/vsg_walkthru1_experiment.png "vsg_walkthru1_experiment")  
  
 Po zaznaczeniu ramki demonstrujący problem, można użyć **listy zdarzeń grafiki** do diagnozowania go. **Listy zdarzeń grafiki** zawiera każdego interfejsu API programu Direct3D wywołania wprowadzone do renderowania aktywną ramkę, na przykład wywołań interfejsu API, aby skonfigurować stanu urządzenia, aby tworzyć i aktualizować buforów i obiektów, które pojawiają się w ramce. Wiele rodzajów połączeń są interesujące, ponieważ często (ale nie zawsze) odpowiadającą jej zmianę w celu renderowania, kiedy aplikacja będzie działać zgodnie z oczekiwaniami, na przykład narysować, wysyłania, kopiowania lub wyczyść połączenia. Wywołań rysowania są zastosowanie szczególnie, ponieważ każda z nich reprezentuje geometry, który renderowany aplikacji (wywołań wysyłania można też renderować geometrii).  
  
#### <a name="to-ensure-that-draw-calls-are-being-made"></a>Aby upewnić się, że rysowania trwa wywołań  
  
1.  Otwórz **listy zdarzeń grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **listy zdarzeń**.  
  
2.  Sprawdź **listy zdarzeń grafiki** narysuj wywołania. Aby ułatwić, wprowadź "Rysuj" w **wyszukiwania** polu w prawym górnym rogu **listy zdarzeń grafiki** okna. Filtruje listę, tak aby zawierała tylko zdarzenia, które mają "Rysuj" w ich tytułów. W tym scenariuszu użytkownik stwierdzi, że wprowadzono kilka wywołań rysowania:  
  
     ![Lista zdarzeń grafiki, wyświetlanie zdarzeń przechwyconych](media/vsg_walkthru1_.png "vsg_walkthru1_")  
  
 Po upewnieniu się, że rysowania, której połączenia są nawiązywane, można określić, która odpowiada Brak geometrii. Ponieważ wiadomo, że brak geometrii jest nie jest wstawiany do elementu docelowego renderowania (w tym przypadku), można użyć **etapy potoku grafiki** okno, aby określić, które rysowania wywołania odnosi się do brakujących geometrii. **Etapy potoku grafiki** okno zawiera geometrię, która została wysłana do każdego wywołania rysunku, niezależnie od jego wpływ na obiektu docelowego renderowania. Podczas przenoszenia za pośrednictwem wywołania rysowania etapy potoku są zaktualizowane w celu wyświetlenia geometrię, która jest skojarzona z tym wywołaniem i renderowania danych wyjściowych jest aktualizowana w celu wyświetlenia stanu obiektu docelowego renderowania po wywołaniu.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Aby znaleźć wywołanie rysowania Brak geometrii  
  
1.  Otwórz **etapy potoku grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **etapy potoku**.  
  
2.  Przechodzenie między każde wywołanie rysowania obserwując **etapy potoku grafiki** Brak modelu w oknie. **Asemblera wprowadzania** etap zawiera dane pierwotne modelu. **Programu do cieniowania wierzchołków** etap zawiera dane po przekształceniu modelu. **Programu do cieniowania pikseli** etap zawierają dane wyjściowe programu do cieniowania pikseli. **Połączenia danych wyjściowych** etap pokazuje to wywołanie rysowania i poprzednich wywołań rysowania obiektu docelowego renderowania scalone.  
  
3.  Przerwij po osiągnięto wywołanie rysowania umożliwiająca Brak modelu. W tym scenariuszu **etapy potoku grafiki** okna wskazuje, że geometrii była renderowana, ale nie znajdował się w celu renderowania:  
  
     ![Podgląd potoku przedstawiający nieistniejącego obiektu](media/vsg_walkthru1_pipeline.png "vsg_walkthru1_pipeline")  
  
 Po upewnieniu się, że aplikacji renderowane Brak geometrii i Znajdź odpowiedniego wywołania rysowania, można wybrać część renderowania danych wyjściowych powinien Pokaż brak geometry, a następnie użyć **Historia pikseli grafiki** okno, aby dowiedzieć się, dlaczego wykluczono pikseli. Historia pikseli zawiera listę co wywołanie rysowania, który może wywrzeć wpływ na piksela. Wywołanie rysowania każdego w **Historia pikseli grafiki** okna jest identyfikowany przez numer, który jest wyświetlany również w **listy zdarzeń grafiki** okna. Dzięki temu można potwierdzić, że piksela powinien być wyświetlany Brak geometry, aby dowiedzieć się, dlaczego piksel został wykluczony, a  
  
#### <a name="to-determine-why-the-pixel-was-excluded"></a>Aby określić, dlaczego piksel został wykluczony.  
  
1.  Otwórz **Historia pikseli grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **historii pikseli**.  
  
2.  Na podstawie **programu do cieniowania pikseli** miniaturę, wybierz piksel w obiektu dane wyjściowe powinny zawierać część Brak geometrii. W tym scenariuszu dane wyjściowe programu do cieniowania pikseli obejmuje większość obiektu docelowego renderowania; Po wybraniu piksel **Historia pikseli grafiki** okno wygląda następująco:  
  
     ![Okno historii pikseli przedstawiający powiązane rysowania wywołania](media/vsg_walkthru1_hist1.png "vsg_walkthru1_hist1")  
  
3.  Upewnij się, że pikseli docelowego renderowania wybranego zawiera część geometrii przez dopasowanie liczba wywołanie rysowania jest zapoznanie (z **listy zdarzeń grafiki** okna) do jednego z tych wywołań rysowania w **grafiki Historia pikseli** okna. Jeśli żadna z tych wywołań w **Historia pikseli grafiki** zgodne okno wywołanie rysowania jest procedury kontroli, powtórz te czynności (z wyjątkiem kroku 1) do momentu znalezienia dopasowania. W tym scenariuszu odpowiadające wywołanie rysowania wygląda następująco:  
  
     ![Okno historii pikseli przedstawiający fragmentu informacji](media/vsg_walkthru1_hist2.png "vsg_walkthru1_hist2")  
  
4.  Po znalezieniu dopasowania rozwiń odpowiadające wywołanie rysowania w **Historia pikseli grafiki** okna i upewnij się, że piksel został wykluczony. Wywołanie rysowania każdego w **Historia pikseli grafiki** okna odnosi się do co najmniej jeden geometrycznych podstawowych (punkty, linie lub trójkąty), które przecina piksela wyniku geometrii odpowiedni obiekt. Takie przecięciu może przyczynić się do ostateczny kolor piksela. Podstawowy, który jest wykluczony, ponieważ test głębi ma nie jest reprezentowany przez ikonę, która zawiera literę Z nad strzałką odchyla dół od lewej do prawej.  
  
5.  Rozwiń wykluczonych typów pierwotnych do dalszego zbadania stanu, który spowodował mają zostać wykluczone. W **połączenia danych wyjściowych** grupy, przesuń wskaźnik myszy nad **wynik**. Etykietka narzędzia wskazuje, dlaczego element pierwotny została wykluczona. W tym scenariuszu badanie wykaże, że element pierwotny został wykluczony, ponieważ test głębi nie powiódł się i w związku z tym nie miało wpływu na kolor końcowy piksela.  
  
 Po określeniu, czy geometrii nie są wyświetlane, ponieważ jego podstawowych nie powiodło się test głębi, może podejrzewać, że ten problem jest związany z stan nieprawidłowo skonfigurowane urządzenia. Stan urządzenia i innych Direct3D object, dane można zbadać za pomocą **tabeli obiektów grafiki**.  
  
#### <a name="to-examine-device-state"></a>Aby sprawdzić stan urządzenia  
  
1.  Otwórz **tabeli obiektów grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **tabeli obiektów**.  
  
2.  Zlokalizuj **urządzeniem D3D10** obiektu w **tabeli obiektów grafiki**, a następnie otwórz **urządzeniem D3D10** obiektu. Nowy **urządzeniem d3d10** Otwiera kartę w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby ułatwić, można sortować **tabeli obiektów grafiki** przez **typu**:  
  
     ![Tabela obiektów graficznych i stan urządzenia powiązane](media/vsg_walkthru1_objtable.png "vsg_walkthru1_objtable")  
  
3.  Sprawdź stan urządzenia, która jest wyświetlana w **urządzeniem d3d10** kartę potencjalnych problemów. Ponieważ geometrii nie pojawia się, ponieważ jego podstawowych nie powiodło się test głębi, można skupić się na stan urządzenia, takie jak wzornika głębi, który ma wpływ na test głębi. W tym scenariuszu **opis wzornika głębi** (w obszarze **dane wyjściowe stanu połączenia**) zawiera wartość rzadko **funkcja głębokość** — członek, `D3D10_COMPARISON_GREATER`:  
  
     ![Okno urządzenia D3D10 przedstawiający informacje wzornika głębi](media/vsg_walkthru1_devicestate.png "vsg_walkthru1_devicestate")  
  
 Po ustaleniu, że przyczyny tego problemu renderowania może być nieprawidłowo głębokość funkcji, dzięki tym informacjom wraz z jego wiedzy kodu do zlokalizowania, gdy funkcja głębokość ustawiono nieprawidłowo, a następnie rozwiąż problem. Jeśli znasz kod, wyszukaj frazę problemu przy użyciu wskazówek, które zebranych podczas zostały debugowanie — na przykład na podstawie **opis wzornika głębi** w tym scenariuszu, wyszukaj frazę kod słowa "Głębokość" lub "GREATER". Po rozwiązaniu kod skompilować go ponownie i uruchomić aplikację ponownie, aby dowiedzieć się, że rozwiązanie jest problem renderowania:  
  
 ![Aplikacji po usunięciu problemu](media/vsg_walkthru1_finalview.png "vsg_walkthru1_finalview")