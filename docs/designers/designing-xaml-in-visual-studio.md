---
title: Projektowanie XAML w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: cd71c63ab20dc943d1e0c7ac94d374c9d3bca359
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="designing-xaml-in-visual-studio"></a>Projektowanie XAML w programie Visual Studio

Visual Studio i Blend for Visual Studio Podaj narzędzia visual dla tworzenia angażowanie interfejsów użytkownika, a multimedialną napotyka z XAML dla różnych typów aplikacji. Zarówno narzędzia korzystają ze wspólnego zestawu funkcji w tym edytorze XAML visual, ale program Blend for Visual Studio udostępnia narzędzia do projektowania dodatkowe bardziej zaawansowanych zadań, takich jak animacji i zachowania.  
  
Proces projektowania aplikacji zależy od wybranego narzędzia i platformy docelowej. Ten temat występuje porównanie narzędzi do projektowania XAML w programie Visual Studio i Blend for Visual Studio. Aby uzyskać bardziej szczegółowe wskazówki dotyczące korzystania z narzędzi zobacz następujące tematy:

- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML w programie Visual Studio](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)
- [Tworzenie nowoczesnych aplikacji klasycznych przy użyciu platformy Windows Presentation Foundation](create-modern-desktop-applications-with-windows-presentation-foundation.md)

## <a name="choosing-the-right-tool"></a>Wybieranie właściwego narzędzia  
 Wybór narzędzi projektowania jest stopniu zależne od zestawu umiejętności. Jeśli masz więcej zorientowane na kod, można napisać kod XAML w programie Visual Studio wykonywać zadania projektu nawet zaawansowanego. Jeśli masz więcej zorientowane na projekt, program Blend for Visual Studio umożliwia wykonywanie zaawansowanych zadań bez pisania kodu.  
  
 Można przełączać i z powrotem Visual Studio i Blend for Visual Studio, a nawet może mieć tego samego projektu Otwórz zarówno w tym samym czasie. Zmiany wprowadzone w plikach XAML w jednym IDE można zastosować za pośrednictwem automatyczne ponowne załadowanie podczas przełączania do środowiska IDE. Można kontrolować zachowanie Załaduj ponownie za pomocą opcji w **narzędzia**, **opcje** okno dialogowe albo IDE.  
  
### <a name="shared-capabilities"></a>Możliwości udostępnionych  
 W przypadku najprostszych zadań IDE programu Visual Studio i Blend for Visual Studio udostępniać ten sam zestaw windows i możliwości, niektóre niewielkie różnice. Niektóre najważniejsze funkcje obejmują:  
  
-   **Spójny interfejs użytkownika:** można zaprojektować aplikacji w kontekście znanego interfejsu użytkownika programu Visual Studio, co sprawia, że przełączenie między IDEs więcej przyjemne i produktywności środowiska. Blend dla Visual Studio ciemny motyw pomaga skupić się na zawartość, którą projektowania skracając kontrast między zawartości i interfejsu użytkownika używa programu Visual Studio. Zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
     ![Program Blend for Visual Studio IDE](../designers/media/blendide.png "BlendIDE")  
  
-   **XAML IntelliSense:** zarówno IDEs obsługuje wszystkie funkcje typowe można oczekiwać od IntelliSense uzupełniania instrukcji, obsługę typowych operacji Edytor komentarzy i formatowania kodu i nawigacji do zasobów, w tym powiązanie i kod.  
  
-   **Podstawowe możliwości debugowania:** można teraz debugowania w programie Blend, w tym ustawianie punktów przerwania w kodzie do debugowania uruchomionej aplikacji. Aby zapewnić spójne środowisko debugowania w programie Visual Studio, program Blend for Visual Studio zawiera większość debugowania systemu windows i paski narzędzi Visual Studio. Zaawansowane możliwości debugowania, takie jak Diagnostyka i analiza kodu są dostępne tylko w programie Visual Studio. Zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).  
  
-   **Środowisko ponowne załadowanie pliku:** można edytować pliki XAML albo program Blend for Visual Studio lub Visual Studio, i mieć edycji plików Załaduj ponownie automatycznie podczas przełączania między nimi. Aby zminimalizować przestoje przepływu pracy, można teraz ustawić pliku preferencji Załaduj ponownie w oknie dialogowym ponowne załadowanie pliku.  
  
     ![Środowisko ponowne załadowanie pliku](../designers/media/blendfilereload.png "BlendFileReload")  
  
-   **Zsynchronizowane ustawienia i układy:** układy niestandardowe umożliwiają zapisać i zastosować dostosowania układu okna narzędzia. Visual Studio zsynchronizuje te dostosowania i preferencji dotyczących programu Blend for Visual Studio i Visual Studio na maszynach gdy zalogujesz się przy użyciu tego samego konta Microsoft. Zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
-   **Typowe Eksploratora rozwiązań:** Eksploratora rozwiązań udostępnia zorganizowany widok projektów i ich pliki, a także łatwy dostęp do poleceń skojarzonych z nimi. W Eksploratorze rozwiązań łatwiej jest praca z projektami duże przedsiębiorstwa. Zobacz [rozwiązań i projektów](../ide/solutions-and-projects-in-visual-studio.md).  
  
