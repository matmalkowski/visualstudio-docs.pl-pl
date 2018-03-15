---
title: Format specyfikatory debugera (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b7efb90e6f2a2489fffb890c664393252021e6f
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Specyfikatory formatu w C++ w debugerze programu Visual Studio
Można zmienić format wyświetlania wartości w **czujki** okna używanie specyfikatorów formatu.  
  
 Umożliwia także specyfikatory formatu w **Immediate** okna, **polecenia** okna w [tracepoints](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints), a nawet w systemie windows źródła. Jeśli zostanie wstrzymana na wyrażeniu w oknach, wynik zostanie wyświetlony etykietek danych. Wyświetlanie etykietek danych odzwierciedla specyfikator formatu.  
  
> [!NOTE]
>  Po zmianie natywny debuger programu Visual Studio do nowy aparat debugowania, niektóre nowe specyfikatory formatu zostały dodane, a niektóre stare zostały usunięte. Starsze debugera jest nadal używana po wykonaniu interop (mieszany natywne i zarządzane) debugowania za pomocą języka C + +/ CLI. W poniższych sekcjach w tym temacie przedstawiono specyfikatory formatu dla każdego aparatu debugowania.
>   
>  -   [Specyfikatory formatu](#BKMK_Visual_Studio_2012_format_specifiers) opisuje specyfikatory formatu w nowy aparat debugowania.  
> -   [Format specyfikatory debugowania międzyoperacyjnego z C + +/ CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) opisuje specyfikatory formatu w starszych silnik debugowania.  
  
## <a name="using-format-specifiers"></a>Używanie specyfikatorów formatu  
 Jeśli masz następujący kod:  
  
```C++  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Dodaj `my_var1` zmienną **czujki** okna (podczas debugowania, **debugowania > Windows > czujki > Obejrzyj 1**), a następnie ustaw wyświetlania w postaci szesnastkowej (w **Obejrzyj**okna, kliknij prawym przyciskiem myszy zmienną i wybierz **wyświetlacz**). Okno czujki zawiera obecnie zawiera wartość 0x0065. Aby zobaczyć tę wartość, wyrażone jako znak zamiast całkowitą w kolumnie Nazwa po nazwie zmiennej, Dodaj znak specyfikator formatu **, c**. **Wartość** kolumny pojawi się teraz z **101 "e"**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Specyfikatory formatu  
 W poniższych tabelach przedstawiono specyfikatory formatu można w programie Visual Studio. Specyfikatory pogrubione nie są obsługiwane w przypadku debugowania międzyoperacyjnego z C + +/ CLI.  
  
|Specyfikator|Format|Oryginalnej wartości czujki|Wartość wyświetlana|  
|---------------|------------|--------------------------|---------------------|  
|d|dziesiętną liczbą całkowitą|0x00000066|102|  
|o|ósemkową liczby całkowitej bez znaku|0x00000066|000000000146|  
|x<br /><br /> **h**|Szesnastkowa liczba całkowita|102|0xcccccccc|  
|X<br /><br /> **H**|Szesnastkowa liczba całkowita|102|0xCCCCCCCC|  
|c|pojedynczy znak|0x0065, c|101 "e"|  
|s|Const char * ciągu|\<Lokalizacja > "hello world"|"hello world"|  
|**sb**|Const char * ciąg (bez cudzysłowu)|\<Lokalizacja > "hello world"|Cześć ludzie|  
|s8|Ciąg UTF-8|\<Lokalizacja > "Jest â˜• Filiżanka kawy UTF-8"|"Jest ☕ Filiżanka kawy UTF-8"|
|**s8b**|Ciąg UTF-8 (bez cudzysłowu)|\<Lokalizacja > "hello world"|Cześć ludzie|  
|su|Ciąg Unicode (kodowania UTF-16)|\<Lokalizacja > L "hello world"|L "hello world"<br /><br /> U "hello world"|  
|Sub|Ciąg Unicode (UTF-16 kodowanie) (bez cudzysłowu)|\<Lokalizacja > L "hello world"|Cześć ludzie|  
|bstr|Ciągów BSTR|\<Lokalizacja > L "hello world"|L "hello world"|  
|env|Blok środowiska (ciąg zakończone o podwójnej precyzji null)|\<Lokalizacja > L "=:: =::\\\\"|L"=::=::\\\\\\0=C:=C:\\\\windows\\\\system32\\0ALLUSERSPROFILE=...|
|**s32**|Ciąg UTF-32|\<Lokalizacja > U "hello world"|U "hello world"|  
|**s32b**|Ciąg UTF-32 (bez cudzysłowu)|\<Lokalizacja > U "hello world"|Cześć ludzie|  
|**en**|enum|SATURDAY(6)|Sobota|  
|**hv**|Typ wskaźnika — wskazuje, że wartość wskaźnika jest sprawdzana jest wynik alokacji sterty w tablicy, na przykład `new int[3]`.|\<Lokalizacja > {\<pierwszego elementu członkowskiego >}|\<Lokalizacja > {\<pierwszego elementu członkowskiego >, \<drugiego elementu członkowskiego >,...}|  
|**na**|Pomija adres pamięci wskaźnika do obiektu.|\<Lokalizacja >, {elementu członkowskiego = wartość...}|{member=value...}|  
|**ND**|Wyświetla tylko klasy podstawowej informacje, ignorowanie klasy pochodne|`(Shape*) square` zawiera klasy podstawowej i pochodnej informacje o klasie|Wyświetla opierać tylko informacje o klasie|  
|hr|Kod błędu HRESULT lub Win32. (Debuger teraz dekoduje wyników HRESULT automatycznie, więc to specyfikator nie jest wymagany w przypadku.|S_OK|S_OK|  
|WC|Flaga klasy okna|0x0010|WC_DEFAULTCHAR|  
|wm|Liczby komunikatów systemu Windows|16|WM_CLOSE|  
|!|format RAW, ignorując wszystkie dostosowania widoków typu danych|\<dostosowane reprezentacja >|4|  
  
> [!NOTE]
>  Gdy **hv** specyfikatora formatu, debuger próbuje określić długość buforu i wyświetlić odpowiedniej liczby elementów. Ponieważ nie zawsze jest możliwe w dla debugera znaleźć dokładnego rozmiaru tablicy, należy używać określenie rozmiaru `(pBuffer,[bufferSize])` zawsze, gdy jest to możliwe. **Hv** specyfikator formatu jest przeznaczony dla scenariuszy, których rozmiar buforu nie jest jeszcze dostępna  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Specyfikatory rozmiar dla wskaźników jako tablic  
 Jeśli masz wskaźnik do obiektu, który ma być wyświetlany jako tablica służy całkowitą lub wyrażenie, aby określić liczbę elementów tablicy:  
  
|Specyfikator|Format|Oryginalnej wartości czujki|Wartość wyświetlana|  
|---------------|------------|---------------------------|---------------------|  
|n|Dziesiętną lub **szesnastkową** liczba całkowita|pBuffer, [32]<br /><br /> pBuffer,**[0x20]**|Wyświetla `pBuffer` jako tablica 32 element.|  
|**[exp]**|Prawidłowe wyrażenie C++, którego wynikiem jest liczbą całkowitą.|pBuffer, [bufferSize]|Wyświetla pBuffer jako tablica `bufferSize` elementów.|  
|**expand(n)**|Prawidłowe wyrażenie języka C++, którego wynikiem jest liczbą całkowitą|pBuffer, expand(2)|Wyświetla trzeci element  `pBuffer`|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Format specyfikatory debugowania międzyoperacyjnego z C + +/ CLI  
 Specyfikatory w **bold** są obsługiwane tylko w przypadku debugowania natywnego i C + +/ CLI kodu.  
  
|Specyfikator|Format|Oryginalnej wartości czujki|Wartość wyświetlana|  
|---------------|------------|--------------------------|---------------------|  
|**d, i**|decimal liczbę całkowitą ze znakiem|0xF000F065|-268373915|  
|**u**|niepodpisane dziesiętną liczbą całkowitą|0x0065|101|  
|o|ósemkową liczby całkowitej bez znaku|0xF065|0170145|  
|x,X|Szesnastkowa liczba całkowita|61541|0x0000f065|  
|**g, h**|Prefiks długich i krótkich: d, i, u, o x X|00406042|0x0c22|  
|**f**|podpisana zmiennoprzecinkowych|(3./2.), f|1.500000|  
|**e**|Notacja naukowa podpisem|(3.0/2.0)|1.500000e+000|  
|**g**|podpisana zmiennoprzecinkowa lub podpisany notacji naukowej, zależności jest krótszy|(3.0/2.0)|1.5|  
|c|pojedynczy znak|\<Lokalizacja >|101 "e"|  
|s|Const char *|\<Lokalizacja >|"hello world"|  
|su|wchar_t const *<br /><br /> Const char16_t\*|\<Lokalizacja >|L "hello world"|  
|Sub|wchar_t const *<br /><br /> Const char16_t\*|\<Lokalizacja >|Cześć ludzie|  
|s8|Const char *|\<Lokalizacja >|"hello world"|  
|hr|Kod błędu HRESULT lub Win32. (Debuger teraz dekoduje wyników HRESULT automatycznie, więc to specyfikator nie jest wymagany w przypadku.|S_OK|S_OK|  
|WC|Flaga klasy okna.|0x00000040,|WC_DEFAULTCHAR|  
|wm|Liczby komunikatów systemu Windows|0x0010|WM_CLOSE|  
|!|format RAW, ignorując wszystkie dostosowania widoków typu danych|\<dostosowane reprezentacja >|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Format lokalizacji pamięci Specyfikatory w debugowania międzyoperacyjnego z C + +/ CLI  
 Poniższa tabela zawiera formatowania symbole używane w przypadku lokalizacji pamięci. Umożliwia określenie lokalizacji pamięci z dowolna wartość lub wyrażenie obliczane do lokalizacji.  
  
|Symbol|Format|Oryginalnej wartości czujki|Wartość wyświetlana|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 znaki ASCII|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|16 bajtów w formacie szesnastkowym, a następnie 16 znaków ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&..|  
|**mb**|16 bajtów w formacie szesnastkowym, a następnie 16 znaków ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&..|  
|**mw**|8 słowa|0x0012ffac|0X0012FFAC 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 doublewords|0x0012ffac|0X0012FFAC 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 quadwords|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|2-bajtowych znaków (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Określenie rozmiaru dla wskaźników jako tablic w debugowania międzyoperacyjnego z C + +/ CLI  
 Jeśli masz wskaźnik do obiektu, który ma być wyświetlany jako tablica umożliwia całkowitą Określ liczbę elementów tablicy:  
  
|Specyfikator|Format|Wyrażenie|Wartość wyświetlana|  
|---------------|------------|----------------|---------------------|  
|n|dziesiętną liczbą całkowitą|pBuffer [32]|Wyświetla `pBuffer` jako tablica 32 element.|
