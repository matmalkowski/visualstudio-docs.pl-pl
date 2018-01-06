---
title: Debuger programu do cieniowania HLSL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9c1aeeb2da6817375e0327dba385037dccdc58cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="hlsl-shader-debugger"></a>Debuger programu do cieniowania HLSL
Debuger HLSL w analizatora grafiki programu Visual Studio pomaga zrozumieć sposób działania kodu programu do cieniowania HLSL w rzeczywistych warunkach aplikacji.  
  
 To jest debuger języka HLSL:  
  
 ![Debugowanie przy użyciu HLSL oglądać i okna stosu wywołań. ] (media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx_diag_demo_hlsl_debugger_orientation")  
  
## <a name="understanding-the-hlsl-debugger"></a>Opis debugera HLSL  
 Debuger HLSL ułatwia lepsze poznanie problemów, które występują w kodzie modułu cieniującego. Debugowanie kodu HLSL w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podobny do debugowania kodu, który jest zapisany w innych językach — na przykład, C++, C# lub Visual Basic. Można zbadać zawartość zmiennych, ustawić punkty przerwania, wykonywać kod krokowo i przechodzić przez stos wywołań, podobnie jak podczas debugowania innych języków.  
  
 Jednak ponieważ GPU osiągnięcia wysokiej wydajności, uruchamiając kod programu do cieniowania na setki wątków jednocześnie, debuger HLSL jest przeznaczona do pracy oraz inne narzędzia Analizator grafiki do prezentowania wszystkie te informacje w sposób, który pomaga analizować go. Analizator grafiki odtwarza ramki przechwycone przy użyciu informacji, który został zapisany w dzienniku grafiki; Debuger HLSL nie monitoruje wykonywania procesora GPU w czasie rzeczywistym, podczas wykonywania kodu programu do cieniowania. Ponieważ dziennika grafiki zawiera wystarczających informacji do odtworzenia dowolną część danych wyjściowych, a ponieważ zapewnia analizy grafiki narzędzia, które mogą ułatwić wskazanie pikseli dokładne i zdarzeń, gdy wystąpi błąd, debuger HLSL zawiera tylko do symulowania dokładne programu do cieniowania Wątek, który chcesz. Oznacza to, że działanie programu cieniującego może być symulowane w procesorze CPU, gdzie działanie jego wewnętrznych mechanizmów jest w pełni widoczne. Dzięki temu debugger HLSL otrzymuje debugowanie podobne do procesora.  
  
 Jednak debuger języka HLSL jest obecnie ograniczony pod następującymi względami:  
  
-   Debuger HLSL nie obsługuje edit-and-continue, ale można zmienić z programów do cieniowania i ponownie wygenerować ramki, aby wyświetlić wyniki.  
  
-   Nie jest możliwe debugowanie aplikacji i jej kodu cieniowania w tym samym czasie. Można jednak używać ich zamiennie.  
  
-   W oknie czujki można dodać zmienne i rejestry, ale wyrażenia nie są obsługiwane.  
  
 Niemniej jednak debuger języka HLSL oferuje lepsze, przypominające zachowanie znane z procesorów CPU debugowanie, niż byłoby to możliwe w innym przypadku.  
  
## <a name="hlsl-shader-edit--apply"></a>Tryb Edytuj i zastosować cieniowania HLSL  
 Debuger programu do cieniowania HLSL nie obsługuje Edytuj i Kontynuuj w taki sam sposób, który wykonuje debuger Procesora, ponieważ model wykonywania procesora GPU nie zezwala na stan programu do cieniowania można cofnąć. Zamiast tego debuger HLSL obsługuje & Zastosuj, dzięki czemu można edytować HLSL pliki źródłowe, a następnie wybierz pozycję Edytuj **Zastosuj** można ponownie wygenerować ramki, aby zobaczyć efekt zmian. Kod modyfikacji programu do cieniowania jest przechowywane w osobnym pliku w celu zachowania spójności oryginalnego pliku źródłowego HLSL projektu, ale po zakończeniu zmiany można **skopiować do...**  skopiować zmiany do projektu. Za pomocą tej funkcji, można szybko iterację programu do cieniowania kod, który zawiera błędy i wyeliminować rebuild kosztowne i etapów przechwytywania z Twojej HLSL debugowanie przepływu pracy.  
  
## <a name="hlsl-disassembly"></a>Dezasemblacja HLSL  
 Debuger programu do cieniowania HLSL zawiera listę zestawów programu do cieniowania HLSL po prawej stronie przykładowy kod źródłowy HLSL.  
  
## <a name="debugging-hlsl-code"></a>Debugowanie kodu HLSL  
 Debuger HLSL dostępne w oknie etapy potoku lub z historii pikseli.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>Aby uruchomić debuger HLSL z okna Etapy potoku grafiki  
  
1.  W **etapy potoku grafiki** okna, zlokalizuj skojarzoną z programu do cieniowania, który chcesz debugować etap potoku.  
  
2.  Pod tytułem etap potoku, wybierz **Rozpocznij debugowanie**, która jest wyświetlana jako małych zieloną strzałkę.  
  
    > [!NOTE]
    >  Ten punkt wejścia do debugera HLSL debuguje tylko pierwszy wątek modułu cieniującego dla odpowiedniego etapu, czyli pierwszy wierzchołek lub piksel, który jest przetwarzany. Historia pikseli umożliwia dostęp do innych wątków etapy te programu do cieniowania.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>Aby uruchomić debuger HLSL z okna Historia pikseli grafiki  
  
1.  W **Historia pikseli grafiki** okna, rozwiń węzeł skojarzoną z programu do cieniowania, który chcesz debugować wywołanie rysowania. Każde wywołanie rysowania może odpowiadać wielu obiektom pierwotnym.  
  
2.  W szczegółach wywołania rysowania, rozwiń prymityw, którego wynikowy kolor sugeruje błąd w kodzie modułu cieniującego. Jeśli wiele prymitywów sugeruje błąd, wybierz pierwszy prymityw, który go sugeruje, tak aby uniknąć nagromadzenia błędów, które mogą utrudnić diagnozę problemu.  
  
3.  W pierwotnym uzyskać szczegółowe informacje, wybierz opcję debugowania **programu do cieniowania wierzchołków** lub **programu do cieniowania pikseli**. Debuguj program do cieniowania wierzchołków, gdy istnieje podejrzenie, że program do cieniowania pikseli jest poprawny, ale generuje niepoprawny kolor, ponieważ program do cieniowania wierzchołków przekazuje mu nieprawidłowe stałe. W przeciwnym razie debuguj program do cieniowania pikseli.  
  
     Po prawej stronie wybranego programu do cieniowania, wybierz **Rozpocznij debugowanie**, która jest wyświetlana jako małych zieloną strzałkę.  
  
    > [!NOTE]
    >  Ten punkt wejścia do debugera HLSL debuguje program cieniowania pikseli, który odpowiada wybranemu wywołaniu rysowania, prymitywowi i pikselowi lub wątkom cieniowania wierzchołków, których wyniki są interpolowane przez wywołanie wybranego rysowania, prymitywu i piksela. W przypadku programów do cieniowania wierzchołków można dodatkowo dostosować punkt wejścia do konkretnego przez rozwijanie szczegółów modułu cieniującego wierzchołek.  
  
 Przykłady o sposobie używania debuger HLSL do debugowania cieniowania błędów można znaleźć [przykłady](graphics-diagnostics-examples.md) lub wskazówki połączony w sekcji Zobacz też.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Wskazówki: Debugowanie błędów renderowania spowodowanych cieniowaniem](walkthrough-debugging-rendering-errors-due-to-shading.md)   
 [Przewodnik: używanie diagnostyki grafiki do debugowania cieniowania obliczenia](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)