-   **Program Team Explorer:** za pomocą programu Team Explorer można zarządzać swoje projekty z repozytoria GIT lub TFS w celu ułatwienia współpraca z zespołem. Zobacz [pracy w programie Team Explorer](http://msdn.microsoft.com/Library/fd7a5cf7-7916-4fa0-b5e6-5a83cf377a02).  
  
-   **NuGet:** można zarządzać pakietami NuGet w Blend for Visual Studio i Visual Studio. NuGet jest Menedżer pakietów dla programu .NET Framework, które upraszcza instalacji i usuwania pakietów z rozwiązania.  
  
## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Zaawansowane możliwości w programie Blend for Visual Studio  
 Aby zwiększyć wydajność pracy, należy wziąć pod uwagę przy użyciu programu Blend for Visual Studio dla następujących zadań. Są to obszary, w którym program Blend for Visual Studio oferuje więcej szybkość i funkcji niż projektanta programu Visual Studio lub tylko kodu.  
  
|Do|Visual Studio|Blend for Visual Studio|Więcej informacji|  
|--------|-------------------|-----------------------------|----------------------|  
|**Tworzenie animacji**|Nie ma narzędzia projektowania dla animacji; należy utworzyć je programowo. Wymaga to zrozumienie animacji i chronometrażu systemu WPF i doświadczenia z dużą ilością kodowania.|Wizualnie tworzyć animacje i można przeglądać je w programie Blend for Visual Studio. Jest szybsze i bardziej dokładne niż tworzenia animacji w kodzie. Można dodać wyzwalaczy do obsługi interakcji z użytkownikiem, a można przełączyć na kod, aby dodać obsługę zdarzeń i inne funkcje.|[Animowanie obiektów](../designers/animate-objects-in-xaml-designer.md)|  
|**Przekształcić ścieżki do manipulowania łatwiejsze kształty i tekst**|Nieobsługiwane.|Niewielkie lub znaczne zmiany do kształtów (na przykład prostokąty i wielokropek) ułatwia konwertując je do ścieżki, które zapewniają kontrolę lepiej edycji.  Można zmienić lub łączenia ścieżek i utworzyć ścieżek złożonych z wielu kształtów.<br /><br /> Bloki tekstu można również konwertowanie ścieżki do manipulowania je jako obrazy wektora.|[Rysowanie kształtów i ścieżek](../designers/draw-shapes-and-paths.md)|  
|**Dodaj interakcję do projektów interfejsu użytkownika**|Wymaga kodu C#, VB lub C++.|Przeciągnij i upuść zachowań na formantów interakcyjności w statycznej projektów. Wstawki kodu gotowe do użycia, które zapewniają funkcje, takie jak zmiany stanu wizualnego, powiększenia i przeciągnij i upuść będą zachowania. Istnieje rosnącej gamy zachowania, które są dostępne, i Utwórz swój własny.<br /><br /> Można następnie dostosować zachowanie każdego przez zmianę jego właściwości w programie Blend for Visual Studio lub przez dodanie obsługi zdarzeń w kodzie.|[Wstawianie kontrolek i modyfikowanie ich zachowania](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)|  
|**Użyj programu Adobe kompozycji**|Nieobsługiwane.|Importowanie Adobe FXG PhotoShop i Illustrator kompozycji i implementować interfejsu użytkownika w programie Blend for Visual Studio.|[Wstawianie obrazów, klipów wideo i klipów audio](../designers/insert-images-videos-and-audio-clips-in-xaml-designer.md)|  
|**Edytowanie formantów, szablonów i style**|Wymaga kodowania i wiedzy style WPF i szablonów.|Włącz żadnego obrazu w formancie.<br /><br /> Użyj narzędzi edycji szablonu, aby wprowadzić zmiany do kontroli, style i szablony z wystarczy kilka kliknięć myszą.<br /><br /> Na przykład można użyć programu Blend for Visual Studio styl zasobów implementuje wspólnych formantów WPF (takie jak przyciski pola listy, paski przewijania, menu, itp.) i zmienianie ich koloru, stylu lub podstawowej szablonu bezpośrednio w programie Blend for Visual Studio. Następnie można przełączyć na kod dla ostateczne poprawki Jeśli chcesz.|[Modyfikowanie stylu obiektów](../designers/modify-the-style-of-objects-in-blend.md)|  
|**Łączenie z danymi interfejsu użytkownika**|Utwórz źródło danych z zasobów, takich jak bazy danych programu SQL Server, WCF lub usługi sieci web, obiektów lub listy programu SharePoint i powiązać źródła danych do formantów interfejsu użytkownika.<br /><br /> Dane czasu projektowania należy utworzyć ręcznie środowisko projektowania interaktywnego.|Utwórz dane przykładowe łatwo dla prototypowania i testowania. Przełącz, aby dane dynamiczne, gdy wszystko jest gotowe.<br /><br /> Blend dla Visual Studio generowania danych możliwości istnieją zaległe (można dodać nazwy, cyfry, adresy URL, zdjęć, łatwe w locie) i może zaoszczędzić dużo czasu.<br /><br /> W przypadku danych na żywo można powiązać formantów interfejsu użytkownika do pliku XML lub dowolnego źródła danych CLR.|[Wyświetlanie danych](../designers/display-data-in-blend.md)|  
  
 Aby uzyskać więcej informacji dotyczących zaawansowanych projektu XAML Zobacz. [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)