---
title: "Omówienie diagnostyki grafiki programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/09/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8fb52530cf5a068081ce3af3325675d2167c57a9
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="overview-of-visual-studio-graphics-diagnostics"></a>Omówienie diagnostyki grafiki w programie Visual Studio
Visual Studio *diagnostyki grafiki* jest zestaw narzędzi dla rejestrowanie i analizowanie danych renderowania i problemom z wydajnością w aplikacjach Direct3D. Diagnostyka grafiki można w aplikacji, które są uruchomione lokalnie na komputerze z systemem Windows lub na urządzeniu lub komputerze zdalnym.  
  
## <a name="using-graphics-diagnostics-to-debug-rendering-problems"></a>Używanie Graphics Diagnostics do debugowania problemów z renderowaniem  
 Debugowanie problemów z renderowaniem w aplikacji rozbudowanej graficznie nie jest tak proste, jak uruchomienie debugera i krokowe wykonywanie kodu. W każdej klatce są produkowane setki tysięcy unikatowych pikseli, każdy na podstawie złożonego zestawu stanu, danych, parametrów i kodu — możliwe, że tylko kilka z powyższych pikseli pokaże problem, który próbujesz zdiagnozować. Aby jeszcze bardziej skomplikować sprawy, kod, który generuje każdy piksel, jest wykonywany na wyspecjalizowanym sprzęcie, który przetwarza setki pikseli równolegle. Tradycyjne narzędzia i techniki debugowania, z których trudno się korzysta nawet w kodzie mało skomplikowanym pod względem wątków, są nieskuteczne w obliczu tak dużej ilości danych.  
  
 Narzędzia diagnostyki grafiki w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są zaprojektowane, aby zlokalizować problemy z renderowaniem, zaczynając od visual artefaktów, które wskazują problem i następnie Śledzenie wstecz do źródła problemu koncentrujące się tylko na odpowiednich programu do cieniowania kodu, w potoku Rysuj etapy, wywołania, zasobów i stan urządzenia — w kodzie źródłowym aplikacji.  
  
## <a name="directx-version-compatibility"></a>Zgodność wersji programu DirectX  
 Diagnostyki grafiki obsługuje aplikacje, które używają Direct3D 10 lub nowszy i zapewnia ograniczoną obsługę aplikacji korzystających z programem Direct2D. Nie obsługuje aplikacji, które używają starszych wersji Direct3D, DirectDraw lub innych graficznych interfejsów API.  
  
### <a name="windows-10-and-direct3d-12"></a>System Windows 10 i Direct3D 12  
 Windows 10 wprowadzone *Direct3D 12*, który znacznie różni się od Direct3D 10 i Direct3D 11. Te różnice przywrócenia DirectX do dostosowania sprzętu nowoczesnych grafiki i unleashing pełni możliwości, ale również przełączyć duże zmiany interfejsu API i umieść większą odpowiedzialność na programisty do zarządzania okresy istnienia zasobu i rywalizacji. Pomimo różnic diagnostyki grafiki z Direct3D 12 obsługuje funkcję parzystości z diagnostyki grafiki z Direct3D 11.2.
  
 Windows 10 zapewnia również obsługę dla wcześniejszych wersji programu Direct3D i gier i aplikacji, które opierają się na nich. Diagnostyki grafiki w programie Visual Studio w dalszym ciągu obsługuje Direct3D 10 i Direct3D 11 w systemie Windows 10.
  
### <a name="limited-direct2d-support"></a>Ograniczona obsługa Direct2D  
 Ponieważ Direct2D jest interfejs API trybu użytkownika, który jest oparty na Direct3D, można użyć diagnostyki grafiki do debugowania problemy z renderowaniem w aplikacjach korzystających z programem Direct2D. Jednak ponieważ rejestrowane są tylko podstawowe zdarzenia Direct3D, a nie zdarzenia Direct2D wyższego poziomu, zdarzenia Direct2D nie pojawią się na liście zdarzeń grafiki. Ponadto, ponieważ relacja między zdarzeniami Direct2D i wynikowymi zdarzeniami Direct3D nie jest zawsze jasna, używanie Graphics Diagnostics do debugowania problemów z renderowaniem w aplikacjach, które używają Direct2D, nie jest proste. Nadal można korzystać z Graphics Diagnostics, aby uzyskać informacje dotyczące problemów renderowania niskiego poziomu w aplikacjach, które korzystają z Direct2D.  
  
## <a name="graphics-diagnostics-features-in-visual-studio"></a>Funkcje diagnostyki grafiki w programie Visual Studio  
 Diagnostyki grafiki ma dedykowany interfejsu — okno analizatora grafiki — do diagnozowania problemów renderowania, ale również dodaje niektóre narzędzia do interfejsu programu Visual Studio.  
  
