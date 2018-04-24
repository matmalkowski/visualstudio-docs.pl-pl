---
title: Ogólne, debugowanie, opcje ― Okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b153f5e411cabc8975ad1a2dca1ed212372b63ee
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="general-debugging-options-dialog-box"></a>Ogólne, debugowanie, okno dialogowe Opcje
**Narzędzia > Opcje > debugowanie > Ogólne** stronie można ustawić następujące opcje:  
  
**Pytaj przed usunięciem wszystkich punktów przerwania**  
Wymaga potwierdzenia przed ukończeniem **Usuń wszystkie punkty przerwania** polecenia.  
  
**Przerwij wszystkie procesy w przypadku przerwania jednego procesu**  
Dzieli jednocześnie wszystkie procesy, do których jest dołączony debuger, gdy występuje podział.  
  
**Przerwij, gdy wyjątki przekraczają AppDomain lub granic zarządzane lub natywne**  
W debugowania zarządzanego lub mieszanym, środowisko uruchomieniowe języka wspólnego można przechwytywać wyjątki, przekraczających granice domeny aplikacji lub zarządzane lub natywne granice, gdy są spełnione następujące warunki:  
  
1\) po kodu natywnego wywołuje zarządzanego kodu za pomocą międzyoperacyjności z modelem COM i kod zarządzany zgłasza wyjątek. Zobacz [wprowadzenie do COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) po kodu zarządzanego działającego w domenie aplikacji 1 wywołania kodu zarządzanego w domenie aplikacji 2 i kodu w domenie aplikacji 2 zgłasza wyjątek. Zobacz [programowania z domenami aplikacji](/dotnet/articles/framework/app-domains/index).  

3\) gdy kod wywołuje funkcję przy użyciu odbicia, a funkcja zwraca wyjątek. Zobacz [odbicia](/dotnet/framework/reflection-and-codedom/reflection).  
  
W warunku, 2 i 3, wyjątek jest czasami zgłoszony przez kod zarządzany w `mscorlib` zamiast środowisko uruchomieniowe języka wspólnego. Ta opcja nie dotyczy dzielenia na wyjątki przechwycony przez `mscorlib`.  
  
**Włącz debugowanie poziomie adresu**  
 Umożliwia zaawansowane funkcje do debugowania na poziomie adresu ( **dezasemblacji** okna, **rejestruje** okna, a punkty przerwania adresu).  
  
- **Pokaż dezasemblację, jeśli źródło jest niedostępne**  
    Automatycznie wyświetlany **dezasemblacji** okno podczas debugowania kodu, dla których źródła jest niedostępna.  
  
**Włącz punktu przerwania filtry**  
Można ustawić filtry w punktów przerwania, aby wpływają one na określone procesy, wątki lub komputery.  
 
**Użyj nowego pomocnika wyjątków**  
Umożliwia pomocnika wyjątków (Visual Studio 2017), który zastępuje Asystenta wyjątków.
  
> [!NOTE]
> Dla kodu zarządzanego, ta opcja była wcześniej określana **Włącz Asystenta wyjątków** . 
  
**Włącz opcję tylko mój kod**  
Wyświetla debugera i kroki do kodu użytkownika ("Mój kod"), ignorowanie kod systemu i innego kodu, która została zoptymalizowana lub, która nie ma symboli debugowania.

- **Ostrzegaj w przypadku braku kodu użytkownika przy uruchomieniu (tylko kod zarządzany)**  
    Podczas debugowania rozpoczyna się od włączono opcję tylko mój kod, ta opcja wyświetli ostrzeżenie, jeśli nie jest wykonywany kod użytkownika ("Mój kod"). 

**Włączyć program .NET Framework krokowe wykonywanie źródła**  
Umożliwia debugera wkraczać do źródła .NET Framework. Włączenie tej opcji powoduje automatyczne wyłączenie tylko mój kod .NET Framework symbole zostaną pobrane do lokalizacji pamięci podręcznej. Możesz zmienić lokalizację pamięci podręcznej w **opcje** okno dialogowe **debugowanie** kategorii, **symbole** strony.  
  
