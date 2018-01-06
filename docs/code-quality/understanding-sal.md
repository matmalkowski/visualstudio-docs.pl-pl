---
title: Opis SAL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 196bfdbeeda00199861ea2f676553f024fcaf98f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-sal"></a>Poznanie SAL
Język Microsoft kodu źródłowego adnotacji (SAL) zawiera zestaw adnotacje, które można użyć do opisania używaniu funkcji jego parametrów, założeń, które ułatwia ich temat i gwarancji, które ułatwia po jej zakończeniu. Adnotacje są zdefiniowane w pliku nagłówka `<sal.h>`. Visual Studio analizy kodu dla języka C++ używa adnotacji SAL do modyfikowania jej analiza funkcji. Aby uzyskać więcej informacji na temat SAL 2.0 dla systemu Windows dla deweloperów sterowników, zobacz [SAL 2.0 adnotacje dla sterowników systemu Windows](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 Natywnie C i C++ umożliwiają tylko ograniczone deweloperom spójnie express zamiar i invariance. Korzystając z adnotacji SAL, można opisać funkcji szczegółowo tak, aby deweloperów, którzy je zużywają można lepiej zrozumieć sposób korzystania z nich.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>Co to jest SAL i dlaczego należy używać go?  
 Krótko mówiąc, SAL jest niedrogich sposób kompilatora Sprawdź swój kod.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL sprawia, że kod większej wartości  
 SAL ułatwiają wprowadzanie projektu kodu bardziej zrozumiałe, zarówno w przypadku ludzi, jak i narzędzi analizy kodu. Należy wziąć pod uwagę w tym przykładzie, który pokazuje funkcji środowiska wykonawczego języka C `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 Można stwierdzić, ta funkcja nie? Gdy funkcja jest zaimplementowana lub o nazwie, niektórych właściwości muszą zostać zachowane w celu zapewnienia poprawności programu. Po prostu analizując deklaracji, takie jak w przykładzie, nie wiadomo, jakie są. Bez adnotacji SAL trzeba polegać na dokumentacji lub komentarze w kodzie. Poniżej przedstawiono w dokumentacji MSDN dla `memcpy` mówi:  
  
> "Kopie liczba bajtów src do miejsca docelowego. Jeśli nakładają się na źródłowym i docelowym, zachowanie memcpy jest niezdefiniowany. Memmove — umożliwia obsługę pokrywających się obszarów.   
> **Uwaga dotycząca zabezpieczeń:** upewnij się, że bufor docelowy jest taki sam lub większy rozmiar niż bufor źródłowy. Aby uzyskać więcej informacji zobacz unikanie Overruns buforu."  
  
 Dokumentacja zawiera kilka bitów informacje, które sugeruje kodu musi obsługiwać niektórych właściwości, aby zapewnić poprawność program:  
  
-   `memcpy`kopie `count` bajtów z bufora źródłowego do docelowego buforu.  
  
-   Bufor docelowy musi być przynajmniej tak duże jak bufor źródłowy.  
  
 Jednak kompilator nie może odczytać dokumentacji lub nieformalny komentarze. Nie wiadomo, że istnieje relacja między dwoma buforów i `count`, i go również nie mogą skutecznie odgadnąć o relacji. SAL można wyjaśnienia więcej o właściwościach i implementację funkcji, jak pokazano poniżej:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Należy zauważyć, że informacje w dokumentacji MSDN przypomina adnotacje, ale są bardziej zwięzły, a stosują wzorzec semantycznego. Po przeczytaniu tego kodu można szybko zrozumieć właściwości dla tej funkcji oraz jak uniknąć problemów z zabezpieczeniami przepełnienie buforu. Nawet lepiej semantycznego wzorców, które zapewnia SAL może zwiększyć wydajność i skuteczność narzędzi analizy kodu automatycznych w wczesne odnajdywania potencjalnych błędów. Załóżmy, że ktoś zapisuje ta implementacja buggy `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Ta implementacja zawiera typowe błąd poza o jedno. Na szczęście autora kodu zawarte adnotacji SAL rozmiar buforu — narzędzie do analizy kodu można przechwycić usterki analizując tej samej funkcji.  
  
### <a name="sal-basics"></a>Podstawy SAL  
 SAL definiuje czterech podstawowych typów parametrów, które są pogrupowane według wzorca użycia.  
  
|Kategoria|Parametr adnotacji|Opis|  
|--------------|--------------------------|-----------------|  
|**Dane wejściowe, aby wywołać — funkcja**|`_In_`|Dane są przekazywane do wywołanej funkcji i jest traktowany jako tylko do odczytu.|  
|**Dane wejściowe wywołał funkcję, a dane wyjściowe do wywołującego**|`_Inout_`|Danych użytecznego została przekazana do funkcji i potencjalnie jest modyfikowany.|  
|**Dane wyjściowe do wywołującego**|`_Out_`|Obiekt wywołujący tylko miejsce wywołana funkcja do zapisu. Wywoływana funkcja zapisuje dane do tego miejsca.|  
|**Dane wyjściowe wskaźnik do obiektu wywołującego**|`_Outptr_`|Podobnie jak **dane wyjściowe do wywołującego**. Wartość zwracana przez funkcję o nazwie jest wskaźnik.|  
  
 Te cztery podstawowe adnotacje bardziej jako jawne można ustawić na różne sposoby. Domyślnie parametry wskaźnika adnotacjami uznaje się, że konieczności — muszą być inne niż NULL dla funkcji powiodło się. Najczęściej używane zmiany podstawowego adnotacje wskazuje, że parametr wskaźnika jest opcjonalne, jeśli ma wartość NULL, funkcja może nadal się powieść, w tym jego pracy.  
  
 W tej tabeli przedstawiono sposób rozróżnienia wymaganych i opcjonalnych parametrów:  
  
||Parametry są wymagane|Parametry są opcjonalne|  
|-|-----------------------------|-----------------------------|  
|**Dane wejściowe, aby wywołać — funkcja**|`_In_`|`_In_opt_`|  
|**Dane wejściowe wywołał funkcję, a dane wyjściowe do wywołującego**|`_Inout_`|`_Inout_opt_`|  
|**Dane wyjściowe do wywołującego**|`_Out_`|`_Out_opt_`|  
|**Dane wyjściowe wskaźnik do obiektu wywołującego**|`_Outptr_`|`_Outptr_opt_`|  
  
 Adnotacje identyfikowania możliwych wartości niezainicjowany i używa nieprawidłowego wskaźnika null w sposób formalny i dokładne. Przekazywanie wartości NULL do wymaganego parametru może spowodować awarię lub może spowodować, że kod błędu "nie powiodło się", ma zostać zwrócona. W obu przypadkach funkcja nie powiodło się w tym swojego zadania.  
  
## <a name="sal-examples"></a>Przykłady SAL  
 W tej sekcji przedstawiono przykłady kodu dla podstawowego adnotacji SAL.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Aby znaleźć wady przy użyciu narzędzie do analizy kodu programu Visual Studio  
 W przykładach narzędzia do analizy kodu w usłudze Visual Studio jest używany razem z adnotacji SAL można znaleźć defektów kodu. Oto jak to zrobić.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Aby użyć narzędzi analizy kodu programu Visual Studio i SAL  
  
1.  W programie Visual Studio Otwórz projekt C++, który zawiera adnotacji SAL.  
  
2.  Na pasku menu wybierz **kompilacji**, **uruchamiania analizy kodu dla rozwiązania**.  
  
     Należy wziąć pod uwagę _W\_ przykładzie w tej sekcji. Po uruchomieniu analizy kodu na nim to ostrzeżenie jest wyświetlane:  
  
    > **C6387 Niepoprawna wartość parametru**   
    > "Pinta" może być "0": jest to niespójne ze specyfikacją funkcji "InCallee".  
  
### <a name="example-the-in-annotation"></a>Przykład: _W\_ adnotacji  
 `_In_` Adnotacja wskazuje, że:  
  
-   Parametr musi być prawidłowy i nie zostaną zmodyfikowane.  
  
-   Funkcja odczyta tylko z jednym elementem buforu.  
  
-   Obiekt wywołujący musi dostarczyć buforu i zainicjować go.  
  
-   `_In_`Określa "read-only". Powszechnym błędem jest zastosowanie `_In_` do parametru, który powinien mieć `_Inout_` adnotacji zamiast tego.  
  
-   `_In_`jest dozwolone, ale jest ignorowana przez analizator na wartości skalarne nie będącego wskaźnikiem.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Jeśli używasz programu Visual Studio kod — analiza w tym przykładzie sprawdza czy obiekty wywołujące przekazać wskaźnika inną niż Null do zainicjowane buforu dla `pInt`. W takim przypadku `pInt` wskaźnika nie może mieć wartości NULL.  
  
### <a name="example-the-inopt-annotation"></a>Przykład: _In_opt\_ adnotacji  
 `_In_opt_`jest taka sama jak `_In_`, z wyjątkiem tego, że parametr wejściowy może mieć wartości NULL i, w związku z tym funkcja należy sprawdzić, czy to.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Kod — analiza Visual Studio weryfikuje, czy funkcja sprawdza NULL przed uzyskuje dostęp do buforu.  
  
### <a name="example-the-out-annotation"></a>Przykład: _poziomie\_ adnotacji  
 `_Out_`obsługuje typowy scenariusz, w którym wskazujące buforu elementu wskaźnik inną niż NULL jest przekazywany w i funkcja inicjuje element. Obiekt wywołujący nie ma zainicjować buforu przed wywołaniem; wywoływana funkcja niesie obietnice przed zwraca go zainicjować.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Narzędzie do analizy kodu programu Visual Studio weryfikuje wywołujący wskaźnik inną niż NULL w buforze dla `pInt` , a bufor jest inicjowany przez funkcję przed zwróceniem.  
  
### <a name="example-the-outopt-annotation"></a>Przykład: _Out_opt\_ adnotacji  
 `_Out_opt_`jest taka sama jak `_Out_`, ale parametr może mieć wartości NULL i, w związku z tym funkcja należy sprawdzić, czy to.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Kod — analiza Visual Studio weryfikuje, czy ta funkcja sprawdza NULL przed `pInt` jest wyłuskiwany i w razie `pInt` nie ma wartości NULL, że rozmiar buforu jest inicjowany przez funkcję przed zwróceniem.  
  
### <a name="example-the-inout-annotation"></a>Przykład: _inout —\_ adnotacji  
 `_Inout_`Służy do dodawania adnotacji parametr wskaźnika, które mogą zostać zmienione przez funkcję. Wskaźnik musi wskazywać prawidłowe dane zainicjowany przed wywołaniem, a nawet jeśli ulegnie zmianie, nadal musi mieć prawidłową wartość dla powrotu. Adnotacja określa funkcja mogą swobodnie odczytywać i zapisać w buforze jeden element. Obiekt wywołujący musi dostarczyć buforu i zainicjować go.  
  
> [!NOTE]
>  Podobnie jak `_Out_`, `_Inout_` muszą być stosowane do wartości można modyfikować.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // 'pInt' should not be NULL  
}  
  
