---
title: 'Wskazówki: Używanie diagnostyki grafiki do debugowania cieniowania obliczenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b26772dd0cb74d90a8b7a401961fd33f86521a82
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Wskazówki: używanie diagnostyki grafiki do debugowania cieniowania obliczenia
W tym przewodniku przedstawiono sposób użycia narzędzia diagnostyki grafiki w programie Visual Studio do sprawdzania, czy cieniowania obliczenia, które generuje niepoprawnych wyników.  
  
 W tym przewodniku przedstawiono te zadania:  
  
-   Przy użyciu **listy zdarzeń grafiki** zlokalizować potencjalne źródła problemu.  
  
-   Przy użyciu **stosu wywołań zdarzeń grafiki** ustalenie, który obliczeniowe programu do cieniowania jest wykonywana przez DirectCompute `Dispatch` zdarzeń.  
  
-   Przy użyciu **etapy potoku grafiki** HLSL i okna debugera do sprawdzenia cieniowania obliczenia, który jest źródłem problemu.  
  
## <a name="scenario"></a>Scenariusz  
 W tym scenariuszu zostały zapisane symulację dynamics płynu używane DirectCompute do wykonywania najbardziej obliczeń intensywnie części aktualizacji symulacji. Gdy aplikacja jest uruchamiana, poprawna renderowania interfejsu użytkownika i zestaw danych, ale symulacji działają zgodnie z oczekiwaniami. Tak, aby umożliwić debugowanie aplikacji przy użyciu diagnostyki grafiki, można przechwytywać problem do dziennika grafiki. Problem wygląda następująco w aplikacji:  
  
 ![Symulowane płynu działa nieprawidłowo. ] (media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx_diag_demo_compute_shader_fluid_problem")  
  
 Aby uzyskać informacje o sposobie przechwytywania grafiki problemy w dzienniku grafiki, zobacz [przechwytywanie informacji graficznych](capturing-graphics-information.md).  
  
## <a name="investigation"></a>Badanie  
 Narzędzia diagnostyki grafiki do załadowania pliku dziennika grafiki, aby sprawdzić przechwycone ramki.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby sprawdzić ramkę w dzienniku grafiki  
  
1.  W programie Visual Studio Załaduj dziennika grafiki, który zawiera ramkę, która wykazuje symulacji niepoprawne wyniki. W programie Visual Studio pojawi się na nowej karcie diagnostyki grafiki. W górnej części na tej karcie jest renderowanie danych wyjściowych zaznaczonej ramki. W dolnej części jest **listy ramek**, które powoduje wyświetlenie miniatur każdego przechwyconej ramki.  
  
2.  W **listy ramek**, wybierz ramkę pokazano zachowanie niepoprawne symulacji. Nawet jeśli ten błąd pojawia się w symulacji kodu i nie kod renderowania, nadal jest konieczne wybieranie ramki, ponieważ DirectCompute zdarzenia są przechwytywane na podstawie przez klatka wraz z zdarzenia Direct3D. W tym scenariuszu grafiki dziennika kartę wygląda następująco:  
  
     ![Grafika Rejestruj dokument w programie Visual Studio. ] (media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx_diag_demo_compute_shader_fluid_step_1")  
  
 Po zaznaczeniu ramki demonstrujący problem, można użyć **listy zdarzeń grafiki** do diagnozowania go. **Listy zdarzeń grafiki** zawiera zdarzenia dla każdego wywołania DirectCompute i wywołania interfejsu API Direct3D, który został utworzony podczas aktywnej ramki — na przykład wywołania interfejsu API, aby uruchomić obliczenia na procesorze GPU lub do renderowania dataset lub interfejsu użytkownika. W takim przypadku Dbamy o `Dispatch` zdarzenia, które reprezentują części symulacji uruchamianych na procesorze GPU.  
  
#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Aby znaleźć zdarzenia wysyłania aktualizacji symulacji  
  
1.  Na **diagnostyki grafiki** narzędzi wybierz **listy zdarzeń** otworzyć **listy zdarzeń grafiki** okna.  
  
2.  Sprawdź **listy zdarzeń grafiki** zdarzenia rysowania, który renderuje zestawu danych. Aby ułatwić, wprowadź `Draw` w **wyszukiwania** polu w prawym górnym rogu **listy zdarzeń grafiki** okna. Filtruje listę, tak aby zawierała tylko zdarzenia, które mają "Rysuj" w ich tytułów. W tym scenariuszu użytkownik stwierdzi, że rysowania te zdarzenia wystąpił:  
  
     ![Na liście zdarzeń &#40;EL&#41; pokazuje rysowania zdarzenia. ] (media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx_diag_demo_compute_shader_fluid_step_2")  
  
3.  Obejrzyj obiektu docelowego renderowania w karcie dokument dziennika grafiki przenieść za pomocą każdego zdarzenia rysowania.  
  
4.  Przerwij po obiektu docelowego renderowania najpierw Wyświetla renderowanych zestawu danych. W tym scenariuszu zestawu danych jest renderowany w pierwszym przypadku rysowania. Błąd w symulacji wyświetlany:  
  
     ![Rysuj to zdarzenie renderuje symulacji zestawu danych. ] (media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx_diag_demo_compute_shader_fluid_step_3")  
  
5.  Teraz sprawdzić **listy zdarzeń grafiki** dla `Dispatch` zdarzeń, która aktualizuje symulacji. Ponieważ istnieje prawdopodobieństwo, że symulacji został zaktualizowany, zanim zostanie wyświetlony, użytkownik może skupić się najpierw na `Dispatch` zdarzenia występujące przed zdarzeniem rysowania, który renderuje wyniki. Aby ułatwić, zmodyfikuj **wyszukiwania** pole, aby odczytać `Draw;Dispatch;CSSetShader(`. Filtruje listę, tak aby zawiera także `Dispatch` i `CSSetShader` zdarzeń oprócz zdarzeń rysowania. W tym scenariuszu użytkownik stwierdza, że kilka `Dispatch` zdarzenia wystąpiły przed zdarzeniem rysowania:  
  
     ![Pokazuje EL rysowania zdarzenia wysyłki i CSSetShader](media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx_diag_demo_compute_shader_fluid_step_4")  
  
 Teraz, gdy wiesz, jakiego kilku potencjalnie wielu `Dispatch` zdarzeń może odpowiadać problem, można sprawdzić bardziej szczegółowo.  
  
#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Aby określić, które obliczeniowe programu do cieniowania wywołań wysyłania wykonuje  
  
1.  Na **diagnostyki grafiki** narzędzi wybierz **stosu wywołań zdarzeń** otworzyć **stosu wywołań zdarzeń grafiki** okna.  
  
2.  Począwszy od zdarzenie rysowania, który renderuje wyniki symulacji, ruch do tyłu za pośrednictwem każdej poprzedniej `CSSetShader` zdarzeń. Następnie w **stosu wywołań zdarzeń grafiki** okna, wybierz funkcję najwyższy można przejść do wywołania. W witrynie wywołanie służy pierwszy parametr [CSSetShader](http://msdn.microsoft.com/library/ff476402.aspx) wywołania funkcji do określenia, które obliczeniowe programu do cieniowania jest wykonywana przez następne `Dispatch` zdarzeń.  
  
 W tym scenariuszu istnieją trzy pary `CSSetShader` i `Dispatch` zdarzenia w każdej ramce. Praca Wstecz, trzeci reprezentuje parę integrację krok (gdzie płynne cząstki są w rzeczywistości przenoszone), Druga para reprezentuje krok życie obliczeń (w którym są obliczane wymusza, które mają wpływ na wszystkie składniki) i reprezentuje pierwszy pary Krok obliczania gęstości.  
  
#### <a name="to-debug-the-compute-shader"></a>Do debugowania cieniowania obliczenia  
  
1.  Na **diagnostyki grafiki** narzędzi wybierz **etapy potoku** otworzyć **etapy potoku grafiki** okna.  
  
2.  Wybierz trzecie `Dispatch` zdarzenia (poprzedzający natychmiast zdarzenie rysowania), a następnie w **etapy potoku grafiki** okna, w obszarze **obliczeniowy program do cieniowania** etap, wybierz  **Rozpocznij debugowanie**.  
  
     ![Wybranie trzeci zdarzenia wysyłania w EL.](media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx_diag_demo_compute_shader_fluid_step_6")  
  
     Debuger HLSL rozpoczyna się moduł, który wykonuje kroku integracji.  
  
3.  Zbadanie kodu źródłowego cieniowania obliczenia kroku integracji znaleźć przyczynę błędu. Użycie diagnostyki grafiki do debugowania HLSL cieniowania obliczenia kodu, można wykonywać krokowo kodu i użyć innych znanych narzędzi debugowania, np. okien wyrażeń kontrolnych. W tym scenariuszu należy określić, że prawdopodobnie w wyniku błędu w cieniowania obliczenia, który wykonuje kroku integracji.  
  
     ![Debugowania cieniowania obliczenia IntegrateCS. ] (media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx_diag_demo_compute_shader_fluid_step_7")  
  
4.  Aby zatrzymać debugowania cieniowania obliczenia na **debugowania** narzędzi wybierz **Zatrzymaj debugowanie** (klawiatury: Shift + F5).  
  
5.  Następnie wybierz pozycję drugiego `Dispatch` zdarzeń i rozpocząć debugowania cieniowania obliczenia, podobnie jak w poprzednim kroku.  
  
     ![Wybranie drugiego zdarzenia wysyłania w EL.](media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx_diag_demo_compute_shader_fluid_step_8")  
  
     Debuger HLSL rozpoczyna się programu do cieniowania, który oblicza wymusza, które mają wpływ na wszystkie składniki płynne.  
  
6.  Zbadanie kodu źródłowego programu do cieniowania obliczeniowe dla kroku życie obliczeń. W tym scenariuszu należy określić, czy źródło błędu jest tutaj.  
  
     ![Debugowanie ForceCS&#95;prosty obliczeniowe programu do cieniowania. ] (media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx_diag_demo_compute_shader_fluid_step_9")  
  
 Po określeniu lokalizacji błędu, można zatrzymać debugowanie i zmodyfikować kod źródłowy cieniowania obliczenia, aby poprawnie obliczyć odległość między cząstki wchodzącymi w interakcje. W tym scenariuszu należy zmienić wiersza `float2 diff = N_position + P_position;` do `float2 diff = N_position - P_position;`:  
  
 ![Poprawiony obliczeń&#45;kodu programu do cieniowania. ] (media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx_diag_demo_compute_shader_fluid_step_10")  
  
 W tym scenariuszu ponieważ programów do cieniowania obliczeniowe są kompilowane w czasie wykonywania, można tylko ponownym uruchomieniu aplikacji po wprowadzeniu zmian, aby sprawdzić ich wpływ na symulacyjnych. Nie masz odbudować aplikacji. Po uruchomieniu aplikacji, można wykryć poprawne działanie teraz symulacji.  
  
 ![Symulowane płynu działa poprawnie. ] (media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")