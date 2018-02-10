---
title: "Używanie modeli w procesie tworzenia aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-modeling
ms.topic: get-started-article
helpviewer_keywords:
- UML, using models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7b5ce42d3856a4caf73413bf49894a78502e55e2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="use-models-in-your-development-process"></a>Używanie modeli w procesie tworzenia aplikacji
W programie Visual Studio można użyć modelu ułatwią zrozumienie i zmień systemu, aplikacji lub składnika. Model może pomóc w wizualizacji świecie, w którym działa system, wyjaśnienia potrzeb użytkowników, zdefiniuj architekturze systemu, analizy kodu i upewnij się, że kod użytkownika spełnia wymagania. Zobacz [Channel 9 wideo: poprawy architektury za pomocą modelowania](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 Aby sprawdzić, które wersje programu Visual Studio obsługi każdego typu modelu, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="how-to-use-models"></a>Jak używać modeli  
 Modele ułatwiają na kilka sposobów:  
  
-   Modelowanie diagramów rysunku pomaga wyjaśnienie pojęcia związane z wymaganiami, architektury i projektu wysokiego poziomu. Aby uzyskać więcej informacji, zobacz [modelu wymagania użytkownika](../modeling/model-user-requirements.md).  
  
-   Praca z modelami ułatwia ujawnia niespójności w wymaganiach.  
  
-   Podczas komunikacji z modelami pomaga komunikować się z ważnymi pojęciami poniżej ambiguously z języka naturalnego. Aby uzyskać więcej informacji, zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).  
  
-   Modele niekiedy mogą być używane do generowania kodu lub innych artefaktów, takich jak schematów bazy danych lub dokumentów. Na przykład modelowania składniki [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] zostaną wygenerowane na podstawie modelu.  Aby uzyskać więcej informacji, zobacz [Generowanie i konfigurowanie aplikacji na podstawie modeli](../modeling/generate-and-configure-your-app-from-models.md).  
  
 Możesz użyć modeli w wielu różnych procesów z bardzo elastyczne wysoki procedury.  
  
### <a name="use-models-to-reduce-ambiguity"></a>Umożliwia ograniczenie niejednoznaczności modeli  
 Język modelowania jest niejednoznaczny mniej niż języka naturalnego i jest przeznaczony do express pomysły, zwykle wymagana podczas tworzenia oprogramowania.  
  
 Jeśli projekt zawiera niewielkich zespołów wskazówek elastyczne, umożliwia modeli pomóc w określeniu scenariuszy użytkownika. W dyskusjach ze specjalistami z klienta dotyczące ich potrzeb w zakresie Tworzenie modelu może generować pytania znacznie szybciej, a przez szerszych obszar produktu, niż pisanie kodu kolekcji lub prototypu.  
  
 Jeśli projekt jest duży i dołącza zespoły w różnych części świecie, można użyć modeli aby komunikować się wymagania i architektura bardziej efektywne niż jest to możliwe w postaci zwykłego tekstu.  
  
 W obu przypadkach powoduje tworzenie modelu prawie zawsze znaczny spadek niespójności i niejednoznaczności. Różnych uczestników często mają różne ustalenia świata biznesowych, w którym działa system i różnych deweloperów często ustalenia różne działania systemu. Przy użyciu modelu jako fokus dyskusji zazwyczaj udostępnia te różnice. Aby uzyskać więcej informacji o sposobie używania modelu, aby zmniejszyć niespójności, zobacz [modelu wymagania użytkownika](../modeling/model-user-requirements.md).  
  
### <a name="use-models-with-other-artifacts"></a>Używanie modeli z pozostałych artefaktów  
 Model nie jest samodzielnie specyfikacji wymagania lub architektury. Jest to narzędzie dla sposób wyrażania niektórych aspektów tych czynności, ale nie wszystkie pojęcia, które są wymagane podczas projektowania oprogramowania można wyrazić. Modele powinna być używana razem z innymi środkami komunikacji, takich jak strony programu OneNote lub akapitów, dokumentów Microsoft Office, elementy robocze w [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)], lub notatki na tablicy miejsca projektu. Z wyjątkiem ostatniego elementu typu obiektu może odnosić się do części elementów modelu.  
  
 Innych aspektów specyfikacji, które zwykle są używane razem z modeli są następujące. W zależności od skali i styl projektu można użyć kilku te aspekty lub nie używane na wszystkich:  
  