### <a name="the-graphics-toolbar-visual-studio"></a>Pasek narzędzi graficznych (Visual Studio)  
 Pasek narzędzi graficznych zapewnia szybki dostęp do poleceń diagnostyki grafiki.  
  
 **Rozpocznij diagnostykę** przycisk uruchamia aplikację pod nadzorem diagnostyki grafiki. Gdy aplikacja działa pod nadzorem diagnostyki grafiki, **Przechwytywanie następnej ramki renderowanych** przycisk jest aktywny.  
  
### <a name="diagnostics-capture-interface"></a>Interfejs przechwytywania danych diagnostycznych  
 Po uruchomieniu aplikacji pod nadzorem diagnostyki grafiki programu Visual Studio wyświetla interfejs sesji diagnostyki można użyć, aby przechwycić ramki, a które są również wyświetlane bieżącego obciążenia procesora CPU i procesora GPU. Obciążenie procesora CPU i procesora GPU jest wyświetlany pomoże zidentyfikować ramek, które należy przechwytywać z powodu ich charakterystyk wydajności, zamiast renderowania błędów.  
  
 Jedynym sposobem, aby przechwycić ramki, ale nie jest. Istnieje również możliwość przechwytywania z ramki za pomocą interfejsu przechwycenie programowe lub za pomocą programu wiersza polecenia przechwytywania dxcap.exe.  
  
 Zobacz [przechwytywanie informacji graficznych](capturing-graphics-information.md) Aby uzyskać więcej informacji.  
  
### <a name="gpu-usage"></a>Użycie procesora GPU  
 Diagnostyka grafiki można również profilowanie wydajności aplikacji Direct3D. Ponieważ dane profilowania będą niesymetryczna przez rejestrowanie szczegóły zdarzeń grafiki, jest oddzielony od przechwytywanie ramek do użycia z analizatora grafiki.  
  
 Zobacz [użycia procesora GPU](gpu-usage.md) Aby uzyskać więcej informacji.  
  
### <a name="directx-control-panel"></a>Panel sterowania DirectX  
 Panel sterowania DirectX to składnik DirectX, którego można użyć, aby zmienić sposób zachowania DirectX — na przykład włączyć wersję składników wykonawczych DirectX przeznaczoną do debugowania, wybrać rodzaj komunikatów debugowania, które są raportowane, oraz uniemożliwić korzystanie z niektórych funkcji sprzętowych karty graficznej w celu emulacji mniej zaawansowanego sprzętu. Ten poziom kontroli nad DirectX może pomóc w debugowaniu i testowaniu aplikacji DirectX. Dostęp do panelu sterowania DirectX można uzyskać z Visual Studio.  
  
#### <a name="to-open-the-directx-control-panel"></a>Aby otworzyć panel sterowania DirectX  
  
-   Na pasku menu wybierz **debugowania**, **grafiki**, **Panelu sterowania DirectX**.  
  
## <a name="graphics-analyzer"></a>Analizator grafiki  
 Analizatora grafiki programu Visual Studio jest interfejsem dedykowanych badania problemów renderowania i wydajności w ramkach już przechwyconych. Wewnątrz analizatora grafiki można znaleźć kilka narzędzi ułatwiających Eksploruj i zrozumieć sposób renderowania aplikacji. Inny rodzaj informacji na temat ramki, w której jest sprawdzana jest udostępnia narzędzia i narzędzi są przeznaczone do użycia w Porozumieniu do intuicyjnie wąskie w dniu źródła problemu renderowania, zaczynając od jego wyglądu w obiektu.  
  
 Na ilustracji przedstawiono typowe układu narzędzi w analizatorze grafiki.  
  
 ![Wszystkie grafiki debugera systemu windows](media/graphicsdebuggerwindows.png "GraphicsDebuggerWindows")  
  
### <a name="the-graphics-toolbar-graphics-analyzer"></a>Pasek narzędzi graficznych (analizator grafiki)  
 Pasek narzędzi graficznych zapewnia szybki dostęp do okna narzędzi analizatora grafiki.  
  
 ![Pasek narzędzi graficznych w trybie diagnostyki grafiki](media/vsg_toolbar.png "vsg_toolbar")  
  
