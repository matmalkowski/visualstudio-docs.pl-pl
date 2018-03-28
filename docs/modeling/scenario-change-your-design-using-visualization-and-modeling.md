---
title: 'Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 225383c3958b6af604463fe68d80481d49bd6e04
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania
Upewnij się, że systemu oprogramowania zaspokoi potrzeby użytkowników z wykorzystaniem wizualizacji i modelowania narzędzia w programie Visual Studio.
Użyj narzędzi, takich jak mapy kodu, diagramy zależności i diagramów klas do:  

 Aby dowiedzieć się, które wersje programu Visual Studio obsługują poszczególnych narzędzi, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

-   Wyjaśnienie procesów biznesowych i wymagania dotyczące użytkowników.  

-   Wizualizowanie i eksplorowanie istniejącego kodu.  

-   Opisano zmiany w istniejącym systemie.  

-   Sprawdź, czy system spełnia wymagania.  

-   Zachowaj kod jest zgodne z projektem.  

 W tym przewodniku:  

-   W tym artykule opisano, jak te narzędzia mogą korzystać projektu oprogramowania.  

-   Pokazuje, jak można użyć tych narzędzi, niezależnie od tego użytkownika podejście do tworzenia, z przykładowy scenariusz.  

 Aby dowiedzieć się więcej na temat tych narzędzi i scenariusze, które obsługują, zobacz:  

-   [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)  

-   [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)  

##  <a name="ScenarioOverview"></a> Omówienie scenariusza  
 W tym scenariuszu opisano odcinki z cykle rozwoju oprogramowania dwóch fikcyjnej firmy: obiad teraz, a następnie lucerny publikowania. Teraz obiad udostępnia usługę dostarczania opartych na sieci Web zawierają najważniejsze nowości w Seattle. Kolejność potrawy klientom i opłacać je w witrynie obiad teraz. Zamówienia są następnie wysyłane do odpowiednich restauracji lokalnych w celu dostarczania. Publikowania lucerny firmy w Nowym Jorku działa wiele firm, zarówno poza, jak i w sieci Web. Na przykład są uruchamiane witryny sieci Web gdzie zamieścić restauracji recenzje klientów.  

 Lucerny ostatnio nabyte obiad teraz i chce wprowadzić następujące zmiany:  

-   Integracja witryn sieci Web, dodając restauracji przegląd możliwości obiad teraz.  

-   Zastąp obiad teraz przez system płatności lucerny przez system.  

-   Rozwiń węzeł usługi obiad teraz w regionie.  

 Teraz obiad używa eXtreme programowanie i SCRUM. Mają one pokrycie testu bardzo duże i bardzo nieco nieobsługiwany kod. One zminimalizować ryzyko tworzenie małych, ale wersje robocze systemu, a następnie stopniowo dodanie funkcji. Opracowują one ich kodu za pośrednictwem krótko- i częste iteracji. Dzięki temu je bezpiecznie dążenie zmiany, często zrefaktoryzuj kod i uniknąć "na początku big projektu".  

 Lucerny obsługuje znacznie większe i złożonych kolekcji systemów, niektóre z nich więcej niż 40 lat. Są one wyjątkową ostrożność podczas wprowadzania zmian z powodu złożoności i zakres starszej wersji kodu. Bardziej rygorystyczne procesu projektowania, preferowanie do projektowania rozwiązania szczegółowe i do projektowania i zmiany wprowadzone podczas tworzenia dokumentów są zgodne.  

 Oba zespoły diagramy modelowania w programie Visual Studio ułatwia ich opracowywanie systemów, które odpowiadają potrzebom użytkownika. Używają Team Foundation Server równolegle z innych narzędzi, aby ułatwić planowanie, organizować i zarządzanie siecią firmową.  

 Aby uzyskać więcej informacji na temat programu Team Foundation Server zobacz:  

