---
title: MFC debugowania techniki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe2ae47be54f175f798e321da7644540f8ea5049
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="mfc-debugging-techniques"></a>Techniki testowania MFC
Jeśli debugowany program MFC, mogą być przydatne tych metod debugowania.  
  
##  <a name="BKMK_In_this_topic"></a> W tym temacie  
 [AfxDebugBreak](#BKMK_AfxDebugBreak)  
  
 [TRACE — makro](#BKMK_The_TRACE_macro)  
  
 [Wykrywanie przecieków pamięci w MFC](#BKMK_Memory_leak_detection_in_MFC)  
  
-   [Śledzenia alokacji pamięci](#BKMK_Tracking_memory_allocations)  
  
-   [Włączanie diagnostyki pamięci](#BKMK_Enabling_memory_diagnostics)  
  
-   [Tworzenie migawek pamięci](#BKMK_Taking_memory_snapshots)  
  
-   [Wyświetlanie statystyk pamięci](#BKMK_Viewing_memory_statistics)  
  
-   [Zrzuty obiektu z argumentami](#BKMK_Taking_object_dumps)  
  
    -   [Interpretowanie pamięci zrzuty](#BKMK_Interpreting_memory_dumps)  
  
    -   [Dostosowywanie obiektów zrzuty](#BKMK_Customizing_object_dumps)  
  
     [Zmniejszenie rozmiaru kompilacji debugowania MFC](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)  
  
    -   [Tworzenie aplikacji MFC z informacji o debugowaniu dla wybranych modułów](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)  
  
##  <a name="BKMK_AfxDebugBreak"></a> Afxdebugbreak —  
 MFC zapewnia specjalnego [afxdebugbreak —](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) funkcja dla kodować punktów przerwania w kodzie źródłowym:  
  
```  
AfxDebugBreak( );  
  
```  
  
 Na platformach firmy Intel `AfxDebugBreak` tworzy następujący kod, w jakich źródła code zamiast kodu jądra:  
  
```  
_asm int 3  
```  
  
 Na innych platformach `AfxDebugBreak` jedynie wywołuje `DebugBreak`.  
  
 Należy usunąć `AfxDebugBreak` instrukcji podczas tworzenia wersji kompilacji lub użyć `#ifdef _DEBUG` otaczającego je.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_TRACE_macro"></a> TRACE — makro  
 Aby wyświetlać komunikaty z programu w debugerze [okno danych wyjściowych](../ide/reference/output-window.md), można użyć [ATLTRACE](http://msdn.microsoft.com/Library/c796baa5-e2b9-4814-a27d-d800590b102e) makro lub MFC [śledzenia](http://msdn.microsoft.com/Library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) makra. Podobnie jak [potwierdzenia](../debugger/c-cpp-assertions.md), makra śledzenia są aktywne tylko w wersji do debugowania programu i znikają podczas kompilacji w wersji.  
  
 W poniższych przykładach pokazano niektóre sposoby używania **śledzenia** makra. Podobnie jak `printf`, **śledzenia** makro może obsługiwać liczbę argumentów.  
  
```  
int x = 1;  
int y = 16;  
float z = 32.0;  
TRACE( "This is a TRACE statement\n" );  
  
TRACE( "The value of x is %d\n", x );  
  
TRACE( "x = %d and y = %d\n", x, y );  
  
TRACE( "x = %d and y = %x and z = %f\n", x, y, z );  
```  
  
 TRACE — makro prawidłowo obsługuje zarówno char * i wchar_t\* parametrów. Poniższe przykłady przedstawiają sposób używania TRACE — makro wraz z różnych typów parametrów typu ciąg.  
  
```  
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);  
  
TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);  
  
TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);  
  
```  
  
 Aby uzyskać więcej informacji na temat **śledzenia** makra, zobacz [usługi diagnostyczne](/cpp/mfc/reference/diagnostic-services).  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Memory_leak_detection_in_MFC"></a> Wykrywanie przecieków pamięci w MFC  
 MFC zawiera klasy i funkcje wykrywania pamięci, który jest przydzielony, ale nigdy nie alokację.  
  
###  <a name="BKMK_Tracking_memory_allocations"></a> Śledzenia alokacji pamięci  
 W MFC, można użyć makra [debug_new —](http://msdn.microsoft.com/Library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) zamiast **nowe** przecieków operatora, aby łatwiej zlokalizować pamięci. W wersji do debugowania programu `DEBUG_NEW` przechowuje informacje o pliku nazwę i wiersz numer dla każdego obiektu, który go przydziela. Podczas kompilowania wydanej wersji programu, `DEBUG_NEW` jest rozpoznawana jako prosty **nowe** operację bez nazwy i wiersz numer informacje o pliku. W związku z tym płacisz nie kar szybkości w wydanej wersji programu.  
  
 Jeśli nie chcesz przepisywania całego programu do użycia `DEBUG_NEW` zamiast **nowe**, to makro można zdefiniować w plikach źródłowych:  
  
```  
#define new DEBUG_NEW  
```  
  
 Po wykonaniu [zrzutu obiektu](#BKMK_Taking_object_dumps), każdy z obiektów przydzielonych za pomocą `DEBUG_NEW` wyświetli liczbę plików i wierszy, gdzie została przydzielona, co umożliwia wskazanie źródeł przecieki pamięci.  
  
 Wersja do debugowania programu MFC framework używa `DEBUG_NEW` automatycznie, ale nie w kodzie. Jeśli chcesz skorzystać z `DEBUG_NEW`, należy użyć `DEBUG_NEW` jawnie lub **#define nowych** zgodnie z powyższym.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Enabling_memory_diagnostics"></a> Włączanie diagnostyki pamięci  
 Przed użyciem funkcji Diagnostyka pamięci, trzeba włączyć śledzenie diagnostyczne.  
  
 **Aby włączyć lub wyłączyć Diagnostyka pamięci**  
  
-   Wywołanie funkcji globalnych [afxenablememorytracking —](http://msdn.microsoft.com/Library/0a40e0c4-855d-46e2-9577-a8f2346f47db) Aby włączyć lub wyłączyć alokatora diagnostycznych. Ponieważ Diagnostyka pamięci są domyślnie w bibliotece debugowania, zwykle użyje tę funkcję, aby tymczasowo wyłączyć je, co przyspiesza wykonywanie programu i zmniejsza diagnostycznych danych wyjściowych.  
  
 **Aby wybrać funkcje diagnostyczne pamięci z afxmemdf —**  
  
-   Jeśli chcesz bardziej precyzyjną kontrolę nad funkcje diagnostyczne pamięci można selektywnie włączyć funkcje diagnostyczne pamięci poszczególnych włączać i wyłączać za pomocą ustawienia wartości zmiennej globalnej MFC [afxmemdf —](http://msdn.microsoft.com/Library/cf117501-5446-4fce-81b3-f7194bc95086). Ta zmienna może mieć następujące wartości zgodnie z typu wyliczeniowego **afxmemdf —**.  
  
    |Wartość|Opis|  
    |-----------|-----------------|  
    |**allocMemDF**|Włącz diagnostycznych alokatora (ustawienie domyślne).|  
    |**delayFreeMemDF**|Opóźnienie zwalnianie pamięci podczas wywoływania metody `delete` lub `free` dopóki wyjście z programu. To spowoduje, że program przydzielić maksymalną ilość pamięci.|  
    |**checkAlwaysMemDF**|Wywołanie [afxcheckmemory —](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) każdorazowo pamięci są przydzielone lub zwolniony.|  
  
     Te wartości można w połączeniu za pomocą operacji operatora logicznego OR, jak pokazano poniżej:  
  
    ```C++  
    afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;  
    ```  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Taking_memory_snapshots"></a> Tworzenie migawek pamięci  
  
1.  Utwórz [CMemoryState](http://msdn.microsoft.com/en-us/8fade6e9-c6fb-4b2a-8565-184a912d26d2) obiekt i wywołanie [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure.md#cmemorystate__Checkpoint) funkcję elementu członkowskiego. Spowoduje to utworzenie pierwszej migawki pamięci.  
  
2.  Po program wykonuje operacje alokacji i dezalokacji jej pamięci, należy utworzyć inny `CMemoryState` obiekt i wywołanie `Checkpoint` dla tego obiektu. Pobiera to drugi migawki użycia pamięci.  
  
3.  Utwórz innej `CMemoryState` obiekt i wywołanie jego [CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure.md#cmemorystate__Difference) funkcji członkowskiej, podając jako argumenty dwa poprzednie `CMemoryState` obiektów. Jeśli ma różnicy między Stanami dwóch pamięci `Difference` funkcja zwraca wartość różną od zera. Oznacza to, że niektóre bloki pamięci nie przydział został cofnięty.  
  
     Ten przykład przedstawia kod wygląda następująco:  
  
    ```  
    // Declare the variables needed  
    #ifdef _DEBUG  
        CMemoryState oldMemState, newMemState, diffMemState;  
        oldMemState.Checkpoint();  
    #endif  
  
        // Do your memory allocations and deallocations.  
        CString s("This is a frame variable");  
        // The next object is a heap object.  
       CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
  
    #ifdef _DEBUG  
        newMemState.Checkpoint();  
        if( diffMemState.Difference( oldMemState, newMemState ) )  
        {  
            TRACE( "Memory leaked!\n" );  
        }  
    #endif  
    ```  
  
     Należy zauważyć, że instrukcje sprawdzanie pamięci są otoczone **#ifdef _DEBUG / #endif** blokuje, dzięki czemu są one kompilowane tylko w wersjach debugowania programu.  
  
     Teraz, znając występuje przeciek pamięci, można użyć innej funkcji członkowskiej, [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure.md#cmemorystate__DumpStatistics) który ułatwi jego znalezienie.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Viewing_memory_statistics"></a> Wyświetlanie statystyk pamięci  
 [CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure.md#cmemorystate__Difference) Funkcja przegląda dwa obiekty stanu pamięci i wykrywa wszystkie obiekty nie cofnąć alokacji sterty między Stanami początku i na końcu. Po podjęte migawki pamięci i porównać je przy użyciu `CMemoryState::Difference`, można wywołać [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure.md#cmemorystate__DumpStatistics) można pobrać informacji o obiektach, które nie zostały alokację.  
  
 Rozważmy następujący przykład:  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpStatistics();  
}  
```  
  
 Zrzut próbki z przykładu wygląda następująco:  
  
```  
0 bytes in 0 Free Blocks  
22 bytes in 1 Object Blocks  
45 bytes in 4 Non-Object Blocks  
Largest number used: 67 bytes  
Total allocations: 67 bytes  
```  
  
 Bezpłatne bloki są blokami dezalokacji których występują opóźnienia, jeśli `afxMemDF` ustawiono `delayFreeMemDF`.  
  
 Bloki zwykłego obiektu, wyświetlany w drugim wierszu pozostają przydzielony na stosie.  
  
 Tablice zawierają bloki non-object i struktur przydzielonych za pomocą `new`. W takim przypadku czterech bloki-object zostały przydzielony na stosie, ale nie alokację.  
  
 `Largest number used` zapewnia maksymalna ilość pamięci, używanych przez program w dowolnym momencie.  
  
 `Total allocations` daje łączną ilość pamięci używanej przez program.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Taking_object_dumps"></a> Zrzuty obiektu z argumentami  
 W programie MFC, można użyć [CMemoryState::DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure.md#cmemorystate__DumpAllObjectsSince) do zrzutu opis wszystkich obiektów na stercie, które nie zostały alokację. `DumpAllObjectsSince` zrzuty wszystkie obiekty przydzielone od momentu ostatniego [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure.md#cmemorystate__Checkpoint). Jeśli nie `Checkpoint` wywołanie miało miejsce, `DumpAllObjectsSince` zrzuty wszystkich obiektów i nonobjects aktualnie w pamięci.  
  
> [!NOTE]
>  Przed użyciem zrzucanie obiekt MFC, należy najpierw [włączyć śledzenie diagnostyczne](#BKMK_Enabling_Memory_Diagnostics).  
  
> [!NOTE]
>  Gdy program jest kończona MFC automatycznie zrzuty ujawnione wszystkie obiekty, dzięki czemu nie trzeba tworzyć kod, aby zrzutu obiektów w tym momencie.  
  
 Poniższy kod testów dla przeciek pamięci na podstawie porównania ilości pamięci dwustanowy i zrzuty wszystkie obiekty, wykryje przeciek.  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpAllObjectsSince();  
}  
```  
  
 Zawartość zrzutu wyglądać następująco:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Liczby w nawiasach klamrowych na początku linii większości określić kolejność, w którym obiekty przydzielone. Najbardziej, ostatnio przydzielone obiekt o najwyższym numerze i pojawia się w górnej części zrzutu.  
  
 Aby uzyskać maksymalną ilość informacji poza zrzutu obiektu, można zastąpić `Dump` funkcji członkowskiej dowolnego `CObject`-pochodnych obiekt, aby dostosować zrzutu obiektu.  
  
 Można ustawić punktu przerwania w alokacji pamięci przez ustawienie zmiennej globalnej `_afxBreakAlloc` do liczby wyświetlanej w nawiasy klamrowe. Jeśli uruchomisz program debuger będzie Przerwij wykonywanie, gdy tej alokacji. Następnie można przeglądać stos wywołań, aby zobaczyć, jak program otrzymano do danego punktu.  
  
 Biblioteki wykonawcze języka C ma podobną funkcję, [_crtsetbreakalloc —](/cpp/c-runtime-library/reference/crtsetbreakalloc), której można uzyskać alokacji wykonawcze języka C.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
####  <a name="BKMK_Interpreting_memory_dumps"></a> Interpretowanie pamięci zrzuty  
 Obejrzyj ten zrzut obiektu bardziej szczegółowo:  
  
```  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Program wygenerowania tego zrzutu ma tylko dwa alokacji jawne — jedną na stosie, a drugi na stercie:  
  
```  
// Do your memory allocations and deallocations.  
CString s("This is a frame variable");  
// The next object is a heap object.  
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
```  
  
 `CPerson` Konstruktor ma trzy argumenty, które są wskaźnikami do `char`, które są używane do zainicjowania `CString` zmiennych Członkowskich. Zrzut pamięci zawiera `CPerson` obiektu wraz z trzech bloków nonobject (3, 4 i 5). Przechowywania tych znaków dla `CString` zmiennych Członkowskich i nie zostaną usunięte po `CPerson` destruktor obiektu jest wywoływany.  
  
 Blok Numer 2 jest `CPerson` samego obiektu. `$51A4` reprezentuje adres bloku i następuje zawartość obiektu, który zostały danych wyjściowych przez `CPerson`::`Dump` wywołanego [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure.md#cmemorystate__DumpAllObjectsSince).  
  
 Można odgadnąć, z którymi skojarzony jest blok o numerze 1 `CString` zmiennej ramki z powodu jego numer sekwencji i wielkości, która jest zgodna z liczbą znaków w ramce `CString` zmiennej. Zmienne przydzielone ramki są automatycznie alokację ramki systemowi poza zakresem.  
  
 **Zmienne ramek**  
  
 Ogólnie rzecz biorąc mogą nie występować sterty obiektów skojarzonych z zmienne ramek, ponieważ są automatycznie alokację podczas zmienne ramek się znaleźć poza zakresem. Aby uniknąć bałaganu Twojego diagnostycznych zrzuty pamięci, należy umieścić wywołaniami `Checkpoint` , które stają się poza zakresem zmienne ramek. Na przykład umieścić zakresu w nawiasach poprzedni kod alokacji, jak pokazano poniżej:  
  
```  
oldMemState.Checkpoint();  
{  
    // Do your memory allocations and deallocations ...  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
}  
newMemState.Checkpoint();  
```  
  
 W zakresie nawiasy w miejscu zrzut pamięci w tym przykładzie jest następujący:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
```  
  
 **Nonobject alokacji**  
  
 Zwróć uwagę, że są niektóre obiekty (takie jak `CPerson`), a inne nonobject alokacji. "Nonobject" są alokacji dla obiektów nie pochodzi od `CObject` lub alokacje typów pierwotnych C, takich jak `char`, `int`, lub `long`. Jeśli **CObject -** klasy pochodnej przydziela miejsce dodatkowe, takie jak dla wewnętrznego buforów, te obiekty będą wyświetlane zarówno obiektu i nonobject alokacji.  
  
 **Zapobieganie przecieki pamięci**  
  
 Zwróć uwagę w powyższym kodzie, że blok pamięci skojarzone z `CString` zmienną ramki alokację automatycznie i nie jest wyświetlany jako przeciek pamięci. Automatyczne cofania alokacji skojarzone z reguł ustawiania zakresu zapewnia obsługę większości przecieki pamięci skojarzone z zmienne ramek.  
  
 Dla obiektów przydzielony na stosie jednak należy jawnie usunąć obiektu, aby zapobiec przeciek pamięci. Aby wyczyścić ostatniego przeciek pamięci w poprzednim przykładzie, należy usunąć `CPerson` obiekt przydzielony na stosie, w następujący sposób:  
  
```  
{  
    // Do your memory allocations and deallocations.  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
    delete p;  
}  
```  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
####  <a name="BKMK_Customizing_object_dumps"></a> Dostosowywanie obiektów zrzuty  
 Gdy klasa wyprowadzona z z [CObject](/cpp/mfc/reference/cobject-class), można zastąpić `Dump` funkcji członkowskiej, aby podać dodatkowe informacje, gdy używasz [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure.md#cmemorystate__DumpAllObjectsSince) do obiektów zrzutu do [Okno danych wyjściowych](../ide/reference/output-window.md).  
  
 `Dump` Funkcja zapisuje tekstową reprezentację wartości elementu członkowskiego obiektu zmienne w kontekście zrzutu ([CDumpContext](/cpp/mfc/reference/cdumpcontext-class)). Kontekst zrzutu jest podobny do strumienia we/wy. Można użyć operatora append (**<<**) do wysyłania danych do `CDumpContext`.  
  
 Jeśli zastąpienie `Dump` funkcji, należy najpierw wywołać wersja klasy podstawowej `Dump` do zrzutu zawartość obiektu klasy podstawowej. Następnie dane wyjściowe tekstowy opis i wartość każdej zmiennej elementu członkowskiego klasy pochodnej.  
  
 Deklaracja `Dump` funkcja wygląda następująco:  
  
```  
class CPerson : public CObject  
{  
public:  
#ifdef _DEBUG  
    virtual void Dump( CDumpContext& dc ) const;  
#endif  
  
    CString m_firstName;  
    CString m_lastName;  
    // And so on...  
};  
```  
  
 Ponieważ zrzucanie obiekt ma sens tylko podczas debugowania programu deklaracja `Dump` funkcji jest oddzielona z **#ifdef _DEBUG / #endif** bloku.  
  
 W poniższym przykładzie `Dump` pierwsze wywołania funkcji `Dump` funkcja dla swojej klasy podstawowej. Następnie zapisuje krótki opis każdego zmiennej członkowskiej, wraz z wartością elementu członkowskiego w strumieniu diagnostycznych.  
  
```  
#ifdef _DEBUG  
void CPerson::Dump( CDumpContext& dc ) const  
{  
    // Call the base class function first.  
    CObject::Dump( dc );  
  
    // Now do the stuff for our specific class.  
    dc << "last name: " << m_lastName << "\n"  
        << "first name: " << m_firstName << "\n";  
}  
#endif  
```  
  
 Należy podać `CDumpContext` argumentu, aby określić, gdzie dane wyjściowe zrzutu. Wersja debugowania MFC udostępnia wstępnie zdefiniowanej `CDumpContext` obiektu o nazwie `afxDump` który wysyła dane wyjściowe do debugera.  
  
```  
CPerson* pMyPerson = new CPerson;  
// Set some fields of the CPerson object.  
//...  
// Now dump the contents.  
#ifdef _DEBUG  
pMyPerson->Dump( afxDump );  
#endif  
```  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Zmniejszenie rozmiaru kompilacji debugowania MFC  
 Informacje o debugowaniu dla dużych aplikacji MFC może zająć dużo miejsca na dysku. Jedną z tych procedur umożliwia zmniejszenie rozmiaru:  
  
1.  Odbuduj bibliotek MFC przy użyciu [/z7, / zi, /ZI (Format informacji debugowania)](/cpp/build/reference/z7-zi-zi-debug-information-format) opcji, zamiast **/z7**. Te opcje tworzenia pliku bazy danych (PDB) jeden program zawierający informacje o debugowaniu dla całej biblioteki, ograniczenie nadmiarowości i zapisywanie miejsca.  
  
2.  Odbuduj biblioteki MFC bez informacji debugowania (nie [/z7, / zi, /ZI (Format informacji debugowania)](/cpp/build/reference/z7-zi-zi-debug-information-format) opcja). W przypadku braku informacji o debugowaniu uniemożliwi przy użyciu większości funkcji debugera kodem biblioteki MFC, ale ponieważ biblioteki MFC są już dokładnie debugowany, nie może to być spowodowane problemem.  
  
3.  Tworzenie aplikacji z informacjami dotyczącymi debugowania dla wybranych modułów tylko zgodnie z poniższym opisem.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Tworzenie aplikacji MFC z informacji o debugowaniu dla wybranych modułów  
 Tworzenie wybranych modułów z biblioteki debugowania MFC umożliwia użycia wykonywanie krok po kroku i inne urządzenia debugowania w tych modułach. Ta procedura korzysta z obu debugowania i wydania tryby makefile Visual C++, co wymaga zmiany opisane w poniższych kroków (i również wprowadzania "odbudowanie wszystkiego" to konieczne, gdy wymagana jest pełna kompilacji wydania).  
  
1.  W Eksploratorze rozwiązań wybierz projekt.  
  
2.  Z **widoku** menu, wybierz opcję **strony właściwości**.  
  
3.  Najpierw należy utworzyć nową konfigurację projektu.  
  
    1.  W  **\<projektu > strony właściwości** okno dialogowe, kliknij przycisk **programu Configuration Manager** przycisku.  
  
    2.  W [okno dialogowe programu Configuration Manager](http://msdn.microsoft.com/en-us/fa182dca-282e-4ae5-bf37-e155344ca18b), zlokalizować projektu w siatce. W **konfiguracji** kolumny wybierz  **\<nowy... >**.  
  
    3.  W [okno dialogowe nowego projektu konfiguracji](http://msdn.microsoft.com/en-us/cca616dc-05a6-4fe3-bdc1-40c72a66f2be), wpisz nazwę dla nowej konfiguracji, takich jak "Częściowe Debug", w **Nazwa konfiguracji projektu** pole.  
  
    4.  W **Skopiuj ustawienia z** wybierz **wersji**.  
  
    5.  Kliknij przycisk **OK** zamknąć **nową konfigurację projektu**okno dialogowe.  
  
    6.  Zamknij **programu Configuration Manager** okno dialogowe.  
  
4.  Teraz zostanie Ustaw opcje dla całego projektu.  
  
    1.  W **strony właściwości** okna dialogowego, w obszarze **właściwości konfiguracji** folderu, wybierz opcję **ogólne** kategorii.  
  
    2.  W siatce ustawienia projektu, rozwiń węzeł **domyślne projektu** (Jeśli to konieczne).  
  
    3.  W obszarze **domyślne projektu**, Znajdź **Użyj MFC**. Bieżące ustawienie jest wyświetlany w prawej kolumnie siatki. Kliknij na bieżące ustawienia i zmień go na **Użyj MFC w bibliotece statycznej**.  
  
    4.  W lewym okienku **stron właściwości** po otwarciu okna dialogowego **C/C++** i wybierz polecenie **preprocesora**. W siatce właściwości znaleźć **definicje preprocesora** i zastąp "NDEBUG" "_DEBUG".  
  
    5.  W lewym okienku **stron właściwości** po otwarciu okna dialogowego **konsolidatora** i wybierz polecenie **dane wejściowe** kategorii. W siatce właściwości znaleźć **dodatkowe zależności**. W **dodatkowe zależności** ustawienie, wpisz "NAFXCWD. LIB"i"LIBCMT."  
  
    6.  Kliknij przycisk **OK** Aby zapisać nowe opcje kompilacji i zamknąć **strony właściwości** okno dialogowe.  
  
5.  Z **kompilacji** menu, wybierz opcję **odbudować**. Usuwa wszystkie informacje o debugowaniu moduły, ale nie ma wpływu na biblioteki MFC.  
  
6.  Teraz należy dodać informacje debugowania do wybranych modułów w aplikacji. Należy pamiętać, że można ustawić punktów przerwania i wykonać inne funkcje debugera tylko moduły, które zostały skompilowane z informacji o debugowaniu. Dla każdego pliku projektu, w którym chcesz dołączyć informacje o debugowaniu, wykonaj następujące czynności:  
  
    1.  W Eksploratorze rozwiązań Otwórz **pliki źródłowe** folder znajduje się w obszarze projektu.  
  
    2.  Wybierz plik, który chcesz ustawić informacji debugowania dla.  
  
    3.  Z **widoku** menu, wybierz opcję **strony właściwości**.  
  
    4.  W **strony właściwości** okna dialogowego, w obszarze **ustawienia konfiguracji** folder, otwórz **C/C++** następnie wybierz folder **ogólne** Kategoria.  
  
    5.  W siatce właściwości znaleźć **Format informacji debugowania.**  
  
    6.  Kliknij przycisk **Format informacji debugowania** ustawień i wybierz odpowiednią opcję (zazwyczaj **/zi**) dla informacji debugowania.  
  
    7.  Jeśli używasz aplikacji generowane przez Kreatora aplikacji lub ma prekompilowane nagłówki, należy wyłączyć prekompilowanych nagłówków lub skompiluj ponownie je przed skompilowaniem innych modułów. W przeciwnym razie zostanie wyświetlony ostrzeżenie C4650 i komunikat o błędzie C2855. Prekompilowane nagłówki można wyłączyć, zmieniając **użycia tworzenie prekompilowanych nagłówków** w  **\<projektu > właściwości** okno dialogowe (**właściwości konfiguracji**  folderu, **C/C++** podfolderu, **prekompilowanych nagłówków** kategorii).  
  
7.  Z **kompilacji** menu, wybierz opcję **kompilacji** odbudować pliki projektu, które są nieaktualne.  
  
 Jako alternatywę techniki opisane w tym temacie, można użyć zewnętrznego pliku reguł programu make określenie poszczególnych opcji dla każdego pliku. W takim przypadku można połączyć z biblioteki debugowania MFC, należy zdefiniować [_DEBUG](/cpp/c-runtime-library/debug) flagi dla każdego modułu. Jeśli chcesz użyć biblioteki MFC wersji, należy zdefiniować NDEBUG. Aby uzyskać więcej informacji na temat pisania zewnętrzne pliki reguł programu make, zobacz [odwołanie NMAKE](/cpp/build/running-nmake).  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie Visual C++](../debugger/debugging-native-code.md)