-   Komentarze klientów. Scenariusza użytkownika jest krótki opis omówione z użytkownikami i inni uczestnicy projektu aspektu zachowanie systemu, które zostaną dostarczone w jednym z iteracji projektu. Rozpoczyna typowego scenariusza "odbiorcy będą mogli..." Scenariusza użytkownika może powodować grupy przypadków użycia lub można określić rozszerzenia przypadków użycia, które zostały wcześniej opracowane. Definiowanie i rozszerzanie przypadki użycia podnosi poziom jaśniejszy scenariusza użytkownika.  
  
-   Żądania zmiany. Żądania zmiany w bardziej formalnych projektów jest bardzo podobny do scenariusza, w projekcie elastyczne. Elastyczne podejście co został opracowany w poprzedniej iteracji traktuje wszystkie wymagania jako zmiany.  
  
-   Użyj przypadków opisu. Przypadek użycia reprezentuje jeden sposób, w którym użytkownik wchodzi w interakcję z systemem na osiągnięcie określonego celu. Pełny opis zawiera cel, głównego i alternatywnych sekwencji zdarzeń i wyjątkowe wyników. Diagram przypadku użycia pomaga podsumować i zawierają omówienie przypadki użycia.  
  
-   Scenariusze. Scenariusz jest dość szczegółowy opis sekwencji zdarzeń przedstawiający sposób systemu, użytkowników i innych systemów współdziałać, aby podać wartość osobom zainteresowanym. Może upłynąć postaci slide show interfejsu użytkownika lub prototyp interfejsu użytkownika. Można go opisać przypadek użycia jednej lub sekwencję przypadki użycia.  
  
-   Słownik. Słownik wymagania dotyczące projektu w tym artykule opisano wyrazy, z których klienci omówienia świata. Modele interfejsu i wymagania dotyczące użytkownika też używać tych postanowień. Diagram klas może pomóc wyjaśnić relacje między większości tych warunków. Tworzenie diagramów i słownik nie tylko zmniejsza nieporozumień między użytkownikami i deweloperów, ale prawie zawsze przedstawia nieporozumień między różnych biznesowych.  
  
-   Reguły biznesowe. Wiele reguł biznesowych może zostać wyrażona jako niezmiennej ograniczenia dotyczące skojarzenia i atrybutów w modelu klasy wymagania i jako ograniczenia w diagramach sekwencji.  
  
-   Projekt wysokiego poziomu. Zawiera opis głównych składników i sposób ich dopasowania. Składnik, sekwencji i diagramy interfejsu są główna część ogólnymi procedurami projektowania.  
  
-   Wzorce projektowe. Opis reguły projektowania, które są współużytkowane przez różne części systemu.  
  
-   Przetestuj specyfikacji. Skrypty testu i projekty dla kodowanego testu potrafi wykorzystać diagramów działania i sekwencji do opisywania sekwencji kroków testu. Testy systemu muszą być wyrażone w modelu wymagania, aby łatwo mogą zostać zmienione w przypadku zmiany wymagań.  
  
-   Plan projektu. Plan projektu lub zaległości definiuje dostarczenia każdej funkcji. Można zdefiniować każdej funkcji Użyj co przypadków i reguł biznesowych implementuje lub rozszerza z informacją. Można albo odwołać się do przypadków użycia i reguły biznesowe bezpośrednio w planie lub w oddzielnych dokumentu zdefiniować zestaw funkcji i użyj funkcji tytuły w planie.  
  
