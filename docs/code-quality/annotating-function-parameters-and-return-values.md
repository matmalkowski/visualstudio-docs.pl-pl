---
title: "Dodawanie adnotacji do parametrów funkcji i zwracanych wartości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ac25f8bbda4431850f613f2b41b1d9ed4908c118
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="annotating-function-parameters-and-return-values"></a>Dodawanie adnotacji do parametrów funkcji i zwracanych wartości
W tym artykule opisano typowe zastosowania adnotacji do parametrów funkcji proste — wartości skalarne i wskaźniki do struktur i klas — i większość typów buforów.  W tym artykule przedstawiono również typowe wzorce użycia dla adnotacji. Aby uzyskać dodatkowe adnotacje dotyczące funkcji, zobacz [zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>Parametry wskaźnika  
 Dla adnotacji w poniższej tabeli gdy parametr wskaźnika jest adnotacją, analizatora zgłasza błąd, jeśli wskaźnik jest null.  Dotyczy to wskaźniki i dowolnego elementu danych, która jest wskazywana.  
  
 **Adnotacje wraz z opisami**  
  
-   `_In_`  
  
     Oznacza parametrów wejściowych, które są wartości skalarne, struktury, wskaźniki do struktur i tym podobne.  Jawnie może być używana dla prostego wartości skalarne.  Parametr musi być w stanie wstępnego nieprawidłowy i nie zostaną zmodyfikowane.  
  
-   `_Out_`  
  
     Oznacza parametrów wyjściowych, które są wartości skalarne, struktury, wskaźniki do struktur i tym podobne.  Dotyczy to obiekt, który nie może zwracać wartości — na przykład wartością skalarną, który jest przekazywany przez wartość.  Parametr musi być prawidłową, w stanie wstępnego, ale musi być w stanie po prawidłowy.  
  
-   `_Inout_`  
  
     Oznacza parametru, która ma zostać zmieniona przez funkcję.  Musi być w stanie przed i po stanie prawidłowy, ale przyjęto, że mają różne wartości przed i po wywołaniu. Stosuje się do wartości można modyfikować.  
  
-   `_In_z_`  
  
     Wskaźnik do zerem ciąg, który jest używany jako dane wejściowe.  Nieprawidłowy ciąg musi być w stanie wstępnego.  Rodzaje `PSTR`, który już ma poprawne adnotacje, są preferowane.  
  
-   `_Inout_z_`  
  
     Wskaźnik do tablicy znaków zakończony znakiem null, które zostaną zmodyfikowane.  Musi być prawidłową przed i po wywołaniu metody, ale wartość przyjęto, że zostały zmienione.  Mogą być przenoszone terminatorem null, ale mogą być używane tylko elementy do oryginalnego terminatorem null.  
  
-   `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     Wskaźnik do tablicy, który jest odczytywany przez funkcję.  Tablica jest rozmiaru `s` elementów, które muszą być prawidłowe.  
  
     `_bytes_` Variant daje rozmiar w bajtach zamiast elementów. Użyj tego tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyje ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy podobnych funkcji `wchar_t` czy.  
  
-   `_In_reads_z_(s)`  
  
     Wskaźnik do tablicy zerem i ma rozmiaru znane. Elementy do terminatorem null — lub `s` Jeśli nie istnieje żadne terminatorem null — musi być w stanie wstępnego prawidłowy.  Jeśli znane jest rozmiar w bajtach, skalowanie `s` według rozmiaru elementu.  
  
-   `_In_reads_or_z_(s)`  
  
     Wskaźnik do tablicy jest zakończony wartością null lub ma rozmiaru znane lub oba. Elementy do terminatorem null — lub `s` Jeśli nie istnieje żadne terminatorem null — musi być w stanie wstępnego prawidłowy.  Jeśli znane jest rozmiar w bajtach, skalowanie `s` według rozmiaru elementu.  (Używane dla `strn` rodziny.)  
  
-   `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Wskaźnik do tablicy `s` elementów (w bajtach komp), które będą zapisywane przez funkcję.  Elementy tablicy musi być prawidłową, w stanie wstępnego, a liczba elementów, które są dozwolone w stanie po jest nieokreślony.  W przypadku adnotacje na typ parametru, są stosowane po stanu. Rozważmy na przykład następujący kod.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     W tym przykładzie, wywołujący zapewnia bufor `size` elementy `p1`.  `MyStringCopy`sprawia, że niektóre z tych elementów prawidłową. Co więcej `_Null_terminated_` adnotacji na `PWSTR` oznacza, że `p1` jest zakończony wartością null w stanie po.  W ten sposób liczbę elementów prawidłową jest nadal dobrze zdefiniowany, ale liczba określony element nie jest wymagana.  
  
     `_bytes_` Variant daje rozmiar w bajtach zamiast elementów. Użyj tego tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyje ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy podobnych funkcji `wchar_t` czy.  
  
-   `_Out_writes_z_(s)`  
  
     Wskaźnik do tablicy `s` elementów.  Nie masz elementy był prawidłowy w stanie wstępnego.  W stanie po, elementów się przy użyciu terminatorem null — musi być obecny — musi być prawidłowy.  Jeśli znane jest rozmiar w bajtach, skalowanie `s` według rozmiaru elementu.  
  
-   `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Wskaźnik do tablicy, która jest zarówno odczytanych i zapisanych w funkcji.  Jest rozmiaru `s` elementów i prawidłowy w stanie przed i po stanu.  
  
     `_bytes_` Variant daje rozmiar w bajtach zamiast elementów. Użyj tego tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyje ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy podobnych funkcji `wchar_t` czy.  
  
-   `_Inout_updates_z_(s)`  
  
     Wskaźnik do tablicy zerem i ma rozmiaru znane. Elementy się za pośrednictwem terminatorem null — musi być obecny — musi być w stanie przed i po stanie prawidłowy.  Wartość w stanie po zakłada, że różni się od wartości w stanie wstępnego; obejmują one lokalizacji terminatorem null. Jeśli znane jest rozmiar w bajtach, skalowanie `s` według rozmiaru elementu.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Wskaźnik do tablicy `s` elementów.  Nie masz elementy był prawidłowy w stanie wstępnego.  W stanie po, elementy do `c`- Ty element musi być prawidłowy.  Jeśli znane jest rozmiar w bajtach, skalowanie `s` i `c` według rozmiaru elementu lub użyj `_bytes_` variant, który jest zdefiniowany jako:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Innymi słowy, każdy element, który istnieje w buforze do `s` w stanie wstępnego jest prawidłowy w stanie po.  Na przykład:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Wskaźnik do tablicy, która jest zarówno do odczytu i zapisywane przez funkcję.  Jest rozmiaru `s` elementów, które musi być prawidłową w stanie wstępnego, i `c` elementów musi być prawidłową, w stanie po.  
  
     `_bytes_` Variant daje rozmiar w bajtach zamiast elementów. Użyj tego tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyje ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy podobnych funkcji `wchar_t` czy.  
  
-   `_Inout_updates_z_(s)`  
  
     Wskaźnik do tablicy zerem i ma rozmiaru znane. Elementy się za pośrednictwem terminatorem null — musi być obecny — musi być w stanie przed i po stanie prawidłowy.  Wartość w stanie po zakłada, że różni się od wartości w stanie wstępnego; obejmują one lokalizacji terminatorem null. Jeśli znane jest rozmiar w bajtach, skalowanie `s` według rozmiaru elementu.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Wskaźnik do tablicy `s` elementów.  Nie masz elementy był prawidłowy w stanie wstępnego.  W stanie po, elementy do `c`- Ty element musi być prawidłowy.  Jeśli znane jest rozmiar w bajtach, skalowanie `s` i `c` według rozmiaru elementu lub użyj `_bytes_` variant, który jest zdefiniowany jako:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Innymi słowy, każdy element, który istnieje w buforze do `s` w stanie wstępnego jest prawidłowy w stanie po.  Na przykład:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Wskaźnik do tablicy, która jest zarówno do odczytu i zapisywane przez funkcję.  Jest rozmiaru `s` elementów, które musi być prawidłową w stanie wstępnego, i `c` elementów musi być prawidłową, w stanie po.  
  
     `_bytes_` Variant daje rozmiar w bajtach zamiast elementów. Użyj tego tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyje ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy podobnych funkcji `wchar_t` czy.  
  
-   `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Wskaźnik do tablicy, która jest zarówno do odczytu i zapisywane przez funkcję rozmiar `s` elementów. Określone jako równoważne:  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     Innymi słowy, każdy element, który istnieje w buforze do `s` w stanie wstępnego jest prawidłowy w stanie przed i po stanu.  
  
     `_bytes_` Variant daje rozmiar w bajtach zamiast elementów. Użyj tego tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyje ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy podobnych funkcji `wchar_t` czy.  
  
-   `_In_reads_to_ptr_(p)`  
  
     Wskaźnika do tablicy, dla której wyrażenie `p`  -  `_Curr_` (to znaczy `p` minus `_Curr_`) jest definiowana za pomocą standardowych odpowiedni język.  Elementy przed `p` musi być w stanie wstępnego prawidłowy.  
  
-   `_In_reads_to_ptr_z_(p)`  
  
     Wskaźnik do tablicą zerem, dla której wyrażenie `p`  -  `_Curr_` (oznacza to, `p` minus `_Curr_`) jest definiowana za pomocą standardowych odpowiedni język.  Elementy przed `p` musi być w stanie wstępnego prawidłowy.  
  
-   `_Out_writes_to_ptr_(p)`  
  
     Wskaźnika do tablicy, dla której wyrażenie `p`  -  `_Curr_` (to znaczy `p` minus `_Curr_`) jest definiowana za pomocą standardowych odpowiedni język.  Elementy przed `p` musi być prawidłową, w stanie wstępnego i musi być w stanie po prawidłowy.  
  
-   `_Out_writes_to_ptr_z_(p)`  
  
     Wskaźnik do tablicą zerem, dla której wyrażenie `p`  -  `_Curr_` (oznacza to, `p` minus `_Curr_`) jest definiowana za pomocą standardowych odpowiedni język.  Elementy przed `p` musi być prawidłową, w stanie wstępnego i musi być w stanie po prawidłowy.  
  
## <a name="optional-pointer-parameters"></a>Parametry opcjonalne wskaźnika  
 Jeżeli zawiera adnotację wskaźnika parametru `_opt_`, oznacza to, że parametr może mieć wartości null. W przeciwnym razie wykonuje taka sama jak wersja, która nie zawiera adnotację `_opt_`. Oto lista `_opt_` wariantów adnotacje parametru wskaźnika:  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Parametry wyjściowe wskaźnika  
 Parametry wyjściowe wskaźnika wymagają specjalnych notacji do odróżniania null przetwarzaniem na parametr i lokalizacji wskazywanej do.  
  
 **Adnotacje wraz z opisami**  
  
-   `_Outptr_`  
  
     Parametr nie może mieć wartości null, a w stanie po wskazywana do lokalizacji docelowej nie może mieć wartości null i musi być prawidłowy.  
  
-   `_Outptr_opt_`  
  
     Parametr może mieć wartości null, ale w stanie po wskazywana do lokalizacji docelowej nie może mieć wartości null i musi być prawidłowy.  
  
-   `_Outptr_result_maybenull_`  
  
     Parametr nie może mieć wartości null, a w stanie po lokalizacji wskazywanej do może mieć wartości null.  
  
-   `_Outptr_opt_result_maybenull_`  
  
     Parametr może mieć wartości null, a w stanie po lokalizacji wskazywanej do może mieć wartości null.  
  
 W poniższej tabeli dodatkowe podciągów są wstawiane do nazwa adnotacji, aby bardziej szczegółowo znaczenie adnotacji.  Podciągi różnych `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, i `_to_`.  
  
> [!IMPORTANT]
>  Jeśli interfejs, który jest dodawanie adnotacji do modelu COM, formularz COM tych adnotacji. Nie należy używać adnotacje COM z dowolnego typu interfejsu.  
  
 **Adnotacje wraz z opisami**  
  
-   `_Outptr_result_z_`  
  
     `_Outptr_opt_result_z_`  
  
     `_Outptr_result_maybenull_z_`  
  
     `_Ouptr_opt_result_maybenull_z_`  
  
     Został zwrócony wskaźnik `_Null_terminated_` adnotacji.  
  
-   `_COM_Outptr_`  
  
     `_COM_Outptr_opt_`  
  
     `_COM_Outptr_result_maybenull_`  
  
     `_COM_Outptr_opt_result_maybenull_`  
  
     Zwrócony wskaźnik ma semantykę COM i dlatego `_On_failure_` po warunkiem, że zwrócony wskaźnik ma wartość null.  
  
-   `_Outptr_result_buffer_(s)`  
  
     `_Outptr_result_bytebuffer_(s)`  
  
     `_Outptr_opt_result_buffer_(s)`  
  
     `_Outptr_opt_result_bytebuffer_(s)`  
  
     Zwrócony wskaźnik wskazuje nieprawidłowy bufor o rozmiarze `s` elementy lub bajtów.  
  
-   `_Outptr_result_buffer_to_(s, c)`  
  
     `_Outptr_result_bytebuffer_to_(s, c)`  
  
     `_Outptr_opt_result_buffer_to_(s,c)`  
  
     `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
     Zwrócony wskaźnik wskazuje bufor o rozmiarze `s` elementy lub bajtów, z których pierwszy `c` są prawidłowe.  
  
 Konwencje niektórych interfejsu zakładają, że parametry wyjściowe są zniweczone w przypadku awarii.  Z wyjątkiem jawnie kod modelu COM. formularzy w poniższej tabeli są preferowane.  Kod modelu COM należy użyć odpowiedniego formularze COM, które są wymienione w poprzedniej sekcji.  
  
 **Adnotacje wraz z opisami**  
  
-   `_Result_nullonfailure_`  
  
     Modyfikuje innych adnotacji. Wynik jest ustawiona na wartość null, jeśli funkcja nie powiedzie się.  
  
-   `_Result_zeroonfailure_`  
  
     Modyfikuje innych adnotacji. Wynik jest ustawiony na zero, jeśli funkcja nie powiedzie się.  
  
-   `_Outptr_result_nullonfailure_`  
  
     Zwrócony wskaźnik wskazuje prawidłowego buforu, jeśli funkcja zakończy się powodzeniem lub wartość null, jeśli funkcja nie powiedzie się. Ta adnotacja jest parametru opcjonalne.  
  
-   `_Outptr_opt_result_nullonfailure_`  
  
     Zwrócony wskaźnik wskazuje prawidłowego buforu, jeśli funkcja zakończy się powodzeniem lub wartość null, jeśli funkcja nie powiedzie się. Ta adnotacja jest parametrem opcjonalnym.  
  
-   `_Outref_result_nullonfailure_`  
  
     Zwrócony wskaźnik wskazuje prawidłowego buforu, jeśli funkcja zakończy się powodzeniem lub wartość null, jeśli funkcja nie powiedzie się. Ta adnotacja jest dla parametru odwołania.  
  
## <a name="output-reference-parameters"></a>Parametry wyjściowe odwołania  
 Zazwyczaj parametru odwołania jest używane dla parametrów wyjściowych.  Dla parametrów odwołania prosty wyjściowy — na przykład `int&`—`_Out_` zawiera poprawne semantyki.  Jednakże, gdy wartość wyjściowa jest wskaźnik — na przykład `int *&`— adnotacje równoważne wskaźnika, takich jak `_Outptr_ int **` nie zapewniają poprawne semantyki.  Aby zwięzłym express semantykę odwołania parametrów wyjściowych typów wskaźnika, należy użyć złożonego adnotacje:  
  
 **Adnotacje wraz z opisami**  
  
-   `_Outref_`  
  
     Wynik musi być w stanie po nieprawidłowy i nie może mieć wartości null.  
  
-   `_Outref_result_maybenull_`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie po.  
  
-   `_Outref_result_buffer_(s)`  
  
     Wynik musi być w stanie po nieprawidłowy i nie może mieć wartości null. Wskazuje nieprawidłowy bufor o rozmiarze `s` elementów.  
  
-   `_Outref_result_bytebuffer_(s)`  
  
     Wynik musi być w stanie po nieprawidłowy i nie może mieć wartości null. Wskazuje nieprawidłowy bufor o rozmiarze `s` bajtów.  
  
-   `_Outref_result_buffer_to_(s, c)`  
  
     Wynik musi być w stanie po nieprawidłowy i nie może mieć wartości null. Wskazuje buforu `s` elementów, z których pierwszy `c` są prawidłowe.  
  
-   `_Outref_result_bytebuffer_to_(s, c)`  
  
     Wynik musi być w stanie po nieprawidłowy i nie może mieć wartości null. Wskazuje buforu `s` bajtów, z których pierwszy `c` są prawidłowe.  
  
-   `_Outref_result_buffer_all_(s)`  
  
     Wynik musi być w stanie po nieprawidłowy i nie może mieć wartości null. Wskazuje nieprawidłowy bufor o rozmiarze `s` elementów prawidłową.  
  
-   `_Outref_result_bytebuffer_all_(s)`  
  
     Wynik musi być w stanie po nieprawidłowy i nie może mieć wartości null. Wskazuje nieprawidłowy bufor `s` bajtów elementów prawidłową.  
  
-   `_Outref_result_buffer_maybenull_(s)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie po. Wskazuje nieprawidłowy bufor o rozmiarze `s` elementów.  
  
-   `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie po. Wskazuje nieprawidłowy bufor o rozmiarze `s` bajtów.  
  
-   `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie po. Wskazuje buforu `s` elementów, z których pierwszy `c` są prawidłowe.  
  
-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie post. Wskazuje buforu `s` bajtów, z których pierwszy `c` są prawidłowe.  
  
-   `_Outref_result_buffer_all_maybenull_(s)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie post. Wskazuje nieprawidłowy bufor o rozmiarze `s` elementów prawidłową.  
  
-   `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie post. Wskazuje nieprawidłowy bufor `s` bajtów elementów prawidłową.  
  
## <a name="return-values"></a>Wartości zwrócone  
 Wartość zwracana funkcji podobny `_Out_` parametru, ale jest na innym poziomie de-reference i nie należy wziąć pod uwagę pojęcie wskaźnika do wyniku.  Dla następujących adnotacji, wartość zwracana jest obiektem adnotacjami — skalarnej, wskaźnik do struktury lub wskaźnikiem w buforze. Adnotacje te mają tej samej semantyki jako odpowiednie `_Out_` adnotacji.  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>Inne typowe adnotacji  
 **Adnotacje wraz z opisami**  
  
-   `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Parametr, pole lub wynik jest z zakresu (włącznie) z `low` do `hi`.  Odpowiednikiem `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` do obiektu adnotacjami oraz odpowiednich warunków wstępnie stanu lub używanego po utworzeniu stanu zastosowano.  
  
    > [!IMPORTANT]
    >  Chociaż nazwy zawierają "in" i "out", semantykę `_In_` i `_Out_` czy **nie** dotyczą te adnotacji.  
  
-   `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     Wartość adnotacjami jest dokładnie `expr`.  Odpowiednikiem `_Satisfies_(_Curr_ == expr)` do obiektu adnotacjami oraz odpowiednich warunków wstępnie stanu lub używanego po utworzeniu stanu zastosowano.  
  
-   `_Struct_size_bytes_(size)`  
  
     Ma zastosowanie do deklaracji struktury lub klasy.  Wskazuje, czy prawidłowy obiekt tego typu może być większa niż deklarowany typ, liczbę bajtów podawana przez `size`.  Na przykład:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     Rozmiar buforu w bajtach parametru `pM` typu `MyStruct *` następnie przyjmuje się:  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>Powiązane zasoby  
 [Blog zespołu ds. analizy kodu](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji SAL w celu redukowanie defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Poznanie SAL](../code-quality/understanding-sal.md)   
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)   
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)   
 [Określanie, kiedy i gdzie dotyczy adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)   
 [Najlepsze praktyki i przykłady](../code-quality/best-practices-and-examples-sal.md)