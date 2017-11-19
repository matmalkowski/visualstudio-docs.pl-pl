---
title: "Wskazówki: Debugowanie błędów renderowania spowodowanych cieniowaniem | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4e11a6b3c3a72c43bf96494a6d87ecc42e31fdf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Wskazówki: debugowanie błędów renderowania spowodowanych cieniowaniem
W tym przewodniku przedstawiono sposób użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostyki grafiki do sprawdzania, czy obiekt, który jest niepoprawnie pokolorowane z powodu błędu programu do cieniowania.  
  
 W tym przewodniku pokazano, jak:  
  
-   Sprawdź dokument dziennika grafiki, aby zidentyfikować pikseli, które zawierają problem.  
  
-   Użyj **Historia pikseli grafiki** okno, aby lepiej sprawdzić stan pikseli.  
  
-   Użyj **debuger HLSL** do sprawdzenia programów do cieniowania pikseli i wierzchołków.  
  
## <a name="scenario"></a>Scenariusz  
 Niepoprawne kolorowanie na obiekty najczęściej występuje po cieniowania wierzchołków przekazuje piksel programu do cieniowania nieprawidłowe lub niekompletne informacje.  
  
 W tym scenariuszu użytkownik niedawno dodał obiektu do aplikacji, oraz nowe wierzchołka i Przekształć obiekt i nadaj mu unikatowy wygląd programów do cieniowania pikseli. Po uruchomieniu aplikacji podczas testu, obiekt jest renderowany w kolorze czarnym stałe. Przy użyciu diagnostyki grafiki, przechwytywania problem do dziennika grafiki, aby umożliwić debugowanie aplikacji. Problem wygląda następująco w aplikacji:  
  
 ![Obiekt jest odwzorowywany z nieprawidłowych kolorów. ] (media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")  
  
## <a name="investigation"></a>Badanie  
 Za pomocą narzędzia diagnostyki grafiki, można załadować dokument dziennika grafiki, aby sprawdzić ramek, które zostały przechwycone podczas testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby sprawdzić ramkę w dzienniku grafiki  
  
1.  W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], załadować dziennika grafiki, który zawiera ramkę, która wykazuje Brak modelu. Nowe okno Dokument dziennika grafiki pojawia się w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W górnej części tego okna jest renderowanie danych wyjściowych zaznaczonej ramki. W dolnej części jest **listy ramek**, który będzie wyświetlany jako obraz miniatury każdego przechwyconej ramce.  
  
