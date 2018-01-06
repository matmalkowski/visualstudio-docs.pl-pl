---
title: "Szczegóły dotyczące sterty debugowania CRT | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cc7b945a8c53d290f573eac4565f2240ec7a2d7b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="crt-debug-heap-details"></a>Szczegóły dotyczące sterty debugowania CRT
Ten temat zawiera szczegółowe przyjrzeć się sterty debugowania CRT.  
  
##  <a name="BKMK_Contents"></a>Zawartość  
 [Znajdź przepełnienia buforu ze stertą debugowania](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Typy bloków w stercie debugowania](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Sprawdź, czy sterty integralności i przecieki pamięci](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Skonfiguruj stercie debugowania](#BKMK_Configure_the_debug_heap)  
  
 [Nowy, Usuń i _CLIENT_BLOCKs w języku C++ sterta debugowania](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Funkcje raportowania stanu sterty](#BKMK_Heap_State_Reporting_Functions)  
  
 [Żądań alokacji stosu śledzenia](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a>Znajdź przepełnienia buforu ze stertą debugowania  
 Są dwa najczęstszych i intractable problemy napotykane przez programistów zastępowanie koniec przydzielonego buforu i przecieki pamięci (nie można zwolnić alokacji po nie są już potrzebne). Sterta debugowania udostępnia zaawansowane narzędzia do rozwiązywania problemów z alokacją pamięci tego rodzaju.  
  
 Debugowania wersji funkcje stosu wywołań wersji standard lub podstawowej używanych w wersji kompilacji. W przypadku żądania blok pamięci, menedżera sterty debugowania przydziela z podstawowej sterty nieco większy blok pamięci niż żądana i zwraca wskaźnik do Twojej części tego bloku. Załóżmy na przykład, aplikacja zawiera wywołanie: `malloc( 10 )`. W kompilacji wydania [— funkcja malloc](/cpp/c-runtime-library/reference/malloc) spowodowałoby wywołanie procedury alokacji sterty podstawowej żąda alokacji 10 bajtów. Kompilacji debugowanej, jednak `malloc` spowodowałoby wywołanie [_malloc_dbg —](/cpp/c-runtime-library/reference/malloc-dbg), który może wywoływać procedury alokacji sterty podstawowej żąda alokacji 10 bajtów plus około 36 bajtów pamięci dodatkowe. Wszystkie wynikowy bloki pamięci w stosie debugowania są połączone w jednym listy połączonej, uporządkowanych według kiedy zostały przydzielone.  
  
 Dodatkowej pamięci przydzielonej przez procedury sterty debugowania jest używana do informacji księgowości, dla wskaźników, że bloki pamięci link Debuguj razem i dla małych buforów po obu stronach dane, aby przechwycić zastępuje przydzielonego obszaru.  
  
 Struktura nagłówka bloku używany do przechowywania informacji księgowości sterty debugowania jest obecnie zadeklarowana w następujący sposób w DBGINT. Plik nagłówka H:  
  
```  
typedef struct _CrtMemBlockHeader  
{  
// Pointer to the block allocated just before this one:  
    struct _CrtMemBlockHeader *pBlockHeaderNext;  
// Pointer to the block allocated just after this one:  
    struct _CrtMemBlockHeader *pBlockHeaderPrev;  
    char *szFileName;    // File name  
    int nLine;           // Line number  
    size_t nDataSize;    // Size of user block  
    int nBlockUse;       // Type of block  
    long lRequest;       // Allocation number  
// Buffer just before (lower than) the user's memory:  
    unsigned char gap[nNoMansLandSize];  
} _CrtMemBlockHeader;  
  
/* In an actual memory block in the debug heap,  
 * this structure is followed by:  
 *   unsigned char data[nDataSize];  
 *   unsigned char anotherGap[nNoMansLandSize];  
 */  
```  
  
 `NoMansLand` Buforów po obu stronach obszaru danych użytkownika w bloku są obecnie 4 bajty rozmiaru i wypełniane znane bajt, używane przez procedury sterty debugowania, aby zweryfikować, że limity bloku pamięci użytkownika nie został zastąpiony. Sterty debugowania wprowadza również nowe bloki pamięci o znanej wartości. W przypadku wybrania zachować zwolnionych bloków w połączonej listy sterty, jak wyjaśniono poniżej, znanej wartości te bloki zwolnionych również są wypełnione. Obecnie wartości rzeczywistych bajtów, używane są następujące:  
  
 NoMansLand (0xFD)  
 Bufory "NoMansLand" po obu stronach pamięci używane przez aplikacje są obecnie wypełnione 0xFD.  
  
 Bloki zwolnionych (0xDD)  
 Bloki zwolnionych przechowywane nieużywane w stercie debugowania na połączone listy podczas `_CRTDBG_DELAY_FREE_MEM_DF` flagę obecnie wypełnione 0xDD.  
  
 Nowe obiekty (0xCD)  
 Nowe obiekty są wypełnione 0xCD, gdy są przydzielone.  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop")  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a>Typy bloków w stercie debugowania  
 Każdy blok pamięci w stosie debugowania jest przypisany do jednego z pięciu typów alokacji. Te typy są śledzone i podać inaczej w celu wykrywania przecieków i raportowanie stanu. Można określić typ bloku przydzielając go przy użyciu bezpośrednie wywołania do jednej z funkcji alokacji sterty debugowania, takich jak [_malloc_dbg —](/cpp/c-runtime-library/reference/malloc-dbg). Pięć typów bloki pamięci w stosie debugowania (w **nBlockUse** członkiem **_crtmemblockheader —** struktury) są następujące:  
  
 **_NORMAL_BLOCK —**  
 Wywołanie [— funkcja malloc](/cpp/c-runtime-library/reference/malloc) lub [calloc —](/cpp/c-runtime-library/reference/calloc) tworzy blok normalnego. Jeśli zamierzasz używać tylko normalne bloków, a nie potrzebują bloki klienta, można zdefiniować [_crtdbg_map_alloc —](/cpp/c-runtime-library/crtdbg-map-alloc), co powoduje, że wszystkie Alokacja stosu wywołań można mapować na ich odpowiedniki debugowania w kompilacjach debugowania. Pozwoli to nazwy i wiersz numer informacje dotyczące każdego wywołania alokacji mają być przechowywane w odpowiedni nagłówek bloku.  
  
 `_CRT_BLOCK`  
 Bloki pamięci przydzielonej wewnętrznie przez wiele funkcji biblioteki wykonawczej są oznaczone jako CRT bloków, mogą być obsługiwane oddzielnie. W związku z tym wyciek wykrywania i inne operacje nie wpływa to przez nich. Alokacji nigdy nie musi przydzielić, ponowne przydzielenie lub zwolnij bloku CRT typu.  
  
 `_CLIENT_BLOCK`  
 Aplikację można śledzić specjalne określonej grupy alokacji na potrzeby debugowania przydzielając je jako tego typu blok pamięci, za pomocą jawnego wywołania funkcji sterty debugowania. MFC, na przykład wszystkie przydziela **CObject — obiekty** jako bloki klienta; inne aplikacje mogą przechowywać obiekty różnych pamięci w bloki klienta. Można również określić podtypów bloki klienta osiągnąć większy poziom szczegółowości śledzenia. Określanie podtypów bloki klienta, przesunięcie numer przy 16 bitów w lewo i `OR` za pomocą `_CLIENT_BLOCK`. Na przykład:  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 Funkcji dostarczonych przez klienta punktu zaczepienia dla zrzucanie obiekty przechowywane w blokach klienta można zainstalować przy użyciu [_crtsetdumpclient —](/cpp/c-runtime-library/reference/crtsetdumpclient), a następnie zostanie wywołany, gdy blok klienta jest utworzyć zrzutu przez funkcję debugowania. Ponadto [_crtdoforallclientobjects —](/cpp/c-runtime-library/reference/crtdoforallclientobjects) może służyć do wywoływania funkcji danego dostarczone przez aplikację dla każdego bloku klienta w stercie debugowania.  
  
 **_FREE_BLOCK —**  
 Zwykle bloków, które są zwalniane zostaną usunięte z listy. Aby sprawdzić, czy zwolnienie pamięci jest nadal nie jest zapisywana lub aby zasymulować niedobór pamięci, użytkownik może zachować zwolnionych bloków w połączonej listy oznaczone jako wolne i podać wartość bajtu znane (obecnie 0xDD).  
  
 **_IGNORE_BLOCK —**  
 Istnieje możliwość wyłączyć operacji sterty debugowania w danym okresie czasu. W tym czasie bloki pamięci pozostają na liście, ale są oznaczone jako Ignoruj bloków.  
  
 Do określenia typu i podtypu bloku, użyj funkcji [_crtreportblocktype —](/cpp/c-runtime-library/reference/crtreportblocktype) i makra **_block_type —** i **_block_subtype —**. Makra są zdefiniowane w następujący sposób (w crtdbg.h):  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a>Sprawdź, czy sterty integralności i przecieki pamięci  
 Funkcje sterty debugowania musi być dostępny z w kodzie. W poniższej sekcji opisano niektóre funkcje i sposobu ich używania.  
  
 `_CrtCheckMemory`  
 Można używać wywołania [_crtcheckmemory —](/cpp/c-runtime-library/reference/crtcheckmemory), na przykład, aby sprawdzić spójność sterty w dowolnym momencie. Ta funkcja sprawdza każdy blok pamięci w stosie, sprawdza, czy informacje o nagłówku bloku pamięci jest nieprawidłowa i potwierdza, że bufor nie zostały zmodyfikowane.  
  
 `_CrtSetDbgFlag`  
 Można kontrolować sposób sterty debugowania przechowuje informacje o alokacji używających flaga wewnętrzna [_crtdbgflag —](/cpp/c-runtime-library/crtdbgflag), który może odczytywać i ustawić za pomocą [_crtsetdbgflag —](/cpp/c-runtime-library/reference/crtsetdbgflag) funkcji. Zmieniając tę flagę można nakazać sterty debugowania, sprawdź przecieki pamięci, gdy program zamyka i zgłoś wszelkie przecieki, które są wykrywane. Podobnie można określić, że bloki zwolnionych pamięci nie można usunąć z listy połączonej, aby symulować sytuacjach ilości pamięci. Po zaznaczeniu tej opcji sterty te zwolnionych bloki są kontrolowane w całości, aby upewnić się, że nie zostały w naruszonych.  
  
 **_Crtdbgflag —** flagi zawiera następujące pola bitowego:  
  
|Pole bitowe|Domyślny<br /><br /> value|Opis|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF —**|On|Powoduje włączenie debugowania alokacji. Jeśli ten bit jest wyłączony, pozostają alokacji połączonych ze sobą, ale jest ich typ bloku **_ignore_block —**.|  
|**_CRTDBG_DELAY_FREE_MEM_DF —**|Off|Zapobiega pamięci faktycznie zwalniana, podobnie jak w przypadku symulacji ilość pamięci jest mała. Po włączeniu tego bit zwolnionych bloki są przechowywane w stercie debugowania listy połączonej, ale nie została oznaczona jako **_free_block —** i wypełnione specjalne bajt.|  
|**_CRTDBG_CHECK_ALWAYS_DF —**|Off|Powoduje, że **_crtcheckmemory —** przy każdej alokacji i cofania alokacji. Spowalnia wykonywania, ale szybko przechwytuje błędy.|  
|**_CRTDBG_CHECK_CRT_DF —**|Off|Powoduje, że bloki oznaczona jako typu **_crt_block —** mają zostać uwzględnione w operacji wykrywania przecieków i stan różnicy. Jeśli ten bit jest wyłączona, pamięć używana wewnętrznie przez biblioteki wykonawczej jest ignorowany w takich operacjach.|  
|**_CRTDBG_LEAK_CHECK_DF —**|Off|Powoduje, że sprawdzanie przeciek wykonywanych przy zamykaniu program za pomocą wywołania **_crtdumpmemoryleaks —**. Raport o błędzie jest generowany, jeśli aplikacja nie powiodło się zwolnić pamięć, która ona przydzielone.|  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a>Skonfiguruj stercie debugowania  
 Wszystkie wywołania funkcji sterty, takich jak `malloc`, `free`, `calloc`, `realloc`, `new`, i `delete` rozwiązania do debugowania wersje tych funkcji, które działają w stercie debugowania. Po zwolnieniu blok pamięci sterty debugowania automatycznie sprawdza spójność buforów po obu stronach obszaru przydzielone i wystawia raportu o błędach, jeśli przeprowadzono zastępowanie.  
  
 **Aby użyć stercie debugowania**  
  
-   Łącze do kompilacji debugowania aplikacji z wersja biblioteki wykonawczej języka C do debugowania.  
  
 **Aby zmienić jeden lub więcej pól bitowych _crtdbgflag — i utworzyć nowy stan flagi**  
  
1.  Wywołania `_CrtSetDbgFlag` z `newFlag` ustawiona `_CRTDBG_REPORT_FLAG` (Aby uzyskać bieżącą `_crtDbgFlag` stanu) i przechowywać zwrócona wartość w zmiennej tymczasowej.  
  
2.  Włącz wszystkie bity przez `OR`- ne (bitowe &#124; symbol) zmiennej tymczasowej z odpowiedniego masek bitowych (reprezentowane przez stałe manifestu w kodzie aplikacji).  
  
3.  Wyłącz usługi bits przez `AND`- ne (bitowe & symbol) zmienna o `NOT` (bitowe ~ symbolu) z odpowiednią masek bitowych.  
  
4.  Wywołanie `_CrtSetDbgFlag` z `newFlag` parametr ustawiony na wartość przechowywana w zmiennej tymczasowej, aby utworzyć nowy stan dla `_crtDbgFlag`.  
  
 Na przykład następujące wiersze kodu Włącz przeciek automatycznego wykrywania i wyłączyć sprawdzanie bloków typu `_CRT_BLOCK`:  
  
```  
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a>Nowy, Usuń i _CLIENT_BLOCKs w języku C++ sterta debugowania  
 Wersje biblioteki wykonawczej języka C do debugowania zawierają debugowania wersji języka C++ `new` i `delete` operatorów. Jeśli używasz `_CLIENT_BLOCK` typ alokacji, należy wywołać wersja do debugowania z `new` operator bezpośrednio lub tworzenia makr, które zastępują `new` operatora w trybie debugowania, jak pokazano w poniższym przykładzie:  
  
```  
/* MyDbgNew.h  
 Defines global operator new to allocate from  
 client blocks  
*/  
  
#ifdef _DEBUG  
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)  
#else  
   #define DEBUG_CLIENTBLOCK  
#endif // _DEBUG  
  
/* MyApp.cpp  
        Use a default workspace for a Console Application to  
 *      build a Debug version of this code  
*/  
  
#include "crtdbg.h"  
#include "mydbgnew.h"  
  
#ifdef _DEBUG  
#define new DEBUG_CLIENTBLOCK  
#endif  
  
int main( )   {  
    char *p1;  
    p1 =  new char[40];  
    _CrtMemDumpAllObjectsSince( NULL );  
}  
```  
  
 Wersja debugowania `delete` operator współpracuje z bloku wszystkich typów, a nie wymaga żadnych zmian w programie podczas kompilowania wersji.  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a>Funkcje raportowania stanu sterty  
 **_Crtmemstate —**  
  
 Aby przechwycić migawkę podsumowania stanu sterty w danym momencie, użyj _crtmemstate — struktury zdefiniowane w CRTDBG. H:  
  
```  
typedef struct _CrtMemState  
{  
    // Pointer to the most recently allocated block:  
    struct _CrtMemBlockHeader * pBlockHeader;  
    // A counter for each of the 5 types of block:  
    size_t lCounts[_MAX_BLOCKS];  
    // Total bytes allocated in each block type:  
    size_t lSizes[_MAX_BLOCKS];  
    // The most bytes allocated at a time up to now:  
    size_t lHighWaterCount;  
    // The total bytes allocated at present:  
    size_t lTotalCount;  
} _CrtMemState;  
```  
  
 Ta struktura zapisuje wskaźnik pierwszy blok (najbardziej ostatnio przydzielone) w stercie debugowania listy połączonej. Następnie, w dwie tablice, rejestruje zablokować ile każdego rodzaju pamięci (_normal_block —, `_CLIENT_BLOCK`, _free_block —, itd.) są na liście i liczba bajtów przydzielonych w każdym typ bloku. Na koniec rejestruje największa liczba bajtów przydzielonych w stercie jako całości do tego punktu, a liczba bajtów aktualnego przydziału.  
  
 **Inne funkcje raportowania CRT**  
  
 Następujące funkcje raport stanu i zawartość sterty i skorzystaj z informacji w celu ułatwienia wykrycia przecieki pamięci i innych problemów.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Zapisuje migawkę sterty w **_crtmemstate —** struktury dostarczone przez aplikację.|  
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|Porównuje dwie struktury stanu pamięci, zapisuje różnica między nimi w strukturze trzeci stan i zwraca wartość PRAWDA, jeśli dwa stany są różne.|  
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Zrzuty danego **_crtmemstate —** struktury. Struktura może zawierać migawkę stanu sterty debugowania w danym momencie lub różnicę między dwiema migawkami.|  
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Zrzuty informacji na temat wszystkich obiektów przydzielonych od danego migawki sterty lub po rozpoczęciu wykonywania. Za każdym razem, gdy jego zrzuty **_client_block —** bloku, wywołuje funkcję punktu zaczepienia dostarczone przez aplikację, jeśli jeden został zainstalowany przy użyciu **_crtsetdumpclient —**.|  
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Określa, czy wszystkie pamięci przecieków wystąpił od momentu rozpoczęcia wykonywania programu, a jeśli tak, zrzuty wszystkie przydzielone obiekty. Za każdym razem, gdy **_crtdumpmemoryleaks —** zrzuty **_client_block —** bloku, wywołuje funkcję punktu zaczepienia dostarczone przez aplikację, jeśli jeden został zainstalowany przy użyciu **_crtsetdumpclient —**.|  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a>Żądań alokacji stosu śledzenia  
 Chociaż trafić źródło pliku nazwę i numer wiersza w której wykonuje assert lub makra raportowania jest często bardzo przydatne podczas lokalizowania przyczynę problemu, nie jest taka sama jak mogą być spełnione funkcji alokacji sterty. Gdy makra można wstawiać w wielu punktach odpowiednie drzewo logikę aplikacji, w specjalnej procedury, która jest wywoływana z wielu różnych miejscach w wielu różnych momentach jest często stosie alokacji. Pytanie jest zwykle nie jakie wierszy kodu możliwe zły alokacji, ale raczej jedną z tysiącami alokacji wprowadzone przez wiersza kodu został zły i dlaczego.  
  
 **Numery żądań alokacji unikatowy i _crtbreakalloc —**  
  
 Najprostszym sposobem, aby zidentyfikować połączenia alokacji sterty określonych, który został zły ma korzystać z alokacji unikatowy numer żądania skojarzony z każdy blok w stercie debugowania. Gdy informacje o bloku zostaje zgłoszone przez jedną z funkcji zrzutu, ta liczba żądań alokacji jest ujęta w nawiasy klamrowe (na przykład "{36}").  
  
 Po sprawdzeniu, liczba żądań alokacji nieprawidłowo przydzielony blok, można przekazać to do [_crtsetbreakalloc —](/cpp/c-runtime-library/reference/crtsetbreakalloc) można utworzyć punktu przerwania. Wykonanie zostanie przerwana przed przydzielania bloku i można cofnąć w celu określenia, jakie procedury się odpowiedzialny za nieprawidłowe wywołanie. Aby uniknąć ponownej kompilacji, można wykonywać samo w debugerze przez ustawienie **_crtbreakalloc —** liczby żądań alokacji planuje się.  
  
 **Tworzenie wersji debugowania z procedury alokacji**  
  
 Nieco bardziej skomplikowane podejście jest utworzenie wersje własnych procedur alokacji, porównywalna do debugowania **_dbg** wersji [stercie funkcji alokacji](../debugger/debug-versions-of-heap-allocation-functions.md). Można następnie przekazać plik źródłowy i wiersza argumentów za pośrednictwem do podstawowej procedury alokacji sterty i natychmiast będzie można zobaczyć, skąd pochodzi zły alokacji.  
  
 Na przykład załóżmy, że aplikacja zawiera często używane procedury podobny do następującego:  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 W pliku nagłówka można dodać kod, takie jak następujące:  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 Następnie można zmienić alokację w Twojej procedury tworzenie rekordów w następujący sposób:  
  
```  
int addNewRecord(struct RecStruct *prevRecord,  
                int recType, int recAccess  
#ifdef _DEBUG  
               , const char *srcFile, int srcLine  
#endif  
    )  
{  
    /* ... code omitted through actual allocation ... */  
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,  
            srcFile, scrLine)) == NULL)  
    /* ... rest of routine omitted too ... */  
}  
```  
  
 Teraz źródło pliku nazwę i numer wiersza gdzie `addNewRecord` wywołano będą przechowywane w każdy blok wynikowy przydzielić w stercie debugowania i zostaną zgłoszone po tym bloku się zbadana.  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)