---
title: Ogólne, debugowanie, okno dialogowe Opcje | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e46301c84b1a9b27eed8cb6667b312ff73af2960
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280640"
---
# <a name="general-debugging-options-dialog-box"></a>Ogólne, debugowanie, okno dialogowe Opcje
**Narzędzia > Opcje > debugowanie > Ogólne** stronie pozwala ustawić opcje opisane w tym artykule.

Jeśli chcesz przywrócić ustawienia domyślne, możesz to zrobić, przy użyciu **narzędzia** > **Import i eksport ustawień** > **Resetuj wszystkie ustawienia**. Jeśli chcesz zresetować podzbioru ustawień, Zapisz ustawienia w **Kreatora importowania i eksportowania ustawień** przed wprowadzeniem zmian, które mają zostać przetestowane, następnie zaimportuj zapisane ustawienia później.
  
**Pytaj przed usunięciem wszystkich punktów przerwania** wymaga potwierdzenia przed ukończeniem **Usuń wszystkie punkty przerwania** polecenia.  
  
**Przerwij wszystkie procesy, gdy jeden proces ulegnie przerwaniu** jednocześnie przerywa wszystkie procesy, do których jest dołączony debuger, gdy występuje przerwa.  
  
**Przerwij, gdy wyjątki przekroczą granice AppDomain lub granice zarządzane/macierzyste** podczas debugowania zarządzanego lub mieszanym, środowisko uruchomieniowe języka wspólnego może przechwytywać wyjątki, które przecinają granice domen aplikacji lub granice zarządzane/macierzyste podczas następujące warunki są spełnione:  
  
1\) kiedy kod macierzysty wywołuje kod zarządzany za pomocą COM Interop, i zgłasza wyjątek, kod zarządzany. Zobacz [wprowadzenie do COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) gdy kodu zarządzanego uruchomionego w domenie aplikacji 1 wywołuje kod zarządzany w domenie aplikacji, 2, a kodw aplikacji Domena 2 zgłasza wyjątek. Zobacz [programowanie z domenami aplikacji](/dotnet/articles/framework/app-domains/index).  

3\) gdy kod wywołuje funkcję przy użyciu odbicia, a funkcja zgłasza wyjątek. Zobacz [odbicia](/dotnet/framework/reflection-and-codedom/reflection).  
  
W warunku, 2 i 3, wyjątek jest czasami zgłoszony przez kod zarządzany w `mscorlib` zamiast środowiska uruchomieniowego języka wspólnego. Ta opcja nie wpływa na przerwanie w wyjątkach przechwyconych przez `mscorlib`.  
  
**Włącz debugowanie na poziomie adresów** włącza zaawansowane funkcje debugowania na poziomie adresów ( **dezasemblacji** oknie **rejestruje** okna, a punkty przerwania adresów).  
  
- **Pokaż dezasemblację, jeśli źródło jest niedostępne** jest automatycznie wyświetlana **dezasemblacji** okna podczas próby debugowania kodu, dla którego źródło jest niedostępne.  
  
**Włącz filtry punktów przerwania** umożliwia ustawiania filtrów punktów przerwania, tak że wpływają one tylko określone procesy, wątki lub komputery.  
 
**Użyj nowego pomocnika wyjątków** umożliwia pomocnika wyjątków (Visual Studio 2017), która zastępuje Asystenta wyjątków.
  
> [!NOTE]
> Dla kodu zarządzanego, ta opcja był wcześniej nazywany programem **Włącz Asystenta wyjątków** . 
  
**Włącz opcję tylko mój kod** debuger wyświetla i kroki kod użytkownika ("Mój kod"), ignorując kod systemowy i inny kod, który zoptymalizowano lub w którym nie ma symboli debugowania.

- **Ostrzegaj w przypadku braku kodu użytkownika przy uruchomieniu (tylko kod zarządzany)** gdy debugowanie się rozpocznie dzięki włączeniu tylko mój kod, opcja ta ostrzega, jeśli nie jest wykonywany kod użytkownika ("Mój kod"). 