2.  W **listy ramek**, wybierz obiekt nie ma poprawny wygląd ramki. Obiektu docelowego renderowania jest aktualizowana w celu odzwierciedlenia zaznaczonej ramki. W tym scenariuszu grafiki dziennika dokumentu okno wygląda następująco:  
  
     ![Grafika Rejestruj dokument w programie Visual Studio. ] (media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")  
  
 Po zaznaczeniu ramki demonstrujący problem, można użyć **Historia pikseli grafiki** okno, aby zdiagnozować go. **Historia pikseli grafiki** okno zawiera podstawowych, które może wywrzeć wpływ na określonych pikseli, ich programów do cieniowania i co ich wpływu na obiektu docelowego renderowania były w kolejności chronologicznej.  
  
#### <a name="to-examine-a-pixel"></a>Aby sprawdzić piksel  
  
1.  Otwórz **Historia pikseli grafiki** okna. Na **diagnostyki grafiki** narzędzi wybierz **historii pikseli**.  
  
2.  Wybierz piksel do sprawdzenia. W oknie Dokument dziennika grafiki wybierz jedną z pikseli na obiekt, który jest niepoprawnie pokolorowane:  
  
     ![Wybranie piksel powoduje wyświetlenie informacji o jego historii. ] (media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")  
  
     **Historia pikseli grafiki** okna jest aktualizowana w celu odzwierciedlenia wybranego piksela. W tym scenariuszu **Historia pikseli grafiki** okno wygląda następująco:  
  
     ![Historia pikseli zawiera jedno zdarzenie DrawIndexed. ] (media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")  
  
     Zauważ, że wynik cieniowania pikseli jest całkowicie nieprzezroczyste czarne (0, 0, 0, 1), a **połączenia danych wyjściowych** połączone z tym **Wstecz** kolor pikseli w taki sposób, który **wynik** jest również całkowicie nieprzezroczyste czarny.  
  
 Po zbadać pikseli, który jest niepoprawnie pokolorowane i wykryć, czy dane wyjściowe programu do cieniowania pikseli nie jest oczekiwanym kolorów, można użyć debuger HLSL do badania programu do cieniowania pikseli i dowiedzieć się, co się stało z kolor obiektu. Można użyć debuger HLSL sprawdzać stan HLSL zmienne w czasie wykonywania kroków kodu HLSL i ustaw punkty przerwania, aby zdiagnozować problem.  
  
#### <a name="to-examine-the-pixel-shader"></a>Aby sprawdzić programu do cieniowania pikseli  
  
1.  Rozpocznij debugowanie programu do cieniowania pikseli. W **Historia pikseli grafiki** okna, w obszarze obiektu na pierwotny, obok pozycji **programu do cieniowania pikseli**, wybierz **Rozpocznij debugowanie** przycisku.  
  
2.  W tym scenariuszu ponieważ program do cieniowania pikseli po prostu przekazuje w kolor za pośrednictwem programu do cieniowania wierzchołków jest łatwo sprawdzić, czy program do cieniowania pikseli nie jest źródłem problemu.  
  
3.  Umieść wskaźnik na `input.color`. Zwróć uwagę, że jego wartość wynosi czarne pełni nieprzezroczyste (0, 0, 0, 1).  
  
     ![Element członkowski "color", "danych wejściowych" jest czarny. ] (media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")  
  
     W tym scenariuszu badanie ujawnia nieprawidłowy kolor jest prawdopodobnie wynik do cieniowania wierzchołków, która nie zawiera informacji prawidłowy kolor dla programu do cieniowania pikseli do działania na.  
  
 Po określeniu, czy program do cieniowania wierzchołków prawdopodobnie nie dostarcza potrzebnych informacji do programu do cieniowania pikseli, następnym krokiem jest zbadanie programu do cieniowania wierzchołków.  
  
#### <a name="to-examine-the-vertex-shader"></a>Aby sprawdzić programu do cieniowania wierzchołków  
  
1.  Rozpocznij debugowanie programu do cieniowania wierzchołków. W **Historia pikseli grafiki** okna, w obszarze obiektu na pierwotny, obok pozycji **programu do cieniowania wierzchołków**, wybierz **Rozpocznij debugowanie** przycisku.  
  
2.  Zlokalizuj strukturę wyjściową do cieniowania wierzchołków — jest to dane wejściowe programu do cieniowania pikseli. W tym scenariuszu nazwa ta struktura jest `output`. Badanie kodu programu do cieniowania wierzchołków i zwróć uwagę, że `color` członkiem `output` struktury została jawnie ustawiona na kolor czarny pełni nieprzezroczyste, być może w związku z tym osoby jest debugowanie działań.  
  
3.  Upewnij się, że Członkowskie kolor nigdy nie został skopiowany z strukturze wejściowej. Ponieważ wartość `output.color` jest ustawiona na kolor czarny pełni nieprzezroczyste tuż przed `output` struktury jest zwracany, jest dobrym pomysłem jest upewnij się, że wartość `output` nie został prawidłowo zainicjowany w poprzednim wierszu. Krok za pomocą kodu programu do cieniowania wierzchołków aż do wiersza, który ustawia `output.color` na kolor czarny podczas odtwarzania wartość `output.color`. Zwróć uwagę, że wartość `output.color` nie została zainicjowana, dopóki nie jest ustawiona na kolor czarny. Potwierdza to, że wiersza kodu, który ustawia `output.color` do czarne powinny być zmodyfikowane, a nie usunięte.  
  
     ![Wartość "output.color" jest czarny. ] (media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")  
  
 Po określeniu, czy jest przyczyny tego problemu renderowania, że programu do cieniowania wierzchołków nie zawiera wartości prawidłowy kolor programu do cieniowania pikseli, można użyć tych informacji, aby rozwiązać ten problem. W tym scenariuszu możesz go rozwiązać, zmieniając następujący kod w programu do cieniowania wierzchołków  
  
```  
output.color = float3(0.0f, 0.0f, 0.0f);  
```  
  
 na  
  
```hlsl  
output.color = input.color;  
```  
  
 Ten kod po prostu przekazuje kolor wierzchołka z obiektu wierzchołków nie mają być modyfikowane — bardziej złożonych programów do cieniowania wierzchołków można zmodyfikować kolor przed przekazaniem go za pośrednictwem. Kod programu do cieniowania wierzchołków poprawiony powinien wyglądać następująco:  
  
 ![Kod programu do cieniowania wierzchołków poprawiony. ] (media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")  
  
 Po rozwiązaniu kod skompilować go ponownie i uruchomić aplikację ponownie, aby dowiedzieć się, że rozwiązanie jest problem renderowania.  
  
 ![Obiekt jest odwzorowywany z poprawną kolorów. ] (media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")