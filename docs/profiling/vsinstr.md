---
title: Narzędzie VSInstr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15fa479a5ce9a27b3723359f65a4436af8caff16
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="vsinstr"></a>VSInstr
Narzędzie VSInstr służy do Instrumentacja plików binarnych. Jest wywoływana przy użyciu następującej składni:  
  
```  
VSInstr [/U] filename [/options]  
```  
  
 W poniższej tabeli opisano opcje narzędzia VSInstr:  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**Pomoc** lub **?**|Wyświetla Pomoc.|  
|**U**|Zapisuje dane wyjściowe z konsoli przekierowanego jako Unicode. Musi być pierwszą określoną opcją.|  
|`@filename`|Określa nazwę pliku odpowiedzi, który zawiera jedną z opcji w wierszu polecenia.  Nie należy używać znaków cudzysłowu.|  
|**OutputPath** `:path`|Określa katalog docelowy dla obrazu z Instrumentacją. Jeśli nie określono ścieżki wyjściowej, oryginalnego pliku binarnego zostanie zmieniona przez dodanie "Orig" do nazwy pliku w tym samym katalogu, i został zinstrumentowany kopię pliku binarnego.|  
|**Wyklucz** `:funcspec`|Określa specyfikację funkcji do wykluczenia z Instrumentacji przez sondy. Jest przydatne w przypadku profilowania wstawieniem sondy w funkcji powoduje, że nieprzewidywalne lub niepożądane wyniki.<br /><br /> Nie używaj **wykluczyć** i **Include** opcje, które odwołują się do funkcji tego samego pliku binarnego.<br /><br /> Można określić wiele Specyfikacja funkcji z oddzielnym **wykluczyć** opcje.<br /><br /> `funcspec` jest zdefiniowana jako:<br /><br /> [przestrzeń nazw\<separator1 >] [klasa\<separator2 >] — funkcja<br /><br /> \<separator1 > jest `::` dla kodu natywnego i `.` dla kodu zarządzanego.<br /><br /> \<separator2 > jest zawsze `::`<br /><br /> **Wyklucz** jest obsługiwany z pokrycia kodu.<br /><br /> Symbol wieloznaczny \* jest obsługiwana. Na przykład, aby wykluczyć wszystkie funkcje w przestrzeni nazw, użyj:<br /><br /> MyNamespace::\*<br /><br /> Można użyć **VSInstr /DumpFuncs** do pełnej nazwy funkcji w określonym pliku binarnego.|  
|**Obejmują** `:funcspec`|Określa Specyfikacja funkcji w pliku binarnym instrumentem sondy. Wszystkie funkcje w plikach binarnych nie są instrumentowane.<br /><br /> Można określić wiele funkcji specyfikacji z oddzielnym **Include** opcje.<br /><br /> Nie używaj **Include** i **wykluczyć** opcje, które odwołują się do funkcji tego samego pliku binarnego.<br /><br /> **Obejmują** nie jest obsługiwany z pokrycia kodu.<br /><br /> `funcspec` jest zdefiniowana jako:<br /><br /> [przestrzeń nazw\<separator1 >] [klasa\<separator2 >] — funkcja<br /><br /> \<separator1 > jest `::` dla kodu natywnego i `.` dla kodu zarządzanego.<br /><br /> \<separator2 > jest zawsze `::`<br /><br /> Symbol wieloznaczny \* jest obsługiwana. Na przykład, aby uwzględnić wszystkie funkcje w przestrzeni nazw, użyj:<br /><br /> MyNamespace::\*<br /><br /> Można użyć **VSInstr /DumpFuncs** do pełnej nazwy funkcji w określonym pliku binarnego.|  
|**DumpFuncs**|Zawiera listę funkcji, które w określonym obrazie. Jest wykonywana żadna Instrumentacja.|  
|**ExcludeSmallFuncs**|Wyklucza małe funkcje, które są krótkich funkcji, które nie wprowadzaj żadnych wywołania funkcji z Instrumentacji. **ExcludeSmallFuncs** opcja zapewnia mniejsze koszty Instrumentacji szybkości w związku z tym ulepszone instrumentacji.<br /><br /> Wyłączenie małe funkcje zmniejsza rozmiar pliku Vsp i czas wymagany do analizy.|  
|**Znacznik:**{**przed**`&#124;`**po**`&#124;`**górnej**`&#124;`**dolnej**}`,funcname,markid`|Wstawia znacznik profilu (identyfikator używany do ograniczania danych w raportach) czy służy do identyfikowania początkowy lub końcowy zakresu danych w pliku Vsp raportu.<br /><br /> **Przed** — bezpośrednio przed wpisem docelowym funkcji.<br /><br /> **Po** — od razu po zamknięciu funkcja docelowej.<br /><br /> **TOP** — natychmiast po wejściu Funkcja docelowej.<br /><br /> **Dolny** — bezpośrednio przed każdego zwracane w funkcji docelowej.<br /><br /> `funcname` -Nazwy funkcji docelowego<br /><br /> `Markid` -Dodatnią liczbą całkowitą (Liczba długa) ma być używana jako identyfikator znacznika profilu.|  
|**Pokrycia**|Wykonuje Instrumentacji pokrycia. Może być może służyć tylko z następującymi opcjami: **pełne**, **OutputPath**, **wykluczyć**, i **Logfile**...|  
|**Pełne**|**Pełne**jest używana opcja, aby wyświetlić szczegółowe informacje na temat procesu instrumentacji.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|Pomiń wszystkie lub określone ostrzeżenia.<br /><br /> `Message Number` -numer ostrzeżenia. Jeśli `Message Number` jest pominięty, wszystkie ostrzeżenia są pomijane.<br /><br /> Aby uzyskać więcej informacji, zobacz [ostrzeżenia VSInstr](../profiling/vsinstr-warnings.md).|  
|**Formant** `:{` **wątku** `&#124;` **procesu** `&#124;` **globalne** `}`|Określa poziom profilowania następującej kolekcji danych VSInstr opcje sterowania:<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Wstrzymaj**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Wątek** — Określa funkcje kontroli zbierania danych na poziomie wątku. Profilowanie jest uruchomiona lub zatrzymana tylko dla bieżącego wątku. Nie dotyczy profilowania stan innych wątków. Wartość domyślna to wątku.<br /><br /> **Proces** — Określa funkcje kontroli zbierania danych poziomie procesu profilowania. Profilowanie uruchomienia lub zatrzymania dla wszystkich wątków w bieżącym procesie. Nie wpływa na stan profilowania innych procesów.<br /><br /> **Globalne** — Określa funkcje kontroli zbierania danych (międzyprocesowa) poziomie globalnym.<br /><br /> Jeśli nie określisz poziomu profilowania wystąpi błąd.|  
|**Uruchom** `:{` **wewnątrz** `&#124;` **zewnętrzne** `},funcname`|Ogranicza zbierania danych funkcji docelowych i podrzędny funkcji wywołanych przez tą funkcję.<br /><br /> **Wewnątrz** -Wstawia funkcję StartProfile natychmiast po wejściu funkcji docelowej. Wstawia funkcję StopProfile bezpośrednio przed powrotem każdego w funkcji docelowej.<br /><br /> **Poza metodą** -Wstawia funkcję StartProfile bezpośrednio przed każdym wywołaniu funkcji docelowej. Wstawia funkcję StopProfile natychmiast po każdym wywołaniu funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.|  
|**Wstrzymaj** `:{` **wewnątrz** `&#124;` **zewnętrzne** `},funcname`|Wyklucza zbierania danych dla docelowej funkcji i funkcji podrzędnych wywołanych przez funkcję.<br /><br /> **Wewnątrz** -Wstawia funkcję SuspendProfile natychmiast po wejściu funkcji docelowej. Wstawia funkcję ResumeProfile bezpośrednio przed powrotem każdego w funkcji docelowej.<br /><br /> **Poza metodą** -Wstawia funkcję SuspendProfile bezpośrednio przed wejściem do funkcji docelowej. Wstawia funkcję ResumeProfile natychmiast po opuszczenia funkcja docelowego.<br /><br /> `funcname` -Nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowy zawiera funkcję StartProfile, funkcja SuspendProfile dodaje się przed nim. Jeśli funkcja docelowy zawiera funkcję StopProfile, funkcja ResumeProfile są wstawiane po nim.|  
|**StartOnly:** `{` **przed** `&#124;` **po** `&#124;` **górnej** `&#124;` **dołu** `},funcname`|Rozpoczyna zbieranie danych w cyklu profilowania. Wstawia funkcję StartProfile interfejsu API w określonej lokalizacji.<br /><br /> **Przed** — bezpośrednio przed wpisem docelowym funkcji.<br /><br /> **Po** — od razu po zamknięciu funkcja docelowej.<br /><br /> **TOP** — natychmiast po wejściu Funkcja docelowej.<br /><br /> **Dolny** — bezpośrednio przed każdego zwracane w funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.|  
|**StopOnly:**{**przed**`&#124;`**po**`&#124;`**górnej**`&#124;`**dolnej**}`,funcname`|Zatrzymuje zbieranie danych w cyklu profilowania. Wstawia funkcję StopProfile w określonej lokalizacji.<br /><br /> **Przed** — bezpośrednio przed wpisem docelowym funkcji.<br /><br /> **Po** — od razu po zamknięciu funkcja docelowej.<br /><br /> **TOP** — natychmiast po wejściu Funkcja docelowej.<br /><br /> **Dolny** — bezpośrednio przed każdego zwracane w funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.|  
|**SuspendOnly:**{**przed**`&#124;`**po**`&#124;`**górnej**`&#124;`**dolnej**}`,funcname`|Zatrzymuje zbieranie danych w cyklu profilowania. Wstawia SuspendProfile interfejsu API w określonej lokalizacji.<br /><br /> **Przed** — bezpośrednio przed wpisem docelowym funkcji.<br /><br /> **Po** — od razu po zamknięciu funkcja docelowej.<br /><br /> **TOP** — natychmiast po wejściu Funkcja docelowej.<br /><br /> **Dolny** — bezpośrednio przed każdego zwracane w funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowy zawiera funkcję StartProfile, funkcja SuspendProfile dodaje się przed nim.|  
|**ResumeOnly:**{**przed**`&#124;`**po**`&#124;`**górnej**`&#124;`**dolnej**}`,funcname`|Rozpoczyna się lub wznawiania pracy zbierania danych w cyklu profilowania.<br /><br /> Zwykle jest używana do uruchomienia profilowania po **SuspendOnly** opcja została zatrzymana profilowania. Interfejs API ResumeProfile do wstawienia w określonej lokalizacji.<br /><br /> **Przed** — bezpośrednio przed wpisem docelowym funkcji.<br /><br /> **Po** — od razu po zamknięciu funkcja docelowej.<br /><br /> **TOP** — natychmiast po wejściu Funkcja docelowej.<br /><br /> **Dolny** — bezpośrednio przed każdego zwracane w funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowy zawiera funkcję StopProfile, funkcja ResumeProfile są wstawiane po nim.|  
  
## <a name="see-also"></a>Zobacz też  
 [Vsperfmon —](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Ostrzeżenia VSInstr](../profiling/vsinstr-warnings.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)