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
ms.openlocfilehash: 5b7af8c68764b3a9ed85bf6a52a3a6c4a0568203
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572053"
---
# <a name="general-debugging-options-dialog-box"></a>Ogólne, debugowanie, okno dialogowe Opcje
**Narzędzia > Opcje > debugowanie > Ogólne** strony pozwala ustawić opcje opisane w tym artykule.

Jeśli trzeba przywrócić ustawienia domyślne, możesz to zrobić przy użyciu tego **narzędzia** > **Import i eksport ustawień** > **zresetować wszystkie ustawienia**. Jeśli chcesz zresetować podzbiór ustawień, Zapisz ustawienia w **Kreator importowania i eksportowania ustawień** przed wprowadzeniem zmian, które mają zostać przetestowane, następnie zaimportować zapisane ustawienia później.
  
**Pytaj przed usunięciem wszystkich punktów przerwania** wymaga potwierdzenia przed ukończeniem **Usuń wszystkie punkty przerwania** polecenia.  
  
**Przerwij wszystkie procesy w przypadku przerwania jednego procesu** jednocześnie dzieli wszystkie procesy, do których jest dołączony debuger, gdy występuje podział.  
  
**Przerwij, gdy wyjątki przekraczają AppDomain lub granic zarządzane lub natywne** w debugowania zarządzanego lub mieszanym, środowisko uruchomieniowe języka wspólnego można przechwytywać wyjątki, które granice domeny aplikacji lub granice zarządzane lub natywne podczas następujące warunki są spełnione:  
  
1\) po kodu natywnego wywołuje zarządzanego kodu za pomocą międzyoperacyjności z modelem COM i kod zarządzany zgłasza wyjątek. Zobacz [wprowadzenie do COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) po kodu zarządzanego działającego w domenie aplikacji 1 wywołania kodu zarządzanego w domenie aplikacji 2 i kodu w domenie aplikacji 2 zgłasza wyjątek. Zobacz [programowania z domenami aplikacji](/dotnet/articles/framework/app-domains/index).  

3\) gdy kod wywołuje funkcję przy użyciu odbicia, a funkcja zwraca wyjątek. Zobacz [odbicia](/dotnet/framework/reflection-and-codedom/reflection).  
  
W warunku, 2 i 3, wyjątek jest czasami zgłoszony przez kod zarządzany w `mscorlib` zamiast środowisko uruchomieniowe języka wspólnego. Ta opcja nie dotyczy dzielenia na wyjątki przechwycony przez `mscorlib`.  
  
**Włącz debugowanie poziomie adresu** umożliwia zaawansowane funkcje do debugowania na poziomie adresu ( **dezasemblacji** okna, **rejestruje** okna, a punkty przerwania adresu).  
  
- **Pokaż dezasemblację, jeśli źródło jest niedostępne** automatycznie wyświetlany **dezasemblacji** okno podczas debugowania kodu, dla których źródła jest niedostępna.  
  
**Włącz punktu przerwania filtry** pozwala ustawić filtry na punktów przerwania, aby wpływają one na określone procesy, wątki lub komputery.  
 
**Użyj nowego pomocnika wyjątków** umożliwia pomocnika wyjątków (Visual Studio 2017), który zastępuje Asystenta wyjątków.
  
> [!NOTE]
> Dla kodu zarządzanego, ta opcja była wcześniej określana **Włącz Asystenta wyjątków** . 
  
**Włącz opcję tylko mój kod** debuger wyświetla i kroki do kodu użytkownika ("Mój kod"), ignorowanie kod systemu i innego kodu, która została zoptymalizowana lub, która nie ma symboli debugowania.

- **Ostrzegaj w przypadku braku kodu użytkownika przy uruchomieniu (tylko kod zarządzany)** gdy debugowanie się rozpocznie z tylko mój kod włączone, ta opcja wyświetli ostrzeżenie, jeśli nie jest wykonywany kod użytkownika ("Mój kod"). 