### <a name="graphics-log-document"></a>Dokument dziennika grafiki  
 W analizatorze grafiki dokument dziennika grafiki jest najbardziej widocznym okna narzędzia. To okno reprezentuje wszystkie ramki, które przechwycone, uruchamiając aplikację pod nadzorem diagnostyki grafiki. W tym miejscu można wybrać innej ramki, aby sprawdzić lub wybierz określone pikseli, który chcesz zbadać za pomocą narzędzia historii pikseli. Obraz obiektu wyświetlany w tej zmiany do uwzględnienia aktualnie zaznaczonego zdarzenia, dzięki czemu można zobaczyć wpływ obiektu wraz z upływem czasu.  
  
 [Dokument dziennika grafiki](graphics-log-document.md) jest również punkt wejścia do narzędzia do analizy ramek, który pomaga zrozumieć wydajności ramki zmienia sposób, w niektórych aspektów renderowania są skonfigurowane i podając wyników testu wydajności Porównaj z oryginalnym.  
  
### <a name="event-list"></a>Lista zdarzeń  
 Graficzne zdarzeń oznaczania każdego wywołania interfejsu API programu Direct3D i zdarzeń zdefiniowanych przez użytkownika.  
  
 [Listy zdarzeń](graphics-event-list.md) są wyświetlane wszystkie zdarzenia grafiki, które zostały zarejestrowane podczas ramki jest sprawdzenie. Ułatwia znajdowanie, co jest ważne, listę zdarzeń mogą być wyświetlane hierarchicznie — ostatnie zmiany stanu poniżej kolejne wywołanie narysuj — lub jako oś czasu. Ponadto zdarzenia są oznaczone kolorami oparte na kolejki, do których należą, oraz można filtrować listę, aby wyświetlić tylko zdarzenia, które chcesz.  
  
 Po wybraniu zdarzenia na liście reszty narzędzi analizy grafiki odzwierciedlają stan ramki w czasie zdarzenia. Dzięki temu można zobaczyć efekt wszystkie zdarzenia na procesorze GPU. Na przykład można zobaczyć efekt natychmiastowego żadnych rysowania wywołać dla obiektu, nawet wtedy, gdy staje się on zasłonięty przez wywołań rysowania kolejne. Niektóre zdarzenia mają również hiperłącza, możesz wykonać, aby zobaczyć bardziej szczegółowe informacje o jego parametrów lub obiektów powiązanych zasobów.  
  
### <a name="pipeline-stages"></a>Etapy potoku  
 Każde wywołanie rysowania w aplikacji przechodzi przez potoku grafiki podał Direct3D. Na każdym etapie w potoku dane wyjściowe poprzedniego etapu jest przekształcenia przez mały program o nazwie programu do cieniowania i następnie przekazywane do kolejnego etapu, dopóki na koniec jest renderowany na ekranie. Wiele błędów renderowania wystąpić na granicę między etapy potoku, gdy format wyjściowy jest inny niż oczekiwana kolejnego etapu lub dowolnego jednego etapu po prostu tworzy niepoprawnych wyników. Zwykle tylko otrzymasz wyniki końcowe jak widać na ekranie i nie można łatwo sprawdzić, gdzie w potoku wystąpił błąd.  
  
 [Etapy potoku](graphics-pipeline-stages.md) okna wizualizuje wynik każdego etapu niezależnie, dzięki czemu można łatwiej ustalić którym etapie problem z renderowaniem najpierw pojawia się w. Po określeniu, czyli etap, można uruchomić debugowania cieniowania jego bezpośrednio w oknie etapy potoku.  
  
### <a name="graphics-state"></a>Stan grafiki  
 Operacje renderowania zależą od partii stanu, które są rozmieszczone na wiele obiektów. Wiele rodzajów problemy z renderowaniem są spowodowane przez niepoprawnie skonfigurowany stanu.  
  
 [Stanu](graphics-state.md) okna zbiera informacje o stanie istotne dla każdego wywołania rysunku razem w jednym miejscu, aby łatwiej znaleźć i przyciągać prezentuje zmiany stanu, które miały miejsce od czasu poprzedniego wywołania.  
  
### <a name="pixel-history"></a>Historia pikseli  
 W złożonych sceny nie jest nietypowe dla pikseli być cieniowania wiele razy w jednej ramce. Czasami wcześniejszych kolor jest po prostu zastąpiona, ale inne razy kolorów są łączone ze sobą w celu osiągnięcia skutki takich jak przezroczystość. Jeśli wynikiem połączenia ich razem nie ma wygląd prawo nie można łatwo sprawdzić, czy jest ponieważ jeden z kolorów jest niepoprawne lub jeśli występuje problem ze sposobem zostały połączone. Innym razem obiektu wydaje się brak, ponieważ jej udziału piksela zostało odrzucone z jakiegoś powodu.  
  
 [Historii pikseli](graphics-pixel-history.md) okna wizualizuje historii pełną programu do cieniowania każdego piksela ramki, w tym wkładów odrzucone. Wkładów, które nie zostały odrzucone wyświetla wyniki raw programu do cieniowania i jak każdy nowy kolor zostało połączone z poprzednim. Dzięki tym informacjom jest dużo łatwiejszy do znalezienia źródła błędów w pikselach, który blend wyników programu do cieniowania lub gdy obiektu odtwarzane brakuje ponieważ jej udziału piksela niepoprawnie został odrzucony.  
  
