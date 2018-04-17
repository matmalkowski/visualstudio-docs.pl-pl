---
title: Potwierdzenia C/C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 8c5180e1ef5a75a31ff6ceb6c225480e1abba5fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="cc-assertions"></a>Potwierdzenia C/C++
Instrukcja potwierdzenia określa warunek, który będzie mieć wartość true w punkcie w programie. Jeśli ten warunek nie zostanie spełniony, potwierdzenie nie powiedzie się, wykonania programu zostanie przerwany i [błędy potwierdzenia — okno dialogowe](../debugger/assertion-failed-dialog-box.md) pojawi się.  
  
 Visual C++ obsługuje instrukcji potwierdzania, które są oparte na następujące elementy:  
  
-   Potwierdzenia MFC dla programów MFC.  
  
-   [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) dla programów, które używają ATL.  
  
-   Potwierdzenia CRT dla programów, które używają biblioteki wykonawczej języka C.  
  
-   ANSI [assert funkcja](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) dla innych programów C/C++.  
  
 Potwierdzenia umożliwia catch błędy logiczne, sprawdź wyniki operacji i przetestowania warunki błędów, które powinno zostać obsłużone.  
  
##  <a name="BKMK_In_this_topic"></a> W tym temacie  
 [Jak działają potwierdzeń](#BKMK_How_assertions_work)  
  
 [Potwierdzenia w kompilacji Debug i Release](#BKMK_Assertions_in_Debug_and_Release_builds)  
  
 [Efekty uboczne użycia potwierdzenia](#BKMK_Side_effects_of_using_assertions)  
  
 [Potwierdzenia CRT](#BKMK_CRT_assertions)  
  
 [Potwierdzenia MFC](#BKMK_MFC_assertions)  
  
-   [Assert_valid — MFC i CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  
  
-   [Ograniczenia AssertValid](#BKMK_Limitations_of_AssertValid)  
  
 [Przy użyciu potwierdzenia](#BKMK_Using_assertions)  
  
-   [Przechwytywanie błędy logiczne](#BKMK_Catching_logic_errors)  
  
-   [Sprawdzanie wyników](#BKMK_Checking_results_)  
  
-   [Błędy niezgodności nieobsługiwany](#BKMK_Testing_error_conditions_)  
  
##  <a name="BKMK_How_assertions_work"></a> Jak działają potwierdzeń  
 Gdy debuger zostaje zatrzymana z powodu potwierdzeniem biblioteki wykonawczej MFC lub C, następnie Jeśli źródło jest dostępne, debuger przechodzi do punktu w pliku źródłowym, w którym wystąpiło to potwierdzenie. Zostanie wyświetlony komunikat potwierdzenia w obu [okno danych wyjściowych](../ide/reference/output-window.md) i **nie powiodła się Asercja** okno dialogowe. Możesz skopiować komunikat potwierdzenia **dane wyjściowe** okna do okna tekstowego, jeśli chcesz zapisać go do użytku w przyszłości. **Dane wyjściowe** okna może zawierać inne komunikaty o błędach oraz. Sprawdź dokładnie, te komunikaty, ponieważ udostępniają one wskazówek do przyczyną błędu potwierdzenia.  
  
 Użyj potwierdzenia do wykrywania błędów w czasie projektowania. Jako zasadę Użyj jednego potwierdzenia dla każdego założeń. Na przykład jeśli założono, że argument nie jest zerowa, należy użyć potwierdzenia do przetestowania tego założeń.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Potwierdzenia w kompilacji Debug i Release  
 Instrukcji potwierdzania skompilować tylko wtedy, gdy `_DEBUG` jest zdefiniowany. W przeciwnym razie kompilator traktuje potwierdzenia oświadczenia wartości null. W związku z tym instrukcji potwierdzania nałożyć całkowitej lub wydajność kosztów w programie Release końcowego i pozwala uniknąć używania `#ifdef` dyrektywy.  
  
##  <a name="BKMK_Side_effects_of_using_assertions"></a> Efekty uboczne użycia potwierdzenia  
 Po dodaniu potwierdzenia do kodu, upewnij się, że potwierdzenia ma efekty uboczne. Na przykład, należy wziąć pod uwagę następujące potwierdzenia, które modyfikuje `nM` wartość:  
  
```  
ASSERT(nM++ > 0); // Don't do this!  
  
```  
  
 Ponieważ `ASSERT` wyrażenie nie jest obliczane w wydanej wersji programu, `nM` mają różne wartości w wersji Debug i Release. Aby uniknąć tego problemu w MFC, można użyć [Sprawdź](/cpp/mfc/reference/diagnostic-services#verify) makro zamiast `ASSERT`.  `VERIFY` oblicza wyrażenie we wszystkich wersjach, ale nie sprawdza wynik w wersji.  
  
 Należy zachować ostrożność szczególnie przy użyciu wywołania funkcji w instrukcji potwierdzania, ponieważ obliczania funkcji może mieć nieoczekiwane skutki uboczne.  
  
```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  
  
 `VERIFY` wywołania `myFnctn` w wersjach zarówno Debug i Release, dlatego jest można korzystać. Jednak przy użyciu `VERIFY` nakłada obciążenie wywołanie funkcji niepotrzebnych w wersji.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_CRT_assertions"></a> Potwierdzenia CRT  
 CRTDBG. Określa plik nagłówka H [_ASSERT i _asserte — makra](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) sprawdzania potwierdzenia.  
  
|Macro|Wynik|  
|-----------|------------|  
|`_ASSERT`|Jeśli określone wyrażenie nie jest SPEŁNIONY, plik nazwy i wiersz numer `_ASSERT`.|`_ASSERTE`|  
|`_ASSERTE`|Taki sam jak `_ASSERT`, oraz reprezentację ciągu wyrażenie, które zostało potwierdzone.|  
  
 `_ASSERTE` jest bardziej wydajne, ponieważ zgłasza potwierdzona wyrażenie, które są wartość FALSE. Może to być za mało, aby zidentyfikować problem bez odwołujących się do kodu źródłowego. Wersja do debugowania aplikacji będzie jednak zawierać stałą typu string dla każdego wyrażenia potwierdzone przy użyciu `_ASSERTE`. Jeśli używasz wielu `_ASSERTE` makra, te wyrażenia ciągu zająć znaczną ilość pamięci. Jeśli okaże się problem, użyj `_ASSERT` można zapisać w pamięci.  
  
 Gdy `_DEBUG` jest zdefiniowany, `_ASSERTE` makro jest zdefiniowane w następujący sposób:  
  
```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  
  
 Jeśli potwierdzenie wyrażenie ma wartość FALSE, [_crtdbgreport —](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) jest wywoływana, aby zgłosić błąd potwierdzenia (przy użyciu wiadomości okno dialogowe domyślnie). Jeśli wybierzesz **ponów** w oknie dialogowym komunikatu `_CrtDbgReport` zwraca wartość 1 i `_CrtDbgBreak` wywołuje debugera za pośrednictwem `DebugBreak`.  
  
### <a name="checking-for-heap-corruption"></a>Sprawdzanie, czy uszkodzenie sterty  
 W poniższym przykładzie użyto [_crtcheckmemory —](/cpp/c-runtime-library/reference/crtcheckmemory) aby wykryć ewentualne uszkodzenia sterty:  
  
```  
_ASSERTE(_CrtCheckMemory());  
```  
  
### <a name="checking-pointer-validity"></a>Sprawdzanie poprawności wskaźnika  
 W poniższym przykładzie użyto [_crtisvalidpointer —](/cpp/c-runtime-library/reference/crtisvalidpointer) można zweryfikować, że pamięci dany zakres jest prawidłowy dla odczytu lub zapisu.  
  
```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  
  
 W poniższym przykładzie użyto [_crtisvalidheappointer —](/cpp/c-runtime-library/reference/crtisvalidheappointer) można sprawdzić wskaźnik do pamięci lokalnej sterty (sterty tworzone i zarządzane przez to wystąpienie biblioteki wykonawczej języka C — biblioteki DLL może mieć własne wystąpienie biblioteki, a w związku z tym własną sterty, poza sterty aplikacji). Ta asercja nie przechwytuje tylko wartości null lub zdalne adresy, ale również wskaźniki zmienne statyczne, zmienne stosu i inne nielokalne pamięci.  
  
```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  
  
### <a name="checking-a-memory-block"></a>Sprawdzanie blok pamięci  
 W poniższym przykładzie użyto [_crtismemoryblock —](/cpp/c-runtime-library/reference/crtismemoryblock) Aby sprawdzić, czy blok pamięci znajduje się w lokalnej sterty i ma typ blokowy prawidłowe.  
  
```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_MFC_assertions"></a> Potwierdzenia MFC  
 Definiuje MFC [ASSERT](http://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) makro sprawdzania potwierdzenia. Definiuje również `MFC ASSERT_VALID` i `CObject::AssertValid` metody kontroli wewnętrzny stan klasy `CObject`-pochodzi z obiektu.  
  
 Jeśli argument MFC `ASSERT` makro ocenia się na zero lub ma wartość FAŁSZ, makra zatrzymuje wykonywanie programu i ostrzega o tym użytkownika; w przeciwnym razie wykonanie jest kontynuowane.  
  
 Jeśli potwierdzenie nie powiedzie się, okno dialogowe komunikat zawiera nazwę plik źródłowy i numer wiersza potwierdzenia. Jeżeli wybierz przycisk Ponów w oknie dialogowym pole, wywołanie [afxdebugbreak —](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) powoduje wykonanie przerwanie i przejście do debugera. W tym momencie można zbadać stosu wywołań i użyj inne urządzenia debugera, aby określić, dlaczego potwierdzenia nie powiodło się. Jeśli włączono [Just in time debugowania](../debugger/just-in-time-debugging-in-visual-studio.md)i debuger nie został jeszcze uruchomiony, okno dialogowe można uruchomić debugera.  
  
 Poniższy przykład przedstawia użycie `ASSERT` można sprawdzić wartość zwrotną funkcji:  
  
```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  
  
 Można użyć ASSERT z [IsKindOf](/cpp/mfc/reference/cobject-class.md#CObject__IsKindOf) funkcji typu sprawdzanie argumentów funkcji:  
  
```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  
  
 `ASSERT` Makro nie tworzy kodu w wersji. Można obliczyć wyrażenia w wersji, należy użyć [Sprawdź](/cpp/mfc/reference/diagnostic-services#verify) makro zamiast ASSERT.  
  
###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> Assert_valid — MFC i CObject::AssertValid  
 [CObject::AssertValid](/cpp/mfc/reference/cobject-class.md#CObject__AssertValid) metoda zapewnia czasu wykonywania kontroli wewnętrzny stan klasy obiektu. Nie są wymagane do przesłonięcia `AssertValid` po pochodzi z klasy `CObject`, możesz wprowadzić klasy bardziej niezawodny w ten sposób. `AssertValid` należy wykonać potwierdzeń na wszystkie zmienne Członkowskie obiektu, aby zweryfikować, że zawierają one prawidłowych wartości. Na przykład należy sprawdzić, że zmienne Członkowskie wskaźnik nie mają wartości NULL.  
  
 Poniższy przykład przedstawia sposób zadeklarować `AssertValid` funkcji:  
  
```  
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  
  
```  
  
 Jeśli zastąpienie `AssertValid`, wywołaj wersja klasy podstawowej `AssertValid` przed wykonaniem własnych kontroli. Następnie użyj ASSERT — makro do sprawdzenia elementów członkowskich unikatowy do klasy pochodnej, jak pokazano poniżej:  
  
```  
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  
  
    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  
  
```  
  
 Wszelkie zmiennych Członkowskich przechowywania obiektów, można użyć `ASSERT_VALID` makra w celu testowania ich ważność wewnętrzny (jeśli ich klasy zastępują `AssertValid`).  
  
 Rozważmy na przykład klasa `CMyData`, której są przechowywane [CObList](/cpp/mfc/reference/coblist-class) w jednym z jego zmiennych Członkowskich. `CObList` Zmiennej `m_DataList`, przechowywana kolekcja `CPerson` obiektów. Deklaracja skróconej `CMyData` wygląda podobnie do następującej:  
  
```  
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  
  
```  
  
 `AssertValid` Zastąpienia w `CMyData` wygląda podobnie do następującej:  
  
```  
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  
  
```  
  
 `CMyData` używa `AssertValid` mechanizmu, aby sprawdzić poprawność obiekty przechowywane w jego elementu członkowskiego danych. Zastępowanie `AssertValid` z `CMyData` wywołuje `ASSERT_VALID` makro własną m_pDataList zmiennej elementu członkowskiego.  
  
 Testowanie poprawności nie Zatrzymaj na tym poziomie, ponieważ klasa `CObList` zastępuje również `AssertValid`. To zastąpienie wykonuje dodatkowe ważności testowania na stan wewnętrzny listy. W związku z tym ważności testu na `CMyData` obiektu prowadzi do ważności dodatkowe testy dla wewnętrznego stanów zapisana `CObList` obiekt listy.  
  
 W niektórych więcej pracy można dodawać testy poprawności dla `CPerson` obiektów również przechowywane na liście. Można wyprowadzenia klasy `CPersonList` z `CObList` i zastąpić `AssertValid`. W zastąpienia, należy wywołać `CObject::AssertValid` , a następnie wykonać iterację liście wywoływania `AssertValid` na każdym `CPerson` obiektu przechowywane na liście. `CPerson` Klasa wyświetlane na początku tego tematu już zastępuje `AssertValid`.  
  
 To zaawansowany mechanizm podczas kompilacji do debugowania. Następnie kompilowania dla wersji, mechanizm jest wyłączony automatycznie.  
  
###  <a name="BKMK_Limitations_of_AssertValid"></a> Ograniczenia AssertValid  
 Wyzwalane potwierdzenia wskazuje, że obiekt jest ostatecznie zły i wykonywania zostanie zatrzymane. Brak potwierdzenia wskazuje jednak tylko nie znaleziono problemów, że obiekt nie gwarantuje to dobre.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_assertions"></a> Przy użyciu potwierdzenia  
  
###  <a name="BKMK_Catching_logic_errors"></a> Przechwytywanie błędy logiczne  
 Można ustawić potwierdzenia, pod warunkiem, że musi mieć wartość true, zgodnie z logiką programu. Potwierdzenie nie ma znaczenia, chyba że występuje błąd logiczny.  
  
 Na przykład, załóżmy, że są symulując związków gazu w kontenerze, a zmienna `numMols` reprezentuje sumę związków. Ta liczba nie może być mniejsza od zera, więc może zawierać instrukcji potwierdzenia MFC, jak to:  
  
```  
ASSERT(numMols >= 0);  
  
```  
  
 Lub może obejmować potwierdzenia CRT, jak to:  
  
```  
_ASSERT(numMols >= 0);  
```  
  
 Te instrukcje nic nie rób Jeśli program działa prawidłowo. Jeśli powoduje błąd logiczny `numMols` do być mniejsza od zera, jednak Potwierdzenie zatrzymuje wykonywanie programu i wyświetla [potwierdzenia nie powiodło się — okno dialogowe](../debugger/assertion-failed-dialog-box.md).  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Checking_results_"></a> Sprawdzanie wyników  
 Potwierdzenia są przydatne do testowania operacje, których wyniki nie są oczywiste z szybkiej kontroli visual.  
  
 Rozważmy na przykład następujący kod, który aktualizuje zmiennej `iMols` na podstawie zawartości połączonej listy wskazywana przez `mols`:  
  
```  
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  
  
 Liczba związków zliczane przez `iMols` zawsze musi być mniejsza niż łączna liczba związków, `numMols`. Visual kontroli pętli nie są wyświetlane, że zawsze będzie case, używana jest instrukcja potwierdzenia po pętli do testowania tego warunku.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Testing_error_conditions_"></a> Błędy niezgodności nieobsługiwany  
 Potwierdzenia można użyć do testowania dla warunków błędu w punkcie w kodzie, gdzie błędy powinien został obsłużony. W poniższym przykładzie graficzne procedury zwraca kod błędu lub zero w przypadku powodzenia.  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* Code to handle errors and  
   reset myErr if successful */  
  
ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  
  
 Jeśli kod obsługi błędów działa prawidłowo, powinien zostać obsłużony błąd i `myErr` resetowania od zera przed osiągnięciem potwierdzenia. Jeśli `myErr` ma inną wartość, potwierdzenie kończy się niepowodzeniem, zatrzymanie program i [potwierdzenia nie powiodło się — okno dialogowe](../debugger/assertion-failed-dialog-box.md) pojawi się.  
  
 Instrukcje potwierdzenie nie są jednak zamiast kodu obsługi błędu. W poniższym przykładzie pokazano instrukcję potwierdzenia, która może prowadzić do problemów w kodzie ostatecznej wersji:  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* No Code to handle errors */  
  
ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  
  
 Ten kod zależy od instrukcji potwierdzenia do obsługi warunku błędu. W związku z tym każdy kod błędu zwrócony przez `myGraphRoutine` będzie nieobsługiwany w ostatecznej wersji kodu.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Potwierdzenia w zarządzanym kodzie](../debugger/assertions-in-managed-code.md)