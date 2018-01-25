---
title: "Rozwiązywanie problemów z punktów przerwania w debugerze programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/23/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "0"
author: carpediemma
ms.author: emrou
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a59a5448cb9ceb9aa4ac5578e9234c1a9972a15a
ms.sourcegitcommit: 062795f922e7b59fe00d3d95a01a9a8a28840017
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2018
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Rozwiązywanie problemów z punktów przerwania w debugerze programu Visual Studio

## <a name="breakpoint-warnings"></a>Ostrzeżenia punktu przerwania

Podczas debugowania, punkt przerwania ma dwa możliwe stany wizualne: stałe czerwone kółko i pusty (biały wypełnione) okręgu. Debuger jest w stanie pomyślnie Ustaw punkt przerwania w procesie docelowym, pozostanie stałe czerwonym kółku. Jeśli punkt przerwania jest ono w pusty okrąg, punkt przerwania jest wyłączona lub ostrzeżenie podczas próby ustawienia punktu przerwania. Aby określić różnicę, umieść kursor nad punkt przerwania i sprawdzić, czy jest ostrzeżenie.

Następujące dwie sekcje opisują poświęcone ostrzeżenia i sposobu ich rozwiązania. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Nie załadowano symboli dla tego dokumentu" 

Przejdź do **modułów** okna (**debugowania** > **Windows** > **modułów**) i sprawdź, czy modułu załadowane.  
* Sprawdź, czy załadowaniu modułu **stan Symbol** kolumny, aby zobaczyć, czy załadowano symbole. 
  * Jeśli nie załadowano symboli, sprawdź stan symbolu, aby zdiagnozować problem. Z menu kontekstowego na moduł **modułów** okna, kliknij przycisk **informacji o symbolach obciążenia...**  aby zobaczyć, których debuger wyszukiwanego, i spróbuj załadować symbole. Aby uzyskać więcej informacji na temat ładowania symboli, zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Jeśli, czy załadowano symbole, oznacza to, pliku PDB nie zawiera informacji o plikach źródłowych. Poniżej przedstawiono kilka możliwych przyczyn: 
    * Jeśli niedawno dodano plików źródłowych, upewnij się, jest ładowany zaktualizowanej wersji modułu.  
    * Można utworzyć przy użyciu pliki PDB **/pdbstripped** — opcja konsolidatora. Pliki PDB nie zawierają informacji o pliku źródłowym. Upewnij się, że korzystasz z pełnego pliku PDB i nie pozbawionego włókien pliku PDB.  
    * Plik PDB częściowo jest uszkodzony. Spróbuj usunąć plik i wykonywanie czystej kompilacji modułu, aby sprawdzić, czy ten został rozwiązany. 

* Jeśli modułu nie jest załadowane, sprawdź następujące polecenie, aby znaleźć przyczynę: 
  * Upewnij się, czy debugowany proces prawo. 
  * Sprawdź, czy debugujesz rodzaj kodu. Można ustalić, jakiego typu kodu debuger jest skonfigurowany do debugowania w **procesów** okna (**debugowania** > **Windows**  >  **Procesów**). Na przykład, jeśli chcesz debugować kod w języku C#, upewnij się, że debuger jest skonfigurowany dla odpowiedniego typu .NET Framework (na przykład zarządzane (v4\*) i zarządzane (v2\*/v3\*) i zarządzane (środowisko CoreCLR)). 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… Bieżący kod źródłowy różni się od wersji skompilowanej w..." 

Jeśli plik źródłowy zmienił i źródła nie jest już zgodny z kodem, debugowana, debuger będzie nie domyślnie punktów przerwania w kodzie. Zazwyczaj ten problem się stanie, jeśli plik źródłowy jest zmieniony, ale nie został ponownie skompilowany kod źródłowy. Aby rozwiązać ten problem, skompiluj ponownie projekt. Jeśli system kompilacji sądzi, że projekt jest już aktualne, nawet jeśli nie jest, możesz wymusić systemu projektu albo zapisując plik źródłowy odbudować lub przez czyszczenie projektu kompilować wynik przed kompilacją. 

W rzadkich przypadkach można debugować bez pasującego kodu źródłowego. To prowadzić do mylące obsługi debugowania, dlatego należy upewnić się, że jest to, jaki sposób chcesz kontynuować.  

Aby wyłączyć kontrole bezpieczeństwa, wykonaj jedną z następujących czynności: 
* Aby zmodyfikować pojedynczy punkt przerwania, umieść kursor nad ikoną punktu przerwania w edytorze i kliknij ikonę ustawień (koło zębate). Okno podglądu zostanie dodany do edytora. W górnej części okna podglądu jest hiperłącze, które wskazuje lokalizację punktu przerwania. Kliknij hiperłącze, aby możliwa jego modyfikacja lokalizacji punktu przerwania i sprawdź **Zezwalaj kod źródłowy różni się od oryginału**.
* Aby zmodyfikować to ustawienie dla wszystkich punktów przerwania, przejdź do **debugowania** > **opcje i ustawienia**. Na **debugowanie/ogólne** wyczyść **wymaga plików źródłowych odpowiadających dokładnie oryginalnej wersji** opcji. Upewnij się ponownie włączyć tę opcję, po zakończeniu debugowania. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Punkt przerwania został pomyślnie ustawiony (bez ostrzeżenia), ale nie został trafiony 

Ta sekcja zawiera informacje o rozwiązywaniu problemów, gdy debuger nie są wyświetlane ostrzeżenia — punkt przerwania jest stałe czerwone kółko podczas debugowania aktywnie, ale nie jest trafienia punktu przerwania. 

Oto kilka rzeczy, aby sprawdzić: 
1. Jeśli kod jest uruchomiony w procesie więcej niż jeden lub więcej niż jeden komputer, upewnij się, że debugowania procesu prawej lub komputera.  
2. Upewnij się, że kod jest uruchomiony. Jeden łatwy sposób na sprawdzenie to polega na dodaniu wywołanie `System.Diagnostics.Debugger.Break` (C# /VB) lub `__debugbreak` (C++) do wiersza kodu, w którym chcesz ustawić punkt przerwania, a następnie ponownie skompiluj projekt. 
3. Przypadku debugowania zoptymalizowanego kodu, upewnij się, że funkcja, gdy punkt przerwania jest ustawiony nie jest wbudowana w innej funkcji. `Debugger.Break` Test opisany w poprzednim wyboru mogą służyć do testowania tej funkcji oraz. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Po usunięciu punktu przerwania, ale można kontynuować trafień go podczas uruchamiania debugowania ponownie 

Usunięcie punktu przerwania podczas debugowania mogą trafiony punkt przerwania ponownie przy następnym uruchomieniu debugowania. Aby zatrzymać naciśnięcie tego punktu przerwania, sprawdź, czy wszystkie wystąpienia punktu przerwania są usuwane z **punktów przerwania** okna.  
