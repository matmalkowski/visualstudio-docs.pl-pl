---
title: Wyszukiwanie przecieków pamięci za pomocą biblioteki CRT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d858b6c67893e49b4d4e9ec87c3b20fce56dd7c4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477865"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Wyszukiwanie przecieków pamięci za pomocą biblioteki CRT
Przecieki pamięci, zdefiniowane jako błąd, aby poprawnie zwolnić pamięć, która była przydzielona wcześniej, są najbardziej delikatny i twardych do wykrycia błędów w aplikacji C/C++. Przeciek pamięci może pozostać niezauważone w pierwszej, ale wraz z upływem czasu, przeciek pamięci progresywnego może spowodować objawy zakresu spadek wydajności do awarii po uruchomieniu aplikacji za mało pamięci. Gorsze ulatniający aplikacji, która używa wszystkich dostępną pamięć, może spowodować inna aplikacja awarię, tworzenie pomyłek, które odpowiada aplikacji. Przecieki pamięci nieszkodliwe może być nawet pozornie objawowych innych problemów, które powinno zostać naprawione.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugera i bibliotek C Run-Time (CRT) zapewniają sposób wykrywania i identyfikacji przecieki pamięci.  
  
## <a name="enabling-memory-leak-detection"></a>Włączanie wykrywania przecieków pamięci  
 Funkcje sterty debugowania jest podstawowe narzędzia do wykrywania pamięci to przecieki debugera i biblioteki wykonawcze języka C (CRT).  
  
 Aby włączyć funkcje sterty debugowania, Dołącz poniższe instrukcje w programie:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Dla funkcji CRT działał prawidłowo `#include` instrukcji należy wykonać w kolejności przedstawionej w tym miejscu.  
  
 Tym mapy crtdbg.h `malloc` i [wolnego](/cpp/c-runtime-library/reference/free) funkcji w celu ich wersje debugowania [_malloc_dbg —](/cpp/c-runtime-library/reference/malloc-dbg) i `free`, który śledzi przydzielanie pamięci i cofania alokacji. To mapowanie występuje tylko w przypadku kompilacji do debugowania, które mają `_DEBUG`. Kompilacjami wydania Użyj niestandardowych `malloc` i `free` funkcji.  
  
 `#define` Instrukcji mapuje wersja podstawowa funkcji CRT sterty z odpowiedniej wersji do debugowania. W przypadku pominięcia `#define` instrukcji zrzutu przeciek pamięci będzie mniej szczegółowe.  
  
 Po włączeniu funkcji sterty debugowania przy użyciu tych instrukcji, możesz nawiązać połączenie z `_CrtDumpMemoryLeaks` przed punkt wyjścia aplikacji, aby wyświetlić raport przeciek pamięci, gdy aplikacja jest kończona:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Jeśli aplikacja zawiera wielu wyjść, nie trzeba ręcznie nawiązać połączenie z [_crtdumpmemoryleaks —](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) w każdym punkcie wyjścia. Wywołanie `_CrtSetDbgFlag` na początku aplikacji spowoduje automatyczne wywołanie `_CrtDumpMemoryLeaks` w każdej zamknąć punktu. Należy ustawić pól bitowych dwóch pokazano poniżej:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Domyślnie `_CrtDumpMemoryLeaks` generuje raport przeciek pamięci, aby **debugowania** okienku **dane wyjściowe** okna. Można użyć `_CrtSetReportMode` przekierować raport do innej lokalizacji.  
  
 Jeśli używasz biblioteki biblioteki może zresetować dane wyjściowe do innej lokalizacji. W takim przypadku można ustawić lokalizacja danych wyjściowych do **dane wyjściowe** okna, jak pokazano poniżej:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interpretowanie raportu przeciek pamięci  
 Jeśli aplikacja nie ma zdefiniowanej `_CRTDBG_MAP_ALLOC`, [_crtdumpmemoryleaks —](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) wyświetla raport przeciek pamięci, że wygląda podobnie do następującej:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Jeśli aplikacja definiuje `_CRTDBG_MAP_ALLOC`, raport przeciek pamięci wygląda następująco:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Różnica polega na tym, że drugi raport zawiera nazwę pliku i numer wiersza, w którym najpierw jest przydzielana pamięć ujawnione.  
  
 Określa, czy należy zdefiniować `_CRTDBG_MAP_ALLOC` lub nie, spowoduje raportu przeciek pamięci wyświetlić następujące informacje:  
  