**Przekrocz nad właściwościami i operatorami (tylko kod zarządzany)**  
Debuger zapobiega Wkraczanie do właściwości i operatory w kodzie zarządzanym.  
  
**Włącz obliczanie właściwości i inne niejawne wywołania funkcji**  
Włącza funkcję automatycznej oceny właściwości i niejawna funkcja wywołuje w oknach zmiennych i **QuickWatch** okno dialogowe.  
  
- **Wywołania funkcji konwersji ciągów na obiektach w oknach zmiennych (C# i JavaScript tylko)**  
    Wykonuje wywołanie ciąg niejawna konwersja podczas obliczania obiektów w oknach zmiennych. W związku z tym że wynik jest wyświetlana jako ciągu zamiast nazwy typu. Ma zastosowanie tylko podczas debugowania w kodzie języka C#. To ustawienie może być zastąpiona przez atrybutu DebuggerDisplay (zobacz [za pomocą atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Włącz obsługę serwera źródłowego**  
Określa, że debuger programu Visual Studio można pobrać plików źródłowych z serwerów źródłowych, które implementują SrcSrv (`srcsrv.dll`) protokołu. Team Foundation Server i debugowania narzędzi dla systemu Windows są dwa serwery źródła, które implementują protokół. Aby uzyskać więcej informacji na temat konfigurowania SrcSrv, zobacz [SrcSrv](https://msdn.microsoft.com/library/windows/hardware/ff558791(v=vs.85).aspx) dokumentacji. Ponadto zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Ponieważ odczytywania .pdb, pliki można wykonania dowolnego kodu w plikach, upewnij się, czy zaufania serwerowi.  
  
- **Drukuj komunikaty diagnostyczne serwera źródłowego w oknie danych wyjściowych**  
    Włączono obsługę serwera źródłowego, to ustawienie włącza wyświetlanie diagnostycznych.  
  
- **Zezwalaj serwerowi źródłowemu na częściowo zaufane zestawy (tylko kod zarządzany)**  
    Po włączeniu obsługę serwera źródłowego, to ustawienie przesłania domyślne zachowanie na częściowo zaufane zestawy nie będą pobierane źródła.  

- **Włącz obsługę łączy źródła**  
    Określa, że debuger programu Visual Studio w celu pobrania plików źródłowych dla .pdb, pliki zawierające informacje o łączu źródła. Aby uzyskać więcej informacji na temat Link źródła, zobacz [Specyfikacja łącze źródła](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Ponieważ łącza źródła pobierze pliki przy użyciu protokołu http lub https, upewnij się, że ufasz plik PDB.  
  
**Podświetl cały wiersz dla punktów przerwania i bieżącej instrukcji (tylko C++)**  
Debuger wyróżnia punktu przerwania i bieżącej instrukcji, zawiera wyróżnione cały wiersz.  
  
**Wymagaj plików źródłowych jest zgodna z wersją oryginalną**  
Określa, że debuger, aby sprawdzić, czy plik źródłowy jest zgodna z wersją, używany do tworzenia pliku wykonywalnego, który debugowania kodu źródłowego. Jeśli wersja nie jest zgodny, zostanie wyświetlony monit można znaleźć zgodnego źródła. Jeśli nie znaleziono zgodnego źródła, nie można wyświetlić kodu źródłowego podczas debugowania. 
  
**Przekieruj cały tekst okna danych wyjściowych do okna bezpośredniego**  
Wysyła wszystkie debugera wiadomości, które zwykle będą widoczne w **dane wyjściowe** okna **Immediate** okna zamiast tego.  
  
**Pokaż nieprzetworzoną strukturę obiektów w oknach zmiennych**  
Wyłącza wszystkie dostosowania widoku struktury obiektu. Aby uzyskać więcej informacji na temat dostosowywania widoku, zobacz [Tworzenie niestandardowych widoków obiektów .managed](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Pomiń optymalizację JIT podczas ładowania modułu (tylko kod zarządzany)**  
Wyłącza optymalizację JIT kodu zarządzanego gdy ładowany jest moduł i JIT jest kompilowana, gdy debuger jest dołączony. Wyłączenie optymalizacji może ułatwić debugowania niektórych problemów, ale kosztem wydajności. Jeśli używane są tylko mój kod, pomijanie JIT optymalizacji może spowodować kodu innych użytkowników, które były wyświetlane jako użytkownika (kod "Moje"). Aby uzyskać więcej informacji, zobacz [optymalizację JIT i debugowanie](../debugger/jit-optimization-and-debugging.md).

**Włącz debugowanie JavaScript dla platformy ASP.NET (Chrome oraz programu IE)** umożliwia debugera skryptów dla aplikacji ASP.NET. Przy pierwszym użyciu w przeglądarce Chrome konieczne może być Zaloguj się do przeglądarki przy pierwszym użyciu włączyć rozszerzenia Chrome, które zostały zainstalowane. Wyłącz tę opcję, aby przywrócić działanie starszej wersji.    

**Załaduj elementy eksportu bibliotek dll**  
Ładuje tabele eksportu biblioteki dll. Informacje dotyczące symboli z tabel eksportu biblioteki dll może być przydatne, jeśli pracujesz z komunikatów systemu Windows, Windows procedury (WindowProcs), obiekty COM lub przekazywanie lub każdej biblioteki dll, dla którego nie ma symboli. Informacje o eksporcie odczytu biblioteki dll obejmuje pewne nadmiarowe obciążenie. Dlatego ta funkcja jest domyślnie wyłączona.  
  
Aby zobaczyć, jakie symboli są dostępne w tabeli eksportu biblioteki dll, użyj `dumpbin /exports`. Symbole są dostępne dla każdej biblioteki dll systemu 32-bitowego. Przeczytaj `dumpbin /exports` danych wyjściowych widać nazwy funkcji dokładne, w tym znaków innych niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji z tabel eksportu biblioteki dll może wyglądać obcięty w innym miejscu w debugerze. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Pokaż diagram równoległych stosów dołu do góry**  
Określa kierunek wyświetlone stosy w **stosów równoległych** okna.  
  
**Ignoruj wyjątki dostępu do pamięci procesora GPU, jeśli zapisane dane nie zmieniły wartości**  
Ignoruje wyścigu, które zostały wykryte podczas debugowania, jeśli dane nie zmieniły. Aby uzyskać więcej informacji, zobacz [debugowanie kodu GPU](../debugger/debugging-gpu-code.md).  
  
**Użyj zarządzanego trybu zgodności**  
Zastępuje domyślną debugowania aparatu przy użyciu starszych wersji, aby włączyć takie scenariusze:  
  
- Używasz języka .NET Framework innego niż C#, VB lub F # udostępniający własną ewaluatora wyrażenia (dotyczy to również C + +/ CLI).  
  
- Chcesz włączyć Edytuj i Kontynuuj dla projektów C++ podczas debugowania w trybie mieszanym.  
  
Pamiętaj, że wybór zgodności zarządzanego trybu wyłącza niektóre funkcje, które są wdrażane tylko w domyślnym aparat debugowania. 

**Użyj starszych ewaluatorów wyrażeń C# i VB**  
Debuger użyje ewaluatorów wyrażeń Visual Studio 2013 C# / VB. zamiast oceniających wyrażenia w Visual Studio 2015 Roslyn.    
  
**Ostrzegaj, gdy niestandardowe wizualizatory debugera względem potencjalnie niebezpiecznych procesów (tylko kod zarządzany)**  
Visual Studio ostrzega użytkownika, gdy używasz wizualizatora niestandardowego debugera uruchomionym kodu w procesie debugowanego obiektu, ponieważ może ona być uruchomiona niebezpieczny kod.  
  
**Włącz alokatora sterty debugowania systemu Windows (tylko kod natywny)**  
Umożliwia sterty debugowania systemu windows poprawić diagnostyki sterty. Włączenie tej opcji będzie mieć wpływ na wydajność debugowania.  
  
**Włącz narzędzia debugowania dla XAML interfejsu użytkownika**  
Drzewie wizualnym i windows Live Eksploruj właściwości pojawią się po rozpoczęciu debugowania typu obsługiwanych projektu (F5). Aby uzyskać więcej informacji, zobacz [właściwości sprawdzić XAML podczas debugowania](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Wyświetl podgląd wybranych elementów w dynamicznym drzewie wizualnym**  
    Element XAML, którego kontekst jest zaznaczona, jest również wybrany w **dynamicznym drzewie wizualnym** okna.  
  
- **Pokaż narzędzia środowiska uruchomieniowego w aplikacji**  
    Pokazuje **dynamicznym drzewie wizualnym** polecenia na pasku narzędzi w oknie głównym aplikacji XAML, która jest debugowana. Ta opcja została wprowadzona w programie Visual Studio 2015 Update 2. 

- **Włącz XAML Edytuj i Kontynuuj** pozwala na korzystanie z opcji Edytuj i Kontynuuj funkcji dla kodu XAML. 
  
**Włącz narzędzia diagnostyczne podczas debugowania**  
**Narzędzia diagnostyczne** okno podczas debugowania.
  
**Pokaż element PerfTip czas, który upłynął podczas debugowania**  
W oknie Kod wyświetla czas wywołania metody danego podczas debugowania.  
  
**Włącz funkcję Edytuj i Kontynuuj**  
Można użyć edycji i kontynuować funkcji podczas debugowania.  
  
- **Włącz natywną funkcję Edytuj i Kontynuuj**  
    Można użyć edycji i kontynuować funkcji podczas debugowania kodu natywnego języka C++. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Zastosuj zmiany przy kontynuowaniu (tylko kod natywny)**  
    Visual Studio kompiluje i automatycznie stosuje zmiany kodu oczekujących, wprowadzonych podczas kontynuowanie procesu w stanie przerwania. Nie wybrano można zastosować zmian przy użyciu elementu "Zastosowanie zmian kodu" w menu debugowania.  
  
- **Ostrzegaj o nieodświeżonym kodzie (tylko kod natywny)**  
    Pobierz ostrzeżenia o kodzie nieodświeżonym.    

**Pokaż wykonywania kliknięcie przycisku w edytorze podczas debugowania** gdy ta opcja jest zaznaczona, [Uruchom kliknięcie](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) przycisk będzie wyświetlany podczas debugowania.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Opcje obsługiwane we wcześniejszych wersjach programu Visual Studio

Jeśli używasz starszej wersji programu Visual Studio, mogą występować pewne dodatkowe opcje.

**Włącz Asystenta wyjątków**  
Włączone z Asystenta wyjątków dla kodu zarządzanego. W programie Visual Studio 2017 r. pomocnika wyjątków zastąpione Asystenta wyjątków.

**Odwiń stos wywołań w przypadku nieobsługiwanych wyjątków**  
Powoduje, że **stos wywołań** okno, aby wycofać stosu wywołań do punktu przed Wystąpił nieobsługiwany wyjątek. 

**Ostrzegaj w przypadku żadnych symboli przy uruchomieniu (tylko kod natywny)**  
Wyświetla okno dialogowe ostrzeżenia podczas debugowania programu, dla którego debugera nie ma symbolu informacji. 

**Ostrzegaj, jeśli debugowanie skryptów jest wyłączone przy uruchomieniu**  
Wyświetla okno dialogowe ostrzeżenia, gdy debuger jest uruchamiana z debugowanie skryptu wyłączone.

**Użyj natywnego trybu zgodności**  
Gdy ta opcja jest zaznaczona, debuger używa debuger natywny programu Visual Studio 2010 zamiast nowego debuger natywny.  
  
Tej opcji należy używać podczas debugowania kodu .NET C++, ponieważ nowy aparat debugowania nie obsługuje wyrażeń .NET C++ oszacowania. Jednak włączenie natywnego trybu zgodności wyłączenie wiele funkcji, które są zależne od bieżącej implementacji debugera do działania. Na przykład starszego aparatu brakuje wiele wizualizatorów dla wbudowanych typów, takich jak `std::string` w projektach Visual Studio 2015.   Dla zapewnienia optymalnego działania debugowania w tych przypadkach Użyj projektów programu Visual Studio 2013.
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)