### <a name="use-models-in-iteration-planning"></a>Używanie modeli w Planowanie iteracji  
 Mimo że wszystkie projekty różnią się w ich skali i organizacji, typowe projektu jest planowana jako serię iteracje od dwóch do sześciu tygodni. Należy zaplanować wystarczająco dużo iteracji, aby umożliwić opinii z wczesnym iteracji, aby można dostosować zakres i planów dla nowszej iteracji.  
  
 Poniższe sugestie mogą być przydatne w celu osiągnięcia korzyści modelowania w projekcie iteracji.  
  
#### <a name="sharpen-focus-as-each-iteration-approaches"></a>Wyostrzania fokus jako metod każdej iteracji  
 Jak zbliża się do każdej iteracji, użyj modeli z myślą o określeniu, jakie ma zostać dostarczona z końcem iteracji.  
  
-   Nie modelu wszystko szczegółowo w wczesne iteracji. W pierwszej iteracji Utwórz diagram klasy głównym elementów w słowniku użytkownika, rysowania diagramu przypadków użycia głównych i utworzyć diagram głównych składników. Nie opisują dowolną z tych dokładniej, ponieważ szczegóły zmieni później w projekcie. Umożliwia utworzenie listy funkcji lub głównych scenariuszy warunki zdefiniowane w tym modelu. Przypisz funkcje do iteracji, aby około zrównoważenia obciążenia szacowany w projekcie. Te przydziały zmieni się później w projekcie.  
  
-   Spróbuj Wdrażanie uproszczonej wersji wszystkich najważniejszych przypadków użycia w wczesne iteracji. Rozszerzenia te przypadki użycia w późniejszym iteracji. Takie podejście pozwala zmniejszyć ryzyko odnajdowania luka w wymaganiach lub architektury za późno w projekcie wykonywanie dodatkowych informacji na ten temat.  
  
-   Pod koniec każdej iteracji przytrzymaj workshop wymagania, aby zdefiniować szczegółowe wymagania lub scenariuszy użytkownika, które zostaną rozwinięte w następnej iteracji. Zaprosić użytkowników i uczestników biznesowe, które można określić priorytety, a także deweloperów i testerów systemu. Zezwalaj na trzy godziny zdefiniować wymagania dotyczące iteracji 2 tygodni.  
  
-   Celem workshop jest dla wszystkich użytkowników, będą musieli się zgodzić co można zrobić końca następnej iteracji. Użyj modeli jako jedno z narzędzi, aby wyjaśnić wymagania. Dane wyjściowe workshop jest zaległości iteracji: czyli listę programowanie zadania w programie [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] i pakiety w testowe [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)].  
  
-   W workshop wymagania omówiono w nim projektu pod warunkiem, że trzeba określić szacuje dla zadań związanych z projektowaniem. W przeciwnym razie Zachowaj dyskusji zachowanie systemu, które użytkownicy mogą występować bezpośrednio. Zachowaj wymagania modelu niezależnie od architektury modelu.  
  
-   Nietechnicznym uczestnicy projektu mają zwykle bez problemów opis diagramów UML wskazówek od użytkownika.  
  
#### <a name="link-model-to-work-items"></a>Model łącza do elementów roboczych  
 Po workshop wymagania rozwijanie szczegółów modelu wymagania i połącz zadań związanych z projektowaniem modelu. Można to zrobić przez łączenie z elementami pracy w [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] do elementów w modelu.
  
 Możesz połączyć dowolny element do elementów roboczych, ale najbardziej przydatne elementy są następujące:  
  
-   Komentarz opisujący reguł biznesowych lub jakości wymagania dotyczące usługi. Aby uzyskać więcej informacji, zobacz [modelu wymagania użytkownika](../modeling/model-user-requirements.md).  
  
#### <a name="link-model-to-tests"></a>Model łącze do testów  
 Wymagania modelu umożliwia przewodnik dotyczący projektowania testów akceptacji. Utwórz te testy równocześnie pracach programistycznych.  
  
 Aby dowiedzieć się więcej na temat tej metody, zobacz [opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md).  
  