### <a name="event-call-stack"></a>Stos wywołań zdarzeń  
 Kod programu do cieniowania jest jedyne źródło problemy z renderowaniem w aplikacji Direct3D, czasami kodu źródłowego aplikacji przekazuje niewłaściwy parametr lub nie skonfiguruj Direct3D całkowicie poprawny. Jednego rodzaju błędu, który już wspomniano funkcja historii pikseli, mogą pomóc jest gdy obiektu odtwarzane brakuje ponieważ wszystkie jej piksele zostały odrzucone. Tego typu błędów zazwyczaj miejsce, gdy użytkownik błędnie skonfigurowane ustawienia, takie jak ten, który określa sposób test głębi i zwykle można znaleźć błędu w dowolnym miejscu w stosie wywołań brakuje obiektu wywołania rysowania.  
  
 [Stosu wywołań zdarzeń](graphics-event-call-stack.md) okno wyświetla stos wywołań pełną każde zdarzenie grafiki na liście zdarzeń, a nawet umożliwia przejście do aplikacji kod źródłowy, jeśli informacje o debugowaniu jest dostępna. Jest to zaawansowane narzędzie następujący błąd, z którym najpierw wygląda na to, na procesor GPU, przywracając miejscu jego występowania w kodzie źródłowym aplikacji.  
  
### <a name="object-table"></a>Tabela obiektów  
 Każda ramka renderuje Twojej aplikacji prawdopodobnie jest wspierany przez setki lub nawet tysiące obiektów zasobów. Te obejmują wstecz buforów i renderowania elementów docelowych, tekstury, buforów wierzchołków, indeks buforów, ogólne buforów — prawie wszystkie pamięta Direct3D jest obiektem.  
  
 [Tabeli obiektów](graphics-object-table.md) Wyświetla wszystkie obiekty, które istnieją w czasie zdarzeń grafiki wybrane listy zdarzeń. Ponieważ większość obiektów w typowej aplikacji tekstury, listę zdarzeń jest zoptymalizowany do zawierają szczegółowe informacje dotyczące obrazów w skrócie. Kolumna typu informuje, jakiego rodzaju obiekt jest w każdym wierszu, a kolumna Format dalsze zawiera podtyp lub wersji obiektu. Inne szczegółowe informacje są także wyświetlane. Niektóre obiekty mają również hiperłącza, które możesz wykonać, aby wyświetlić obiektu wyspecjalizowanego Viewer, takie jak tekstury (można wyświetlić tekstury jako obraz) lub buforów (możesz wybrać sposób podglądu buforu analizuje i wskazuje liczbę bajtów buforu raw, definiując buforu Format).  
  
### <a name="frame-analysis"></a>Analiza ramek  
 Grafika aplikacji nie wystarczy, że są prawidłowe — muszą być zbyt szybkie. Nawet w przypadku mniejszej mocy urządzeniami, takimi jak komputery przenośne zintegrowanego grafiki lub telefonów komórkowych. I będzie konieczne wygląda świetnie zbyt.  
  
 [Analizy ramek](graphics-frame-analysis.md) narzędzie Eksploruje potencjalnych optymalizacji wydajności automatycznie zmienia sposób aplikacja korzysta z Direct3D i podając wyniki testu do porównania. Na przykład analizy ramek można włączyć MCI mapowania na każdy tekstury, który może ujawnić tekstury, które mogą korzystać z mapowania MCI, ale nie jest ona włączona. Na sprzęcie, który ją obsługuje analizy ramek przedstawia również informacje zebrane liczniki wydajności procesora GPU — poziom informacji można zidentyfikować problemy z wydajnością poziomie sprzętu, takich jak dużej liczby wstrzymania pobierania tekstury lub liczba chybień pamięci podręcznej.  
  
 Ale analiza ramek nie jest niemal przechodzi do szybkiego — chodzi o uzyskanie większości wydajności, podczas gdy zwiększanie minimalnej liczbie jakości visual. Czasami kosztowne efekt, który wygląda bardzo dużych wyświetloną nie należy tego samego negatywny wpływ na ekranie małych telefonu, gdzie efekt łatwiejsze może wyglądać po prostu tak dobrze bez opróżnianie baterii. Automatyczne zmiany i wzorce, które zapewnia analizy grafiki ułatwiają znalezienie równowagi, które jest odpowiednie dla twojej aplikacji w różnych urządzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie wiersza polecenia przechwytywania](command-line-capture-tool.md)   
 [Debuger HLSL](hlsl-shader-debugger.md)