**Włączyć program .NET Framework krokowe wykonywanie źródła** umożliwia debugera wkraczać do źródła .NET Framework. Włączenie tej opcji powoduje automatyczne wyłączenie tylko mój kod .NET Framework symbole zostaną pobrane do lokalizacji pamięci podręcznej. Możesz zmienić lokalizację pamięci podręcznej w **opcje** okno dialogowe **debugowanie** kategorii, **symbole** strony.  
  
**Przekrocz nad właściwościami i operatorami (tylko kod zarządzany)** zapobiega Wkraczanie do właściwości i operatory w kodzie zarządzanym przez debuger.  
  
**Włącz obliczanie właściwości i inne niejawne wywołania funkcji** włącza funkcję automatycznej oceny właściwości i niejawna funkcja wywołuje w oknach zmiennych i **QuickWatch** okno dialogowe.  
  
- **Wywołania funkcji konwersji ciągów na obiektach w oknach zmiennych (C# i JavaScript tylko)** wykonuje wywołanie ciąg niejawna konwersja podczas obliczania obiektów w oknach zmiennych. Wynik jest wyświetlany w postaci ciągu zamiast nazwy typu. Ma zastosowanie tylko podczas debugowania w kodzie języka C#. To ustawienie może być zastąpiona przez atrybutu DebuggerDisplay (zobacz [za pomocą atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Włącz obsługę serwera źródłowego** informuje debuger programu Visual Studio można pobrać plików źródłowych z serwerów źródłowych, które implementują SrcSrv (`srcsrv.dll`) protokołu. Team Foundation Server i debugowania narzędzi dla systemu Windows są dwa serwery źródła, które implementują protokół. Aby uzyskać więcej informacji na temat konfigurowania SrcSrv, zobacz [SrcSrv](https://msdn.microsoft.com/library/windows/hardware/ff558791(v=vs.85).aspx) dokumentacji. Ponadto zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Ponieważ odczytywania .pdb, pliki można wykonania dowolnego kodu w plikach, upewnij się, czy zaufania serwerowi.  
  
- **Drukuj komunikaty diagnostyczne serwera źródłowego w oknie danych wyjściowych** po włączeniu obsługę serwera źródłowego, to ustawienie włącza wyświetlanie diagnostycznych.  
  
- **Zezwalaj serwerowi źródłowemu na częściowo zaufane zestawy (tylko kod zarządzany)** po włączeniu obsługę serwera źródłowego, to ustawienie przesłania domyślne zachowanie na częściowo zaufane zestawy nie będą pobierane źródła.  

**Włącz obsługę łącze źródło** informuje debuger programu Visual Studio w celu pobrania plików źródłowych dla .pdb, pliki zawierające informacje o łączu źródła. Aby uzyskać więcej informacji na temat Link źródła, zobacz [Specyfikacja łącze źródła](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Podświetl cały wiersz dla punktów przerwania i bieżącej instrukcji (tylko C++)** gdy debuger wyróżnia punktu przerwania i bieżącej instrukcji, zawiera opis cały wiersz.  
  
**Wymagaj źródła dokładnej zgodności plików oryginalnej wersji** informuje debugera, aby sprawdzić, czy plik źródłowy zgodna z wersją używany do tworzenia pliku wykonywalnego debugowania kodu źródłowego. Jeśli wersja nie jest zgodny, zostanie wyświetlony monit można znaleźć zgodnego źródła. Jeśli nie znaleziono zgodnego źródła, nie można wyświetlić kodu źródłowego podczas debugowania. 
  
**Przekieruj cały tekst okna danych wyjściowych do okna bezpośredniego** wysyła debugera wszystkie komunikaty pojawiały się zwykle w **dane wyjściowe** okna **Immediate** okna zamiast tego.  
  
**Pokaż nieprzetworzoną strukturę obiektów w oknach zmiennych** wyłącza wszystkie dostosowania widoku struktury obiektu. Aby uzyskać więcej informacji na temat dostosowywania widoku, zobacz [Tworzenie niestandardowych widoków obiektów .managed](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Pomiń optymalizację JIT podczas ładowania modułu (tylko kod zarządzany)** wyłącza optymalizację JIT kodu zarządzanego gdy ładowany jest moduł i JIT jest kompilowana, gdy debuger jest dołączony. Wyłączenie optymalizacji może ułatwić debugowania niektórych problemów, ale kosztem wydajności. Jeśli używane są tylko mój kod, pomijanie JIT optymalizacji może spowodować kodu innych użytkowników, które były wyświetlane jako użytkownika (kod "Moje"). Aby uzyskać więcej informacji, zobacz [optymalizację JIT i debugowanie](../debugger/jit-optimization-and-debugging.md).

**Włącz debugowanie JavaScript dla platformy ASP.NET (Chrome oraz programu IE)** umożliwia debugera skryptów dla aplikacji ASP.NET. Przy pierwszym użyciu w przeglądarce Chrome konieczne może być Zaloguj się do przeglądarki przy pierwszym użyciu włączyć rozszerzenia Chrome, które zostały zainstalowane. Wyłącz tę opcję, aby przywrócić działanie starszej wersji.    

**Załaduj elementy eksportu bibliotek dll** ładuje tabele eksportu biblioteki dll. Informacje dotyczące symboli z tabel eksportu biblioteki dll może być przydatne, jeśli pracujesz z komunikatów systemu Windows, Windows procedury (WindowProcs), obiekty COM lub przekazywanie lub każdej biblioteki dll, dla którego nie ma symboli. Informacje o eksporcie odczytu biblioteki dll obejmuje pewne nadmiarowe obciążenie. Dlatego ta funkcja jest domyślnie wyłączona.  
  
Aby zobaczyć, jakie symboli są dostępne w tabeli eksportu biblioteki dll, użyj `dumpbin /exports`. Symbole są dostępne dla każdej biblioteki dll systemu 32-bitowego. Przeczytaj `dumpbin /exports` danych wyjściowych widać nazwy funkcji dokładne, w tym znaków innych niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji z tabel eksportu biblioteki dll może wyglądać obcięty w innym miejscu w debugerze. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Pokaż równoległych stosów od dołu do góry diagram** steruje kierunkiem wyświetlone stosy w **stosów równoległych** okna.
  
**Ignoruj wyjątki dostępu do pamięci procesora GPU, jeśli zapisane dane nie zmieniły wartości** ignoruje wyścigu, które zostały wykryte podczas debugowania, jeśli dane nie zmieniły. Aby uzyskać więcej informacji, zobacz [debugowanie kodu GPU](../debugger/debugging-gpu-code.md).  
  
**Użyj zarządzanego trybu zgodności** zastępuje domyślną debugowania aparatu przy użyciu starszych wersji, aby włączyć takie scenariusze:  
  
- Używasz języka .NET Framework innego niż C#, VB lub F # udostępniający własną ewaluatora wyrażenia (dotyczy to również C + +/ CLI).  
  
- Chcesz włączyć Edytuj i Kontynuuj dla projektów C++ podczas debugowania w trybie mieszanym.  
  
> [!NOTE]
> Wybieranie zarządzanego zgodności tryb wyłącza niektóre funkcje, które są wdrażane tylko w domyślnym aparat debugowania. 

**Użyj starszych ewaluatorów wyrażeń C# i VB** debuger użyje ewaluatorów wyrażeń Visual Studio 2013 C# / VB. zamiast oceniających wyrażenia w Visual Studio 2015 Roslyn.    
  
**Ostrzegaj, gdy niestandardowe wizualizatory debugera względem potencjalnie niebezpiecznych procesów (tylko kod zarządzany)** Visual Studio ostrzega użytkownika, gdy używasz wizualizatora niestandardowego debugera uruchomionym kodu w procesie debugowanego obiektu, ponieważ mogą być wykonywane unsafe Kod.  
  
**Włącz alokatora sterty debugowania systemu Windows (tylko kod natywny)** umożliwia sterty debugowania systemu windows poprawić diagnostyki sterty. Włączenie tej opcji będzie mieć wpływ na wydajność debugowania.  
  
**Włącz narzędzia debugowania interfejsu użytkownika dla XAML** dynamicznym drzewie wizualnym i windows Live Eksploruj właściwości pojawią się po rozpoczęciu debugowania (F5) typu obsługiwanych projektu. Aby uzyskać więcej informacji, zobacz [właściwości sprawdzić XAML podczas debugowania](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Wyświetl podgląd wybranych elementów w dynamicznym drzewie wizualnym** również wybrano element XAML, którego kontekst jest zaznaczona w **dynamicznym drzewie wizualnym** okna.  
  
- **Pokaż narzędzia środowiska uruchomieniowego w aplikacji** pokazuje **dynamicznym drzewie wizualnym** polecenia na pasku narzędzi w oknie głównym aplikacji XAML, która jest debugowana. Ta opcja została wprowadzona w programie Visual Studio 2015 Update 2. 

- **Włącz XAML Edytuj i Kontynuuj** pozwala na korzystanie z opcji Edytuj i Kontynuuj funkcji dla kodu XAML. 
  
**Włącz narzędzia diagnostyczne podczas debugowania** **narzędzia diagnostyczne** okno podczas debugowania.
  
**Pokaż element PerfTip czas, który upłynął podczas debugowania** okna kod przedstawia czas, który upłynął wywołania metody danego podczas debugowania.  
  
**Włącz Edytuj i Kontynuuj** można użyć edycji i kontynuować funkcji podczas debugowania.  
  
- **Włącz natywnego Edytuj i Kontynuuj** można użyć edycji i kontynuować funkcji podczas debugowania kodu natywnego języka C++. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Zastosuj zmiany przy kontynuowaniu (tylko kod natywny)** Visual Studio kompiluje i automatycznie stosuje zmiany oczekujące kodu zostały wykonane po kontynuowanie procesu w stanie przerwania. Nie wybrano można zastosować zmian przy użyciu elementu "Zastosowanie zmian kodu" w menu debugowania.  
  
- **Ostrzegaj o nieodświeżonym kodzie (tylko kod natywny)** uzyskać ostrzeżenia o kodzie nieodświeżonym.    

**Pokaż wykonywania kliknięcie przycisku w edytorze podczas debugowania** gdy ta opcja jest zaznaczona, [Uruchom kliknięcie](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) przycisk będzie wyświetlany podczas debugowania.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Opcje obsługiwane we wcześniejszych wersjach programu Visual Studio

Jeśli używasz starszej wersji programu Visual Studio, mogą występować pewne dodatkowe opcje.

**Włącz Asystenta wyjątków** dla kodu zarządzanego włączone Asystenta wyjątków. W programie Visual Studio 2017 r. pomocnika wyjątków zastąpione Asystenta wyjątków.

**Odwiń stos wywołań w przypadku nieobsługiwanych wyjątków** powoduje, że **stos wywołań** okno, aby wycofać stosu wywołań do punktu przed Wystąpił nieobsługiwany wyjątek. 

**Ostrzegaj w przypadku żadnych symboli przy uruchomieniu (tylko kod natywny)** Wyświetla okno dialogowe ostrzeżenia podczas debugowania programu, dla którego debugera nie ma symbolu informacji. 

**Ostrzegaj, jeśli debugowanie skryptów jest wyłączone przy uruchomieniu** Wyświetla okno dialogowe ostrzeżenia, gdy debuger jest uruchamiana z debugowanie skryptu wyłączone.

**Użyj natywnego trybu zgodności** gdy ta opcja jest zaznaczona, debuger używa debuger natywny programu Visual Studio 2010 zamiast nowego debuger natywny.  
  
Tej opcji należy używać podczas debugowania kodu .NET C++, ponieważ nowy aparat debugowania nie obsługuje wyrażeń .NET C++ oszacowania. Jednak włączenie natywnego trybu zgodności wyłączenie wiele funkcji, które są zależne od bieżącej implementacji debugera do działania. Na przykład starszego aparatu brakuje wiele wizualizatorów dla wbudowanych typów, takich jak `std::string` w projektach Visual Studio 2015.   Użyj projektów programu Visual Studio 2013 celu zapewnienia optymalnego działania debugowania w tych przypadkach.
  
## <a name="see-also"></a>Zobacz także  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)