#### <a name="estimate-remaining-work"></a>Oszacowania pracy pozostałej  
 Wymagania modelu może ułatwić oszacowanie całkowitego rozmiaru projektu w odniesieniu do rozmiaru każdej iteracji. Oceny liczba i złożoność przypadki użycia i klas mogą ułatwić oszacowanie projektach, które będzie wymagane. Po wykonaniu pierwszej iteracji kilka porównanie wymagań określonych i wymagania nadal tak, aby pokrywał można przekazać przybliżone miara kosztu i zakres pozostałej części projektu.  
  
 Pod koniec każdej iteracji Przejrzyj przypisania wymagań dotyczących przyszłych iteracji. Może być przydatne do reprezentowania stan oprogramowania na końcu każdej iteracji jako podsystemu w diagram przypadku użycia. W jego dyskusji można przenieść przypadki użycia i używanie rozszerzeń case z jednego z tych podsystemów do innego.  
  
## <a name="levels-of-abstraction"></a>Poziomy abstrakcji  
 Modele mają zakres abstrakcji w odniesieniu do oprogramowania. Najbardziej konkretnych modeli bezpośrednio reprezentuje kod programu i najbardziej abstrakcyjny modeli reprezentują koncepcje biznesowe, które mogą lub nie może być reprezentowany w kodzie.  
  
 Model można wyświetlić za pośrednictwem różnych typów schematów. Aby uzyskać informacje na temat modeli i diagramów, zobacz [tworzenia modeli dla aplikacji](../modeling/create-models-for-your-app.md).  
  
 Różne rodzaje diagram są przydatne do opisu projektu na różnych poziomach abstrakcji. Wiele typów diagram są przydatne w więcej niż jeden poziom. W poniższej tabeli zamieszczono użycia każdego typu diagramu.  
  
|Poziom projektu|Typy diagramów|  
|------------------|-------------------|  
|Proces biznesowy<br /><br /> Opis kontekst, w którym będzie używany system pomaga w zrozumieniu, użytkownicy muszą z niego.|— Diagramy klas koncepcyjnej opis pojęć biznesowych w ramach procesu biznesowego.|  
|Wymagania dotyczące użytkownika<br /><br /> Definicja użytkownicy potrzebują z systemu.|-Reguły biznesowe i jakość wymagania dotyczące usługi można przedstawić w oddzielnych dokumentów.|  
|Wysoki poziom projektu<br /><br /> Ogólna struktura systemu: główne składniki i sposób ich połączyć ze sobą.|— Diagramy zależności opisano struktury systemu na współzależne części. Można sprawdzić poprawność kodu programu przed diagramy zależności, aby upewnić się, że działa zgodnie z architektury.|  
|Kod — analiza<br /><br /> Diagramy może zostać wygenerowane przez kod.|-Zależności diagramach zależności między klasami. Zaktualizowany kod może zostać zweryfikowany względem diagram zależności.<br />— Diagramy klas Pokaż klas w kodzie.|  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
|**Kategoria**|**Łącza**|  
|------------------|---------------|  
|**Filmy wideo**|![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo") [MSDN jak wideo: sposobu tworzenia i użyj modeli i diagramów UML (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkId=214460)<br /><br /> ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: UML z programu Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=201106)<br /><br /> ![łącze do wideo](../data-tools/media/playvideo.gif "PlayVideo") [MSDN jak seria: UML narzędzi i rozszerzeń (Visual Studio 2010 Ultimate)](http://go.microsoft.com/fwlink/?LinkID=214467)|  
|**Fora**|-   [Visual Studio wizualizacji & Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio wizualizacji & modelowania SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogi**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Artykuły techniczne i arkuszy**|[Centrum architektura MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)<br /><br /> [Architektura Visual Studio — wskazówki dotyczące oprzyrządowania](../modeling/visual-studio-architecture-tooling-guidance.md)|  
  
## <a name="see-also"></a>Zobacz także

[Używanie modeli w elastyczne programowanie](http://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)   
[Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)   
[Wymagania modelu użytkownika](../modeling/model-user-requirements.md)   
[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)   
[Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)   
[Tworzenie struktury rozwiązania modelowania](../modeling/structure-your-modeling-solution.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