-   [Planowanie i śledzenie pracy](#PlanningTracking)  

-   [Testowanie, sprawdzanie poprawności i ewidencjonowanie zaktualizowanego kodu](#TestValidateCheckInCode)  

##  <a name="ModelingDiagramsTools"></a> Role architektura i modelowanie diagramów w rozwoju oprogramowania  
 W poniższej tabeli opisano role, które tych narzędzi można odtworzyć wiele i różnych etapach cyklu tworzenia oprogramowania:  

||**Wymagania dotyczące użytkownika modelowania**|**Modelowanie biznesowe procesu**|**Architektura systemu i projektowanie**|**Kod — wizualizacja & eksploracji**|**Weryfikacja**|  
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|  
|Diagram języka specyficznego dla domeny (DSL)|Tak|Tak|Tak|||  
|Diagram zależności, Walidacja warstw|||Tak|Tak|Tak|  
|Mapy kodu|||Tak|Tak|Tak|  
|Projektant klas (oparte na kodzie)||||Tak||  

Aby narysować diagramy zależności, należy utworzyć jako część istniejącego rozwiązania lub do nowego projektu modelowania. Diagramy te muszą być tworzone w projekcie modelowania.
Elementów na diagramach zależności znajdują się w projekcie modelowania, ale nie są przechowywane w wspólnego modelu. Mapy kodu i diagramów klasy .NET utworzone na podstawie kodu istnieją spoza projektu modelowania.  

 Zobacz:  

-   [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)  

-   [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)  

-   [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  

-   [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

 Oba zespoły Ponadto używają walidacji zależności do upewnij się, że kod opracowywane nadal zgodne z projektem.  

 Zobacz:  

-   [Utrzymywanie kodu zgodne z projektem](#ValidatingCode)  

-   [Architektura logiczna opisują: diagramy zależności](#DescribeLayers)  

-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)  

    > [!NOTE]
    >  Niektóre wersje programu Visual Studio obsługuje walidacji zależności i wersji tylko do odczytu map kodu do wizualizacji i modelowania. Aby dowiedzieć się, które wersje programu Visual Studio obsługują tę funkcję, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

##  <a name="UnderstandingCommunicating"></a> Opis i przekazywania informacji o systemie  
 Nie ma wymaganych aby za pomocą programu Visual Studio modelowanie diagramów, dzięki czemu można ich używać jako mieściły się potrzeb lub metody. Zwykle zespoły ponownie ich modeli wielokrotnie powtarzane i często w projekcie. Każdy diagram oferuje określonego sile ułatwiające zrozumienie, opis i komunikować się różne aspekty systemu opracowywane.  

 Teraz obiad i Lucerna komunikować się z każdym innym i uczestników projektu przy użyciu diagramów jako ich języka wspólnego. Na przykład obiad używa teraz diagramy do wykonywania następujących zadań:  

-   Tworzenie wizualizacji kodu istniejących.  

-   Komunikować się z lucerny o nowych lub zaktualizowanych scenariuszy.  

-   Zidentyfikuj zmiany, które są wymagane do obsługi nowych lub zaktualizowanych scenariuszy.  

 Lucerny używa diagramy do wykonywania następujących zadań:  

-   Więcej informacji na temat procesu biznesowego obiad teraz.  

-   Zrozumienie projektowania systemu.  

-   Komunikować się z obiad teraz o wymaganiach dotyczących nowych lub zaktualizowanych użytkowników.  

-   Aktualizacje dokumentu do systemu.  

 Diagramy są zintegrowane z Team Foundation Server, więc zespołów można zaplanować, zarządzanie i łatwo śledzić pracę. Na przykład użyć ich modeli do identyfikowania przypadków testowych i zadań związanych z projektowaniem i do oszacowania pracy. Łącza lucerny Team Foundation Server elementów roboczych, aby elementy modelu, aby mogli monitorować postęp i upewnij się, że system spełnia wymagania dotyczące użytkowników. Na przykład one łączy przypadki użycia elementów roboczych przypadek testowy, zobaczą, że spełnione są przypadki użycia, gdy wszystkie testy zostały zaliczone pomyślnie.  

 Przed zespoły zaewidencjonować zmian, ich sprawdzić kod przed testy i projekt uruchamiając kompilacje, które obejmują zależności weryfikacji i testów automatycznych. Dzięki temu, upewnij się, że zaktualizowanego kodu nie są w konflikcie z projektu i wcześniej przerwanie pracy funkcji.  

 Zobacz:  

-   [Identyfikowanie zmiany w istniejącym systemie](#DeterminingChanges)  

-   [Utrzymywanie kodu zgodne z projektem](#ValidatingCode)  

-   [Ogólne porady dotyczące tworzenia i używania modeli](#GeneralTips)  

-   [Planowanie i śledzenie pracy](#PlanningTracking)  

-   [Testowanie, sprawdzanie poprawności i ewidencjonowanie zaktualizowanego kodu](#TestValidateCheckInCode)  

###  <a name="DeterminingChanges"></a> Identyfikowanie zmiany w istniejącym systemie  
 Teraz obiad musi szacowania kosztów spełnienia nowe wymaganie. Zależy to częściowo ile tej zmiany będzie miało wpływ na inne części systemu. Aby ułatwić im to zrozumieć, co deweloperów obiad teraz tworzy tych map i diagramów z istniejącego kodu:  

|**Mapa lub diagram**|**Pokazuje**|  
|------------------------|---------------|  
|*Mapy kodu*<br /><br /> Zobacz:<br /><br /> -   [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Przeglądanie i rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Zależności i relacje w kodzie.<br /><br /> Na przykład obiad może rozpocząć od przejrzenia map kodu zestawu omówienie zestawy oraz ich zależności. Ich można przejść do szczegółów mapy, aby zapoznać się z przestrzeni nazw i klasy w tych zestawów.<br /><br /> Teraz obiad można również utworzyć mapy, aby zapoznać się z konkretnym obszarów i innych rodzajów relacji w kodzie. Aby znaleźć i wybrać obszarów i relacje, które ich interesują korzystają z Eksploratora rozwiązań.|  
|*Diagram klas opartych na kodzie*<br /><br /> Zobacz [porady: Dodawanie diagramów klasy do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Istniejące klasy w kodzie|  

 Na przykład deweloper tworzy mapę kodu. Dopasowuje ona jego zakres, aby skoncentrować się na obszarów, które wpływają na nowy scenariusz. Te obszary są zaznaczone i wyróżnione na mapie:  

 ![Wykres zależności Namespace](../modeling/media/namespace_reviewsystem.png "Namespace_ReviewSystem")  

 **Namespace mapy kodu**  

 Deweloper rozszerza wybrane obszary nazw ich klas, metod i relacji:  

 ![Wykres zależności rozwinięte przestrzeni nazw](../modeling/media/dep_reviewsystem.png "Dep_ReviewSystem")  

 **Mapa kodu rozwinięte przestrzeni nazw z widoczne linki międzygrupowe**  

 Deweloper sprawdza, czy kod, aby znaleźć dotyczy klasy i metody. Aby zobaczyć efekty każdej zmianie po wykonaniu ich, regenerate kod mapuje po każdej zmianie. Zobacz [tworzenie wizualizacji kodu](../modeling/visualize-code.md).  

 Do opisania zmian do innych części systemu, takie jak składników i interakcje, zespół może narysuj tych elementów tablic. Może również przyjmą poniższych diagramach w programie Visual Studio, aby szczegóły może być przechwycone, zarządzane i zrozumiałe dla obu zespołów:  

|**Diagramy**|**W tym artykule opisano**|  
|------------------|-------------------|  
|*Diagram klas opartych na kodzie*<br /><br /> Zobacz [porady: Dodawanie diagramów klasy do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Istniejące klasy w kodzie.|  

###  <a name="ValidatingCode"></a> Utrzymywanie kodu zgodne z projektem  
 Teraz obiad należy się upewnić, że zaktualizowanego kodu jest zgodne z projektem. Tworzenia diagramy zależności, które opisują warstwy funkcjonalności w systemie, określ dozwolone zależności między rozwiązania ich i skojarz artefakty do nich.  

|**Diagram**|**W tym artykule opisano**|  
|-----------------|-------------------|  
|*Diagram zależności*<br /><br /> Zobacz:<br /><br /> -   [Tworzenie diagramów zależności w kodzie](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|Architektura logiczna kodu.<br /><br /> Diagram zależności organizuje i mapuje artefaktów w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania abstrakcyjnej grupy o nazwie *warstwy*. Te warstwy identyfikowanie ról, zadania lub funkcje służące do wykonywania tych artefaktów w systemie.<br /><br /> Diagramy warstw są przydatne w przypadku opisujące projektowi systemu i sprawdzanie poprawności zmieniające się kod dla tego projektu.<br /><br /> Aby utworzyć warstw, przeciągnij elementy z Eksploratora rozwiązań, mapy kodu, Widok klas i przeglądarka obiektów. Do rysowania nowych warstw, Użyj przybornika, lub kliknij prawym przyciskiem myszy powierzchnię diagramu.<br /><br /> Aby wyświetlić istniejące zależności, kliknij prawym przyciskiem myszy powierzchnię warstwy, a następnie kliknij przycisk **Generowanie zależności**. Aby określić zależności zamierzone, Rysuj nowe zależności.|  

 Na przykład na poniższym diagramie zależności opisano zależności między warstwami i liczbę artefaktów, które są skojarzone z każdą warstwę:  

 ![Diagram zależności system płatności zintegrowanego](../modeling/media/layer_integrated_dnlucerne.png "Layer_Integrated_DNLucerne")  

 **Diagram zależności**  

 Aby upewnić się, że nie występują konflikty z projektu podczas tworzenia kodu, używa zespołów, sprawdzanie poprawności zależności w kompilacji, które są uruchamiane na Team Foundation Build. Tworzy także niestandardowego zadania MSBuild do wymagania weryfikacji zależności w swoich operacji wyboru. Raporty kompilacji ich użyć do zbierania błędy sprawdzania poprawności.  

 Zobacz:  

-   [Definiowanie procesu kompilacji](http://msdn.microsoft.com/Library/61593e10-d24b-492f-b19a-af4d85abea6b)  

-   [Aby zatwierdzić zmiany, użyj procesu kompilacji warunkowe zaewidencjonowanie](http://msdn.microsoft.com/Library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)  

-   [Dostosuj szablon procesu kompilacji](http://msdn.microsoft.com/Library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  

###  <a name="GeneralTips"></a> Ogólne porady dotyczące tworzenia i używania modeli  

-   Diagramy większości składają się z węzłów, które są połączone liniami. Dla każdego typu diagram przybornika zawiera różne rodzaje węzłów i wierszy.  

     Aby otworzyć w przyborniku **widoku** menu, kliknij przycisk **przybornika**.  

-   Aby utworzyć węzeł, przeciągnij je z przybornika do diagramu. Niektóre rodzaje węzłów musi przeciągnięto istniejących węzłów. Na przykład na diagramie składników nowy port należy dodać do istniejącego składnika.  

-   Aby utworzyć linię lub połączenie, kliknij w przyborniku odpowiednie narzędzia, kliknij węzeł źródła, a następnie kliknij węzeł docelowy. Wiersze mogą być tworzone tylko między niektórych typów węzłów. Kiedy wskaźnik myszy nad możliwe źródłowa lub docelowa, wskaźnik wskazuje, czy można utworzyć połączenia.  

###  <a name="PlanningTracking"></a> Planowanie i śledzenie pracy  
 Visual Studio modelowania diagramów są zintegrowane z Team Foundation Server, dzięki czemu można zaplanować, zarządzanie i łatwiej śledzenie pracy. Zarówno zespoły użyć modeli, aby zidentyfikować przypadki testowe i zadań związanych z projektowaniem i do oszacowania pracy. Tworzy lucerny i elementy do elementów modelu, takie jak przypadków użycia lub składników pracy łącza Team Foundation Server. Dzięki temu je monitorować ich postęp i śledzenie ich pracy do potrzeb użytkowników. Pomoże im to upewnij się, że swoje zmiany w dalszym ciągu spełnienia tych wymagań.  

 W miarę postępów prac ich aktualizacji zespoły elementów pracy do uwzględnienia czas poświęcony na ich na ich zadań. Również monitorować i zgłosić stan w pracy przy użyciu następujących funkcji serwera Team Foundation Server:  

-   Codzienne *raporty postęp* który Pokaż, czy będzie ich zakończeniu planowanej pracy w oczekiwanym czasie. Generują inne podobne raporty z serwera Team Foundation Server, aby śledzić postęp usterek.  

-   *Arkusza iteracji* który używa programu Microsoft Excel ułatwiających zespołowi monitorować i równoważenie obciążenia między jego elementów członkowskich. Ten arkusz jest połączony z Team Foundation Server i zapewnia fokus omówienie podczas ich postępu regularne spotkania.  

-   A *pulpitu nawigacyjnego programowanie* używającą Office Project do zachowania zespołu informację o ważnych informacji.  

 Zobacz:  

-   [Śledzenie pracy za pomocą programu Visual Studio Team Services lub program Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)  

-   [Wykresy, pulpity nawigacyjne i raporty dla programu Visual Studio ALM](http://msdn.microsoft.com/Library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)  

-   [Tworzenie zaległości i zadań za pomocą programu Project](http://msdn.microsoft.com/Library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)  

###  <a name="TestValidateCheckInCode"></a> Testowanie, sprawdzanie poprawności i sprawdzania w kodzie  
 Jak zespołów, dokończ wszystkie zadania, sprawdź swój kod do kontroli wersji Team Foundation i otrzymywać monitów Team Foundation Server nie pamięta one. Przed Team Foundation Server akceptuje zaewidencjonowania, zespołów uruchamiania testów jednostkowych i walidacji zależności można zweryfikować kodu przed ich przypadków testowych i projektu. Korzystają z Team Foundation Server do uruchomienia kompilacji, testy jednostkowe automatycznych i regularnie walidacji zależności. Dzięki temu, upewnij się, że kod spełnia następujące kryteria:  

-   Działa.  

-   Go nie DZIEL wcześniej pracy kodu.  

-   Nie powoduje konfliktu z projektu.  

 Teraz obiad ma dużą kolekcję zautomatyzowanych testów, które lucerny można użyć ponownie, ponieważ prawie wszystkie nadal stosować. Lucerny można również rozbudowywać te testy i dodać nowe, aby pokrywał się nowych funkcji. Aby uruchomić testy ręczne zarówno również użyć programu Visual Studio.  

 Aby upewnić się, że kod jest zgodny ze projektu, zespołów, należy skonfigurować ich kompilacji w Team Foundation Build uwzględnienie walidacji zależności. Jeśli wystąpią konflikty, raport jest generowany ze szczegółami.  

 Zobacz:  

-   [Testowanie aplikacji](https://www.visualstudio.com/docs/test/overview)  

-   [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)  

-   [Korzystanie z kontroli wersji](http://go.microsoft.com/fwlink/?LinkID=525605)  

-   [Kompilowanie i wydawanie](/vsts/build-release/index)  

##  <a name="UpdatingSystem"></a> Aktualizowanie systemu za pomocą wizualizacji i modelowania  
 Lucerny i obiad teraz należy zintegrować ich systemy płatności. W poniższych sekcjach przedstawiono diagramów modelowania w programie Visual Studio ułatwić ich wykonywania tego zadania:  

-   [Tworzenie wizualizacji kodu istniejących: Mapy kodu](#VisualizeCode)  

-   [Zdefiniuj słownik typów: diagramy klas](#DefineClasses)  

-   [Architektura logiczna opisują: diagramy zależności](#DescribeLayers)  

 Zobacz:  

-   [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)  

-   [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)  

-   [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)  

###  <a name="VisualizeCode"></a> Tworzenie wizualizacji kodu istniejących: Mapy kodu  
 Mapy kodu wyświetlenie bieżącego organizacji i relacji w kodzie. Elementy są reprezentowane przez *węzłów* na mapie, i relacje są reprezentowane przez *łącza*. Mapy kodu można wykonywać następujące rodzaje zadań:  

-   Poznaj nieznane kodu.  

-   Dowiedz się, jak i gdzie proponowanej zmiany mogą mieć wpływ na istniejący kod.  

-   Znajdź obszary złożoności, fizycznych zależności lub wzorce lub innych obszarów, które mogą korzystać z ulepszeń.  

 Na przykład obiad teraz oszacować koszt Aktualizacja składnika PaymentProcessing. Zależy to częściowo ile tej zmiany będzie miało wpływ na inne części systemu. Aby ułatwić im to zrozumieć, jedna deweloperów obiad teraz generuje mapy kodu z kodu i dostosowuje obszarów, które mogą wpłynąć na zmianę fokusu zakresu.  

 Następujące Mapa pokazuje zależności między klasami PaymentProcessing a innymi składnikami systemu obiad teraz, które są wyświetlane jako wybrane:  

 ![Wykres zależności dla obiad teraz system płatności](../modeling/media/dep_dnpayment.png "Dep_DNPayment")  

 **Mapy kodu obiad teraz system płatności**  

 Deweloper Eksploruje mapy rozszerzania klasy PaymentProcessing i wybierając jej elementów członkowskich, aby zobaczyć obszarów, które są potencjalnie wpływ:  

 ![Metody wewnątrz PaymentProcessing i zależności](../modeling/media/depgraph_expandeddn.png "DepGraph_ExpandedDN")  

 **Metody wewnątrz klasy PaymentProcessing oraz ich zależności**  

 Generują one następujące mapy dla System płatności lucerny sprawdzić jej klas, metod i zależności. Zespół widzi lucerny systemu może być także wymagane pracy na interakcję z innymi częściami obiad teraz:  

 ![Wykres zależności dla system płatności lucerny](../modeling/media/depgraph_lucernepay.png "DepGraph_LucernePay")  

 **Mapy kodu lucerny System płatności**  

 Oba zespoły współdziałać, aby określić zmiany, które są wymagane do integracji z dwóch systemów. Zdecydują Refaktoryzuj części kodu, dzięki czemu będzie łatwiejszy do aktualizacji. Klasa PaymentApprover zostanie przeniesione do obszaru nazw DinnerNow.Business i będzie wymagać pewnych nowych metod. Teraz obiad klasy obsługujące transakcje będą miały własnej przestrzeni nazw. Zespoły tworzenie i używanie elementów roboczych do planu, organizować i śledzenie ich pracy. Elementy modelu, w których jest użyteczny połączone elementy robocze.  

 Po reorganizacja kod, zespołów Generowanie nowej mapy kodu, aby zobaczyć zaktualizowane struktury i relacji:  

 ![Wykres zależności z kodem reorganizowane po kolei](../modeling/media/depgraph_integrated.png "DepGraph_Integrated")  

 **Mapy kodu z kodem reorganizowane po kolei**  

 Ta mapa pokazuje, że klasa PaymentApprover znajduje się teraz w przestrzeni nazw DinnerNow.Business i ma kilka nowych metod. Klasy transakcji obiad teraz mają teraz własne nazw PaymentSystem, co ułatwia biznesowych w radzeniu sobie z tym kodem później.  

#### <a name="creating-a-code-map"></a>Tworzenie mapy kodu  

-   W przypadku szybki przegląd kodu źródłowego wykonaj następujące kroki, aby wygenerować mapę kodu:  

     Na **architektura** menu, kliknij przycisk **Generuj mapę kodu dla rozwiązania**.  

     Szybkie omówienie skompilowany kod Utwórz mapę kodu puste, a następnie przeciągnij pliki zestawu lub plików binarnych powierzchnię mapy.  

-   Aby zapoznać się z określonym kod lub elementy rozwiązania, umożliwia wybór elementów i relacji, które mają być wyświetlane Eksploratora rozwiązań. Możesz następnie wygenerować nową mapę lub Dodaj wybrane elementy do istniejącej mapy. Zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).  

-   Aby pomóc w eksplorowaniu mapy, rozmieszczanie układu, aby pasujące do rodzaje zadań, które chcesz wykonać.  

     Na przykład w celu wizualizacji Tworzenie warstw w kodzie, wybierz układ drzewa. Zobacz [przeglądania i zmieniać code map](../modeling/browse-and-rearrange-code-maps.md).  

#### <a name="summary-strengths-of-code-maps"></a>Podsumowanie: Sile mapy kodu  
 Mapy kodu ułatwiają:  

-   Informacje o organizacji i relacje w istniejącym kodzie.  

-   Określenie obszarów, które mogą wpłynąć na proponowanej zmiany.  

-   Znajdź obszarów złożoności, wzorce, warstwy lub innymi obszarami, które można poprawić, aby ułatwić Obsługa, zmienianie i ponowne użycie kodu.  

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  

|**Diagram**|**W tym artykule opisano**|  
|-----------------|-------------------|  
|Diagram zależności|Architektura logiczna systemu. Aby upewnić się, że kod jest zgodne z projektem, należy użyć walidacji zależności.<br /><br /> Aby zidentyfikować istniejące dependencys lub zamierzone dependencys, utwórz mapę kodu i grupować powiązane elementy. Aby utworzyć diagram zależności, zobacz:<br /><br /> -   [Tworzenie diagramów zależności w kodzie](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)|  
|Diagram klas (oparte na kodzie)|Istniejące klasy w kodzie dla określonego projektu.<br /><br /> Wizualizacji i modyfikowania istniejącej klasy w kodzie, za pomocą projektanta klas.<br /><br /> Zobacz [porady: Dodawanie diagramów klasy do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|  

###  <a name="DefineClasses"></a> Zdefiniuj słownik typów: diagramy klas  
 Diagramy klas Definiowanie jednostek, terminy i pojęcia uczestniczących w systemie oraz ich relacji między sobą. Na przykład można te diagramy podczas tworzenia opisano atrybuty i operacje dla każdej klasy, niezależnie od ich implementacji języka i styl.  

 Ułatwia lucerny opisują i przedyskutować jednostek, które uczestniczą w przypadku użycia płatności procesu przyjmą na poniższym diagramie klasy:  

 ![Przetwarzanie płatności jednostek na diagramie klas](../modeling/media/uml_payentities.png "UML_PayEntities")  

 **Proces jednostek płatności na diagramie klas**  

 Ten diagram przedstawia, że klient może mieć wiele zleceń i opłacać zamówienia na różne sposoby. Prezentowanie ich i CreditCard dziedziczyć płatności.  

 Podczas tworzenia lucerny używa następujących diagram klas do opisywania, żeby omówić szczegóły każdej klasy:  

 ![Przetwarzanie płatności szczegóły jednostki na diagramie klas](../modeling/media/uml_payment.png "UML_Payment")  

 **Szczegóły procesu płatności na diagramie klas**  

#### <a name="drawing-a-class-diagram"></a>Rysowanie diagramu klas  
 Diagram klas zawiera następujące główne funkcje:  

-   Typy, takich jak klasy, interfejsy i wyliczenia:  

    -   A *klasy* jest definicji obiektów, które mają określone właściwości strukturalne i funkcjonalne.  

    -   *Interfejsu* definiuje część widoczne na zewnątrz zachowanie obiektu.  

    -   *Wyliczenie* jest klasyfikator, który zawiera listę wartości literału.  

-   *Atrybuty* wartości określonego typu opisujące każde wystąpienie *klasyfikatora*. Klasyfikator jest ogólne nazwy dla typów, składników, przypadków użycia i nawet uczestników.  

-   *Operacje* metody lub funkcji, które można wykonać wystąpień klasyfikatora.  

-   *Skojarzenie* wskazuje określonego rodzaju relacji między dwoma klasyfikatory.  

    -   *Agregacji* jest skojarzeniem wskazuje udostępnionego własność między klasyfikatory.  

    -   A *kompozycji* jest skojarzeniem wskazuje całkowitą część relacji między klasyfikatory.  

     Aby wyświetlić agregacji lub kompozycji, ustaw **agregacji** właściwości skojarzenia. **Udostępnione** pokazuje agregacji i **złożonego** pokazuje kompozycji.  

-   A *zależności* wskazuje, że definicja jednego klasyfikatora może zmiana definicji innego klasyfikatora.  

-   A *generalizacji* wskazuje, czy określonych klasyfikatora dziedziczy część definicję klasyfikatora ogólnego. A *realizacji* wskazuje, że klasa implementuje operacji i atrybuty oferowane przez interfejs.  

     Aby utworzyć te relacje, użyj **dziedziczenia** narzędzia. Alternatywnie realizacją może być reprezentowana jako *interfejs typu lizak*.  

-   *Pakiety* są grupami klasyfikatory, skojarzenia linii życia, składników i inne pakiety. *Importuj* relacje wskazać, że jeden pakiet zawiera wszystkie definicje inny pakiet.  

 Jako punktu wyjścia do eksplorowania i przedyskutować istniejące klasy projektanta klas służy do tworzenia diagramów klasy z kodu.  

-   [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  

#### <a name="summary-strengths-of-class-diagrams"></a>Podsumowanie: Sile diagramy klas  
 Diagramy klas w celu określenia:  

-   Wspólny Słownik terminów do użycia przy omawianiu potrzeb użytkowników i jednostek, które uczestniczą w systemie. Zobacz [modelu wymagania użytkownika](../modeling/model-user-requirements.md).  

-   Typy, które są używane przez części systemu, takich jak składniki, niezależnie od ich implementacji. Zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).  

-   Relacje, takich jak zależności między typami. Na przykład można pokazać, że jeden typ może być skojarzony z wielu wystąpień innego typu.  

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  

|**Diagram**|**Opis**|  
|-----------------|---------------------|  
|Diagram zależności|Zdefiniuj architektura logiczna systemu do klas.<br /><br /> Aby upewnić się, że kod jest zgodne z projektem, należy użyć walidacji zależności.<br /><br /> Zobacz:<br /><br /> -   [Tworzenie diagramów zależności w kodzie](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|  
|Mapy kodu|Wizualizuj organizacji i relacje w istniejącym kodzie.<br /><br /> Aby zidentyfikować klas, ich relacje i ich metod tworzenia mapy kodu, który pokazuje tych elementów.<br /><br /> Zobacz:<br /><br /> -   [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)|  

###  <a name="DescribeLayers"></a> Architektura logiczna opisują: diagramy zależności  
 Diagramy zależności opisano architekturę logicznych systemu przez organizowanie artefaktów w rozwiązaniu w abstrakcyjnej grup lub *warstwy*. Artefakty można wiele rzeczy, takich jak obszary nazw, projektów, klas, metod i tak dalej. Warstwy reprezentują i opisano role lub zadania, które wykonują artefaktów w systemie. Możesz również uwzględnić Walidacja warstw w kompilacji i zaewidencjonuj operacji upewnij się, że kod jest zgodny z jego projekt.  

 Aby zachować kod jest zgodne z projektem, teraz obiad i lucerny umożliwia na poniższym diagramie zależności sprawdzanie poprawności ich kodu jak ewoluują:  

 ![Diagram zależności system płatności zintegrowanego](../modeling/media/layer_integrated_dnlucerne.png "Layer_Integrated_DNLucerne")  

 **Diagram zależności obiad teraz zintegrowana z lucerny**  

 Warstw na tym diagramie, łącze do odpowiedniego artefaktów obiad teraz i lucerny rozwiązania. Na przykład, łącza warstwy biznesowej do przestrzeni nazw DinnerNow.Business i jej elementów członkowskich, które zawierają teraz klasy PaymentApprover. Dostęp do zasobów warstwy łącza do DinnerNow.Data przestrzeni nazw. Strzałki, lub *zależności*, określ warstwie Business można użyć funkcji warstwy dostępu do zasobów. Jak zespołów aktualizacji swój kod, warstwy weryfikacji regularnie catch konfliktów w miarę ich występowania, a także pomagające zespoły niezwłocznie ich rozwiązywania.  

 Zespoły współdziałają ze sobą przyrostowo integrować i dwa systemy testowe. One najpierw upewnij się, że PaymentApprover i pozostałe obecnie obiad pracy ze sobą pomyślnie zanim mają do czynienia PaymentProcessing.  

 Następujące Mapa kodu pokazuje nowe wywołania między obiad teraz i PaymentApprover:  

 ![Wykres zależności zaktualizowane za pomocą zintegrowanego systemu](../modeling/media/depgraph_intsystem.png "DepGraph_IntSystem")  

 **Mapa kodu z wywołań metody zaktualizowane**  

 Po ich upewnić się, że system działa zgodnie z oczekiwaniami, teraz obiad komentarzy kodu PaymentProcessing. Raporty weryfikacji warstwy są czystego, a wynikowy Mapa kodu pokazuje, czy istnieją ma więcej PaymentProcessing zależności:  

 ![Wykres zależności bez PaymentProcessing](../modeling/media/depgraph_nomore.png "DepGraph_NoMore")  

 **Mapy kodu bez PaymentProcessing**  

#### <a name="drawing-a-dependency-diagram"></a>Rysowanie Diagram zależności  
 Diagram zależności zawiera następujące główne funkcje:  

-   *Warstwy* opisano grupy logiczne artefaktów.  

-   A *łącze* jest skojarzenie między warstwami artefaktu.  

     Aby utworzyć warstwy z artefaktów, przeciągnij elementy z Eksploratora rozwiązań, mapy kodu, Widok klas lub przeglądarki obiektów. Rysuj nowe warstwy, a następnie połączenie ich do artefaktów, Użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu do utworzenia warstwy, a następnie przeciągnij elementy do nich.  

     Numer na warstwie pokazuje liczbę artefaktów, które są połączone z warstwy. Tych artefaktów może być przestrzeni nazw, projektów, klas, metod i tak dalej. Podczas interpretacji liczbę artefaktów na warstwie, należy pamiętać o następujące czynności:  

    -   Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.  

         Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.  

    -   Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.  

     Aby wyświetlić artefaktów, które są połączone z warstwy, kliknij prawym przyciskiem myszy zależności, a następnie kliknij **Wyświetl łącza** otworzyć **Explorer warstwy**.  

-   A *zależności* wskazuje jednej warstwie może używać funkcji w innej warstwie, ale nie odwrotnie. A *zależności dwukierunkowego* wskazuje jednej warstwie może używać funkcji w innej warstwie i na odwrót.  

     Aby wyświetlić istniejące zależności na diagramie zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij przycisk **Generowanie zależności**. Do opisania zamierzone zależności, Rysuj nowe.  

 Zobacz:  

-   [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)  

-   [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)  

-   [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)  

-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)  

#### <a name="summary-strengths-of-dependency-diagrams"></a>Podsumowanie: Sile diagramy zależności  
 Diagramy zależności ułatwiają:  

-   Opisz architektura logiczna systemu zgodnie z funkcji jego artefakty.  

-   Upewnij się, że kod opracowywane odpowiada określonego projektu.  

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami  

|**Diagram**|**Opis**|  
|-----------------|---------------------|  
|Mapy kodu|Wizualizuj organizacji i relacje w istniejącym kodzie.<br /><br /> Aby utworzyć warstwy, Generuj mapę kodu, a następnie grupować elementy na mapie jako potencjalne warstwy. Przeciągnij grup z mapy do diagramu zależności.<br /><br /> Zobacz:<br /><br /> -   [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Przeglądanie i rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)|  

## <a name="external-resources"></a>Zasoby zewnętrzne  

|**Kategoria**|**Łącza**|  
|------------------|---------------|  
|**Fora**|-   [Visual Studio wizualizacji & Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio wizualizacji & modelowania SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  

## <a name="see-also"></a>Zobacz także

[Tworzenie wizualizacji kodu](../modeling/visualize-code.md)   
[Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)   
[Używanie modeli w elastyczne programowanie](http://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)   
[Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)