```  
  
 Kod — analiza Visual Studio sprawdza, czy obiekty wywołujące przekazać wskaźnika inną niż NULL do zainicjowane buforu dla `pInt`oraz że przed powrotem, `pInt` jest nadal różna od NULL i zainicjowano bufor.  
  
### <a name="example-the-inoutopt-annotation"></a>Przykład: _Inout_opt\_ adnotacji  
 `_Inout_opt_`jest taka sama jak `_Inout_`, z wyjątkiem tego, że parametr wejściowy może mieć wartości NULL i, w związku z tym funkcja należy sprawdzić, czy to.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Kod — analiza Visual Studio sprawdza, czy ta funkcja sprawdza NULL przed uzyskuje dostęp do buforu, a jeśli `pInt` nie ma wartości NULL, że rozmiar buforu jest inicjowany przez funkcję przed zwróceniem.  
  
### <a name="example-the-outptr-annotation"></a>Przykład: _Outptr\_ adnotacji  
 `_Outptr_`Służy do dodawania adnotacji parametr, który ma być przeznaczona do zwraca wskaźnik.  Parametr sam nie powinna być równa NULL i wywołana funkcja zwraca wskaźnik inną niż NULL i danymi zainicjowanymi wskazuje ten wskaźnik.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Kod — analiza Visual Studio weryfikuje wywołujący wskaźnik inną niż NULL `*pInt`, oraz że buforu został zainicjowany przez funkcję przed zwróceniem.  
  
### <a name="example-the-outptropt-annotation"></a>Przykład: _Outptr_opt\_ adnotacji  
 `_Outptr_opt_`jest taka sama jak `_Outptr_`, z wyjątkiem tego, że parametr jest opcjonalny — wywołującego można przekazać wskaźnik NULL dla parametru.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Kod — analiza Visual Studio weryfikuje, czy ta funkcja sprawdza NULL przed `*pInt` jest wyłuskiwany, a bufor jest inicjowany przez funkcję przed zwróceniem.  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>Przykład: _Success\_ adnotacji w połączeniu z _poziomie\_  
 Adnotacje może odnosić się do większości obiektów.  W szczególności może dodawać adnotacje do całej funkcji.  Jest jedną z najbardziej oczywisty właściwości funkcji, można go powodzenie lub niepowodzenie. Ale jak skojarzenie między buforu i jego rozmiar, C/C++ nie express funkcja powodzenie lub niepowodzenie. Za pomocą `_Success_` adnotacji, powiedzieć, jakie sukces dla funkcji.  Parametr `_Success_` adnotacja jest tylko wyrażenia, że gdy ma wartość true wskazuje, że funkcja zakończyła się pomyślnie. Wyrażenie może być wszystko, co może obsłużyć analizatora składni adnotacji. Efekty adnotacje po funkcja zwraca mają zastosowanie tylko wtedy, gdy funkcja zakończy się pomyślnie. W tym przykładzie pokazano sposób `_Success_` współdziała z `_Out_` co zrobić. Można użyć słowa kluczowego `return` do reprezentowania wartości zwracanej.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 `_Out_` Adnotacji powoduje, że program Visual Studio analizy kodu do sprawdzania poprawności wywołujący wskaźnik inną niż NULL w buforze dla `pInt`, oraz że buforu został zainicjowany przez funkcję przed zwróceniem.  
  
## <a name="sal-best-practice"></a>Najlepszym rozwiązaniem SAL  
  
### <a name="adding-annotations-to-existing-code"></a>Dodawanie adnotacji do istniejącego kodu  
 SAL to technologia Zaawansowane w celu poprawy bezpieczeństwa i niezawodności kodu. Po SAL możesz dowiedzieć się, można zastosować nowych umiejętności do codziennej pracy. W nowy kod można używać na podstawie SAL specyfikacje zgodnie z projektem w całym; w przypadku starszego kodu można przyrostowo dodawać adnotacje i zwiększając korzyści za każdym razem, gdy.  
  
 Nagłówki publicznych firmy Microsoft ma już adnotacji. W związku z tym zaleca się, że w projektach najpierw dodawania adnotacji do funkcji węzeł liścia i funkcji, które wywołują API Win32, aby maksymalnie wykorzystać zalety.  
  
### <a name="when-do-i-annotate"></a>Gdy adnotacji  
 Poniżej przedstawiono kilka wskazówek:  
  
-   Dodawanie adnotacji wszystkie parametry wskaźnika.  
  
-   Adnotacji adnotacje zakres wartości, dzięki czemu kod — analiza może zapewnić bezpieczeństwo buforu i wskaźnika.  
  
-   Dodawanie adnotacji reguły blokowania i blokowania efekty uboczne. Aby uzyskać więcej informacji, zobacz [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md).  
  
-   Dodawanie adnotacji, sterowników i inne właściwości specyficzne dla domeny.  
  
 Lub może dodawać adnotacje do wszystkich parametrów z konwersji wyczyść w całym i ułatwiają Sprawdź, czy zostały wykonane adnotacji.  
  
## <a name="related-resources"></a>Powiązane zasoby  
 [Blog zespołu ds. analizy kodu](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji SAL w celu redukowanie defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)   
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)   
 [Określanie, kiedy i gdzie dotyczy adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Najlepsze praktyki i przykłady](../code-quality/best-practices-and-examples-sal.md)