-   Numer alokacji pamięci, która jest `18` w tym przykładzie  
  
-   [Zablokować typu](http://msdn.microsoft.com/en-us/e2f42faf-0687-49e7-aa1f-916038354f97), który jest `normal` w tym przykładzie.  
  
-   Lokalizacji pamięci szesnastkowa, która jest `0x00780E80` w tym przykładzie.  
  
-   Rozmiar bloku, `64 bytes` w tym przykładzie.  
  
-   Pierwszych 16 bajtów danych w bloku, w postaci szesnastkowej.  
  
 Raport przeciek pamięci identyfikuje bloku pamięci jako normalny, klienta lub CRT. A *normalne bloku* zwykłej pamięci przydzielonej przez program. A *bloku klienta* jest specjalnym rodzajem blok pamięci używane przez programy MFC dla obiektów, które wymagają destruktora. MFC `new` operator tworzy normalne bloku lub blok klienta na potrzeby tworzony obiekt. A *bloku CRT* został przydzielony Biblioteka CRT dla tego urządzenia. Biblioteka CRT obsługuje dezalokacji dla tych bloków. W związku z tym jest mało prawdopodobne, zobaczysz je w raporcie przeciek pamięci niewłaściwa chyba, że dany element jest znacznie, na przykład biblioteki CRT jest uszkodzony.  
  
 Istnieją dwa typy bloków pamięci, które nigdy nie są wyświetlane w raportach przeciek pamięci. A *bloku wolnego* pamięci, który został zwolniony. Oznacza to, że jej jest nie przedostają, zgodnie z definicją. *Ignoruj bloku* jest pamięć, która jawnie oznaczone jako Aby wykluczyć go z raportu przeciek pamięci.  
  
 Te techniki pracy pamięci przydzielony przy użyciu standardowych CRT `malloc` funkcji. Jeśli program przydziela pamięć przy użyciu języka C++ `new` operatora, jednak może widoczne są tylko liczby plików i wierszy gdzie implementacji globalnych `operator new` wywołania `_malloc_dbg` w raporcie przeciek pamięci. Ponieważ tego zachowania nie jest bardzo przydatny, można zmienić go do raportu na wiersz zawierający wprowadzone Alokacja za pomocą makra, który wygląda następująco: 
 
```C++  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Teraz można zastąpić `new` operator przy użyciu `DBG_NEW` makra w kodzie. W kompilacjach do debugowania to używane jest przeciążenie globalnych `operator new` pobierającej dodatkowe parametry typ bloku, plików i numer wiersza. To przeciążenie metody `new` wywołania `_malloc_dbg` zarejestrować dodatkowych informacji. Jeśli używasz `DBG_NEW`, przeciek pamięci raporty Pokaż nazwę i numer wiersza, gdzie przydzielone obiekty ujawnione. W kompilacjach detalicznej używa domyślnie `new`. (Nie zaleca się utworzenie makra preprocesora o nazwie `new`, ani żadnych innych słów kluczowych języka.) Oto przykład techniki:  
  
```C++  
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```  
  
Po uruchomieniu tego kodu w debugerze programu Visual Studio, wywołanie `_CrtDumpMemoryLeaks` generuje raport w **dane wyjściowe** okna, która wygląda podobnie do poniższego:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Oznacza to, że ujawnione przydział został w wierszu 20 debug_new.cpp.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Ustawianie punktów przerwania na numer alokacji pamięci  
 Liczba alokacji pamięci informuje, kiedy został przydzielony blok pamięci ujawnione. Blok o liczbie alokacji pamięci 18, na przykład jest 18 blok pamięci przydzielony przy uruchomieniu aplikacji. Raport CRT zlicza wszystkie alokacje blok pamięci podczas uruchamiania. W tym przydziały biblioteki CRT i innych bibliotek, takich jak MFC. W związku z tym blok o liczbie alokacji pamięci 18 nie może być 18 blok pamięci przydzielony w kodzie. Zazwyczaj nie będzie.  
  
 Liczba alokacji umożliwia Ustaw punkt przerwania w alokacji pamięci.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>Aby ustawić punkt przerwania alokacji pamięci przy użyciu okna czujki  
  
1.  Ustaw punkt przerwania w pobliżu uruchomienia aplikacji, a następnie uruchom aplikację.  
  
2.  Gdy aplikacja dzieli się na punkt przerwania, **czujki** okna.  
  
3.  W **czujki** wpisz `_crtBreakAlloc` w w **nazwa** kolumny.  
  
     Jeśli używane są wielowątkowe wersja DLL biblioteki CRT (opcja / / MD), należy uwzględnić w operatorze kontekstu: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4.  Naciśnij klawisz **ZWRACAĆ**.  
  
     Debuger daje w wyniku wywołania i umieszcza wynik w **wartość** kolumny. Ta wartość będzie -1, jeśli nie zdefiniowano żadnych punktów przerwania w alokacji pamięci.  
  
5.  W **wartość** kolumny, zastąp wartość pokazana z liczbą alokacji alokacji pamięci, której chcesz przerwać.  
  
 Po skonfigurowaniu punktu przerwania na liczbę alokacji pamięci można debugować. Należy zachować ostrożność uruchomić program na warunkach jako poprzedniego uruchomienia, aby nie zmieniać kolejności alokacji pamięci. Jeśli program dzieli w alokacji pamięci określona, możesz użyć **stos wywołań** oknami debugera określenie warunków, w których została przydzielona pamięć. Następnie można kontynuować wykonywania, aby sprawdzić, co się dzieje z obiektem i ustalić, dlaczego on jest nie poprawnie cofnąć alokacji.  
  
 Ustawianie punktu przerwania danych dla obiekt może być również przydatne. Aby uzyskać więcej informacji, zobacz [przy użyciu punktów przerwania](../debugger/using-breakpoints.md).  
  
 Można również ustawić alokacji pamięci punktów przerwania w kodzie. Istnieją dwa sposoby wykonania tej czynności:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 lub:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Porównywanie stanów pamięci  
 Innej techniki do lokalizowania przecieki pamięci obejmuje tworzenie migawek stan pamięci aplikacji w punktach klucza. Aby utworzyć migawkę stanu pamięci w danym punkcie w aplikacji, Utwórz **_crtmemstate —** struktury i przekaż go do `_CrtMemCheckpoint` funkcji. Ta funkcja wprowadza w strukturze migawki bieżący stan pamięci:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` wypełnia struktury migawki bieżący stan pamięci.  
  
 Do wyjściowego zawartość **_crtmemstate —** struktury należy przekazać do struktury `_ CrtMemDumpStatistics` funkcji:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` generuje zrzutu pamięci stan, który wygląda następująco:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Aby ustalić, czy w sekcji kodu wystąpił wyciek pamięci, można wykonać migawki stanu pamięci przed i po sekcji i następnie użyć `_ CrtMemDifference` Aby porównać dwa stany:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` porównuje stanów pamięci `s1` i `s2` i zwraca wynik (`s3`) czyli różnica `s1` i `s2`.  
  
 Wyszukiwanie przecieków pamięci jeden technika rozpoczyna się przez umieszczenie `_CrtMemCheckpoint` wywołania na początku i na końcu aplikację, następnie za pomocą `_CrtMemDifference` porównanie wyników. Jeśli `_CrtMemDifference` pokazuje przeciek pamięci, możesz dodać więcej `_CrtMemCheckpoint` wywołania do dzielenia programie za pomocą wyszukiwanie binarne, dopóki nie mają odizolowane źródło systemu.  
  
## <a name="false-positives"></a>Fałszywych alarmów  
 W niektórych przypadkach `_CrtDumpMemoryLeaks` można podać fałszywych informacji przecieków pamięci. Taka sytuacja może wystąpić, jeśli korzystasz z biblioteki, która oznacza wewnętrzny alokacji jako _NORMAL_BLOCKs zamiast `_CRT_BLOCK`s lub `_CLIENT_BLOCK`s. W takim przypadku `_CrtDumpMemoryLeaks` nie może odróżnić alokacji użytkownika i Wewnętrzna biblioteka alokacji. Jeśli globalne destruktory dla alokacji biblioteki Uruchom od momentu, gdy wywołanie `_CrtDumpMemoryLeaks`, każdej operacji przydzielenia pamięci wewnętrznej biblioteki został zgłoszony jako przeciek pamięci. Starsze wersje standardowa biblioteka szablonów, starszych niż program Visual Studio .NET, spowodowane `_CrtDumpMemoryLeaks` zgłoszenia takie false alarmów, ale został rozwiązany w najnowszych wersjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Szczegóły dotyczące sterty debugowania CRT](../debugger/crt-debug-heap-details.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