**Włączyć program .NET Framework krokowe wykonywanie źródła** pozwala debugerowi na wkroczenie do źródła .NET Framework. Włączenie tej opcji spowoduje automatyczne wyłączenie tylko mój kod .NET Framework symbole będą pobierane do lokalizacji pamięci podręcznej. Możesz zmienić lokalizację pamięci podręcznej w **opcje** okno dialogowe **debugowanie** kategorii **symbole** strony.  
  
**Przekrocz nad właściwościami i operatorami (tylko kod zarządzany)** sprawia, że debuger wchodzi we właściwości i operatory w kodzie zarządzanym.  
  
**Włącz obliczanie właściwości i inne niejawne wywołania funkcji** włącza funkcję automatycznej oceny właściwości i niejawne funkcja wywołuje w oknach zmiennych i **QuickWatch** okno dialogowe.  
  
- **Wywołaj funkcję konwersji ciągu na obiektach w oknach zmiennych (C# i JavaScript tylko)** wykonuje wywołanie niejawnej konwersji ciągu podczas szacowania wartości obiektów w oknach zmiennych. Wynik jest wyświetlany jako ciąg, nie nazwę typu. Dotyczy to tylko podczas debugowania kodu C#. To ustawienie może być zastąpiona przez atrybut DebuggerDisplay (zobacz [korzystanie z atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Włącz obsługę serwera źródłowego** nakazuje debugerowi programu Visual Studio pobranie plików źródłowych z serwerów źródłowych, które implementują SrcSrv (`srcsrv.dll`) protokołu. Team Foundation Server i Debugging Tools for Windows to dwa serwery źródłowe implementujące ten protokół. Aby uzyskać więcej informacji o konfiguracji SrcSrv, zobacz [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) dokumentacji. Ponadto zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Ponieważ czytania *.pdb* plików może wykonywać dowolny kod w plikach, upewnij się, że masz zaufanie do serwera.  
  
- **Drukowanie komunikatów diagnostycznych serwera źródłowego w oknie danych wyjściowych** po włączeniu obsługi serwera źródłowego, to ustawienie powoduje włączenie ekranu diagnostycznego.  
  
- **Zezwalaj serwerowi źródłowemu na częściowo zaufane zestawy (tylko kod zarządzany)** po włączeniu obsługi serwera źródłowego, ustawienie to zastępuje domyślne zachowanie niepobierania źródeł dla zestawów częściowej relacji zaufania.  

**Włącz obsługę Source Link** informuje debuger programu Visual Studio, aby pobrać pliki źródłowe pliki .pdb, które zawierają informacje o Linku źródłowego. Aby uzyskać więcej informacji dotyczących Linku źródłowego, zobacz [określenie Linku źródłowego](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Zaznaczanie całego wiersza dla punktów przerwania i bieżącej instrukcji (tylko C++)** gdy debuger wyróżnia punkt przerwania lub bieżącą instrukcję, wyróżnia jej cały wiersz.  
  
**Wymagaj plików źródłowych Aby dokładnie dopasować oryginalną wersję** nakazuje debugerowi sprawdzenie, czy plik źródłowy jest zgodny z wersją kodu źródłowego użytego do utworzenia pliku wykonywalnego debugowania. Jeśli wersja nie jest zgodny, będzie się monit o znalezienie pasującego źródła. Jeśli zgodne źródło nie zostanie znaleziony, nie można wyświetlić kodu źródłowego podczas debugowania. 
  
**Przekieruj wszystkie dane wyjściowe okna tekstowego do okna bezpośredniego** wysyła wszystkie komunikaty debugera, które normalnie pojawiają się w **dane wyjściowe** okna **bezpośrednie** okna zamiast tego.  
  
**Pokaż nieprzetworzoną strukturę obiektów w oknach zmiennych** wyłącza wszystkie dostosowania widoku struktury obiektu. Aby uzyskać więcej informacji na temat dostosowania widoków, zobacz [Tworzenie niestandardowych widoków obiektów .managed](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Pomijanie optymalizacji JIT przy ładowaniu modułu (tylko kod zarządzany)** wyłącza optymalizację JIT kodu zarządzanego, gdy moduł jest załadowany a JIT kompilowana w czasie, gdy jest dołączony debuger. Wyłączenie optymalizacji może ułatwić debugowanie pewnych problemów, ale kosztem wydajności. Jeśli używasz tylko mój kod, pomijanie JIT optymalizacji może spowodować niebędący kodem użytkownika do wyświetlania jako kod użytkownika ("Mój kod"). Aby uzyskać więcej informacji, zobacz [optymalizację JIT i debugowanie](../debugger/jit-optimization-and-debugging.md).

**Włącz debugowanie kodu JavaScript dla platformy ASP.NET (przeglądarki Chrome i programu Internet Explorer)** umożliwia debugera skryptów w przypadku aplikacji ASP.NET. Przy pierwszym użyciu w przeglądarce Chrome może być konieczne Zaloguj się do przeglądarki przy pierwszym użyciu, aby włączyć rozszerzenia dla programu Chrome, które zostały zainstalowane. Wyłącz tę opcję, aby przywrócić starsze zachowanie.    

**Ładuj eksporty dll** ładuje tabele eksportu bibliotek dll. Informacje o symbolach tabel eksportu biblioteki dll może być przydatne, jeśli pracujesz z Windows wiadomości, procedur Windows (WindowProcs), obiektami COM, lub organizowanie lub dowolną biblioteką dll, dla której nie masz symboli. Odczytywanie pliku dll informacji o eksportowaniu pewne nadmiarowe obciążenie. Dlatego ta funkcja jest domyślnie wyłączona.  
  
Aby zobaczyć, jakie symbole są dostępne w tabeli eksportu biblioteki dll, użyj `dumpbin /exports`. Symbole są dostępne dla każdej biblioteki dll systemu 32-bitowego. Czytając `dumpbin /exports` danych wyjściowych, możesz zobaczyć dokładną nazwę funkcji, w tym znaki inne niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji tabel eksportu biblioteki dll, może pojawić się obcięte gdzie indziej w debugerze. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [dumpbin/EXPORTS](/cpp/build/reference/dash-exports).  
  
**Pokaż równoległych stosów od dołu do góry diagram** kontroluje kierunek, w którym stosy są wyświetlane w **stosów równoległych** okna.
  
**Ignoruj wyjątki dostępu do pamięci procesora GPU, jeśli zapisane dane nie zmieniły wartości** ignoruje Sytuacje wyścigu, które zostały wykryte podczas debugowania, jeśli dane nie zmieniły. Aby uzyskać więcej informacji, zobacz [debugowania kodu GPU](../debugger/debugging-gpu-code.md).  
  
**Użyj zarządzanego trybu zgodności** zastępuje domyślny aparat starszą wersją, aby włączyć te scenariusze debugowania:  
  
- W przypadku korzystania z języka .NET Framework innego niż C#, VB lub F # zapewniający własny Ewaluator wyrażeń (to obejmuje C + +/ CLI).  
  
- Chcesz włączyć Edytuj i Kontynuuj dla projektów C++ podczas debugowania w trybie mieszanym.  
  
> [!NOTE]
> Trybu, wybierając zgodności zarządzanej wyłącza niektóre funkcje, które są zaimplementowane tylko w domyślnym aparacie debugowania. 

**Użyj starszych ewaluatory wyrażeń języka C# i VB** debuger użyje ewaluatory wyrażeń Visual Studio 2013 w języku C# /VB zamiast ewaluatory wyrażeń opartych na programie Visual Studio 2015 Roslyn.    
  
**Ostrzegaj, gdy niestandardowe wizualizatory debugera względem potencjalnie niebezpiecznych procesów (tylko kod zarządzany)** programu Visual Studio ostrzeże Cię, gdy używasz wizualizatora niestandardowego debugera działającego kodu w procesie debugowanego obiektu, ponieważ może być uruchomiony unsafe Kod.  
  
**Włącz alokatora sterty debugowania Windows (tylko natywne)** pozwala na stercie systemu windows, lepszą diagnostykę sterty. Włączenie tej opcji będzie mieć wpływ na wydajność debugowania.  
  
**Włącz narzędzia debugowania interfejsu użytkownika dla XAML** dynamiczne drzewo wizualne i windows Live Eksplorowanie właściwość pojawi się po rozpoczęciu debugowania (F5) typu obsługiwanych projektu. Aby uzyskać więcej informacji, zobacz [właściwości sprawdzić XAML podczas debugowania](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Wyświetl podgląd wybranych elementów w dynamicznym drzewie wizualnym** XAML elementu, którego kontekst jest zaznaczona, jest również wybrany w **dynamiczne drzewo wizualne** okna.  
  
- **Pokaż narzędzia środowiska uruchomieniowego w aplikacji** pokazuje **dynamiczne drzewo wizualne** polecenia na pasku narzędzi w oknie głównym aplikacji XAML, która jest debugowana. Ta opcja została wprowadzona w Visual Studio 2015 Update 2. 

- **Włącz Edytuj XAML i Kontynuuj** pozwala na używanie funkcji Edytuj i Kontynuuj funkcji dla kodu XAML. 
  
**Włącz narzędzia diagnostyczne podczas debugowania** **narzędzia diagnostyczne** zostanie wyświetlone okno podczas debugowania.
  
**Podczas debugowania Pokaż element perftip dla czasu upłynęło** okna kodu wyświetla czas wywołania danej metody podczas debugowania.  
  
**Włącz Edytuj i Kontynuuj** można użyć edycji i kontynuowania funkcji podczas debugowania.  
  
- **Włączanie natywnego Edytuj i Kontynuuj** można użyć edycji i kontynuowania funkcji podczas debugowania kodu natywnego języka C++. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Zastosuj zmiany przy kontynuowaniu (tylko natywne)** programu Visual Studio kompiluje i automatycznie stosuje żadnych zmian w kodzie oczekujących wprowadzone podczas kontynuując proces w stanie przerwania. Jeśli nie jest zaznaczone, można zastosować zmian przy użyciu elementu "Zastosowanie zmian kodu" w menu Debugowanie.  
  
- **Ostrzeżenie o nieodświeżonym kodzie (tylko natywne)** Pobierz ostrzeżenia o nieodświeżonym kodzie.    

**Pokaż Uruchom do kliknięcia przycisku w edytorze podczas debugowania** po wybraniu tej opcji [uruchamianie do kliknięcia](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) przycisk będzie wyświetlany podczas debugowania.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Opcje obsługiwane w starszych wersjach programu Visual Studio

Jeśli używasz starszej wersji programu Visual Studio może istnieć pewne dodatkowe opcje.

**Włącz Asystenta wyjątków** dla kodu zarządzanego, włączone Asystenta wyjątków. W programie Visual Studio 2017 pomocnika wyjątków zastąpione Asystenta wyjątków.

**Operacja unwind na stosie wywołań dotycząca nieobsłużonych wyjątków** powoduje, że **stos wywołań** okna, aby wycofać stos wywołań do punktu przed wystąpieniem nieobsługiwanego wyjątku. 

**Ostrzegaj, jeśli brak symboli podczas uruchamiania (tylko natywne)** Wyświetla okno dialogowe ostrzeżenia podczas próby debugowania programu, dla którego debuger nie ma żadnych informacji o symbolach. 

**Ostrzegaj, jeśli debugowanie skryptów jest wyłączone w momencie uruchomienia** Wyświetla okno dialogowe ostrzeżenia, gdy debuger jest uruchamiany z wyłączonym debugowaniem skryptów.

**Użyj trybu zgodności natywnych** po wybraniu tej opcji debuger używa macierzystym debugerze programu Visual Studio 2010, zamiast nowej macierzystym debugerze.  
  
Należy używać tej opcji podczas debugowania kodu w języku C++ platformy .NET, ponieważ nowy aparat debugowania nie obsługuje oceny wyrażeń języka C++ platformy .NET. Włączanie natywnego trybu zgodności wyłącza jednak wiele funkcji, które są zależne od bieżącej implementacji debugera do działania. Na przykład starszego aparatu nie posiada wiele wizualizatorów, dla wbudowanych typów, takich jak `std::string` w projektach programu Visual Studio 2015.   Projekty programu Visual Studio 2013 na użytek optymalne środowisko debugowania w tych przypadkach.
  
## <a name="see-also"></a>Zobacz także  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
