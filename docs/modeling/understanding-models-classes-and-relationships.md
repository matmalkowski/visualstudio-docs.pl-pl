---
title: Opis modeli, klasy i relacje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a3ee963ef1ac4c4159f0fe1922bfafa90875fad7
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="understanding-models-classes-and-relationships"></a>Opis modeli, klas i relacji
Język specyficznego dla domeny (DSL) jest zdefiniowany przez jego plik definicji DSL, wraz z dowolny kod niestandardowy program, który może zapisać. Większość kodu programu w rozwiązaniu DSL są generowane na podstawie tego pliku.  
  
 W tym temacie omówiono funkcje centralnej definicji DSL.  
  
## <a name="the-dsl-definition"></a>Definicja DSL  
 Po otwarciu `Dsl\DslDefinition.dsl`, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okna podobny poniższej ilustracji.  
  
 ![Projektant DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 Najważniejsze informacje w definicji DSL jest wyświetlane na diagramie definicji DSL. Dodatkowe informacje, które jest również częścią DslDefinition.dsl, jest wyświetlana w Eksploratorze DSL, który zazwyczaj znajduje się na stronie diagramu. Możesz pracować z diagramem najczęściej wykonywanych zadań i Explorer DSL bardziej zaawansowane dostosowania.  
  
 Diagram definicji DSL przedstawia klasy domeny, które definiują elementy modelu i relacje definiujące łącza między elementami modelu. Przedstawiono również kształty i łączniki, które są używane do wyświetlania elementów modelu dla użytkownika.  
  
 ![Projektant DSL z tor](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 Po wybraniu elementu w definicji DSL, na diagramie lub w Eksploratorze DSL, informacje o tym są wyświetlane w oknie właściwości. Dodatkowe informacje mogą być wyświetlane w okienku szczegółów DSL.  
  
### <a name="models-are-instances-of-dsls"></a>Modele są wystąpieniami klasy DSLs  
 A *modelu* jest wystąpieniem programu DSL utworzone przez użytkownika. Model zawiera elementy modelu, które są wystąpieniami klasy domeny, które należy zdefiniować i łącza między elementami, które są wystąpieniami klasy relacje domeny, które zostały zdefiniowane. Model może być również kształtów i łączników, które są wyświetlane na diagramie elementy modelu i łącza. Definicja DSL zawiera klasy kształtu, łącznik klas i klasa diagramu.  
  
 Definicja DSL jest także znana jako *modelu domeny*. Modelu DSL definicji lub domeny jest reprezentacja czasu projektowania języka specyficznego dla domeny modelu jest utworzenie wystąpienia środowiska wykonawczego języka specyficznego dla domeny.  
  
## <a name="domain-classes-define-model-elements"></a>Klasy domeny definiują elementy modelu  
 Klasy domeny są używane do tworzenia poszczególnych elementów w domenie i relacje domeny są łącza między elementami. Są one reprezentacja czasu projektowania elementów i linki, które zostaną utworzone przez użytkowników języka specyficznego dla projektu, podczas tworzenia ich modeli.  
  
 Na ilustracji przedstawiono model, który został utworzony przez użytkownika bibliotece utworów muzycznych DSL. Albumów muzycznych są reprezentowane przez pola, które zawierają listy utworów. Artystów są reprezentowane przez zaokrąglonych pola i są podłączone do albumów, na które przyczyniły się.  
  
 ![Wystąpienie modelu DSL wygenerowanego](../modeling/media/music_instance.png "Music_Instance")  
  
 Definicja DSL oddziela dwa aspekty. Wygląd elementów modelu diagramu modelu jest definiowana za pomocą klasy kształt i klasy łącznika. Informacje w modelu jest zdefiniowana za pomocą klasy i relacje domeny.  
  
 Na poniższej ilustracji przedstawiono klasy i relacje w bibliotece utworów muzycznych definicji DSL.  
  
 ![Dokumentacja i osadzanie relacje](../modeling/media/music_classes.png "Music_Classes")  
  
 Na ilustracji przedstawiono cztery klasy domeny: Muzyka, albumy, wykonawcy i utworu. Klasy domeny definiują właściwości domeny, takie jak nazwa, tytuł i tak dalej. W modelu wystąpienia wartości niektóre z tych właściwości są wyświetlane na diagramie.  
  
 Między klasami są relacje domeny: MusicHasAlbums, MusicHasArtists AlbumbHasSongs i ArtistAppearedOnAlbums. Relacje zostały liczebnościami powodującymi, takich jak 1..1, 0.. *. Na przykład musi być powiązany co utworu dokładnie jeden Album za pośrednictwem relacji AlbumHasSongs. Każdego albumu może mieć dowolną liczbę utworów.  
  
### <a name="rearranging-the-dsl-definition-diagram"></a>Zmienianie rozmieszczenia Diagram definicji DSL  
 Należy zauważyć, że klasą domeny może się pojawić kilka razy na diagramie definicji DSL jak Album na tym rysunku. Zawsze jest jeden widok główny i może być niektóre *odwołania* widoków.  
  
 Aby zmienić kolejność na diagramie definicji DSL, można:  
  
-   Zamiana głównego i odwoływania widoków przy użyciu **Przełącz drzewa tutaj** i **podziału drzewa** poleceń. Kliknij prawym przyciskiem myszy klasy pojedynczej domeny, aby wyświetlić te polecenia.  
  
-   Zmień kolejność klasy domeny i klasy kształtu, naciskając klawisze Ctrl + Strzałka w górę i Ctrl + Strzałka w dół.  
  
-   Zwiń lub rozszerzyć klasy przy użyciu ikony w prawym górnym rogu każdej kształtu.  
  
-   Zwiń części drzewa, klikając znak minus (-) u dołu klasą domeny.  
  
## <a name="inheritance"></a>Dziedziczenie  
 Można zdefiniować klasy domeny przy użyciu dziedziczenia. Aby utworzyć pochodnym dziedziczenia, kliknij narzędzie dziedziczenia, kliknij klasy pochodnej, a następnie kliknij klasy podstawowej. Element modelu ma wszystkie właściwości, które są zdefiniowane w klasie własnej domeny, wraz z właściwościami dziedziczona z klasy podstawowej. Dziedziczy jego role w relacji.  
  
 Można także dziedziczenia między relacje, kształty i łączniki. Dziedziczenie musi przechowywać w tej samej grupie. Kształt nie może dziedziczyć po klasie domeny.  
  
## <a name="domain-relationships"></a>Relacje domeny  
 Elementy modelu można połączyć relacjami. Łącza są zawsze binary; połączone dokładnie dwa elementy. Jednak każdy element może mieć wiele łączy do innych obiektów, a może nawet istnieć więcej niż jednego łącza między tej samej pary elementów.  
  
 Tak samo, jak można określić różnych klas elementów, można określić różnych klas łącza. Klasa łącza jest nazywana *relacji domeny*. Relacji domeny określa, jakie klasy elementu mogą łączyć z jego wystąpienia. Nosi nazwę każdego końca relacji *roli*, a relacja domeny definiuje nazwy dla dwóch ról, a także dla samego relacji.  
  
 Istnieją dwa rodzaje relacje domeny: osadzanie relacje i relacji odwołania. Na diagramie definicji DSL osadzania relacje w każdej roli jest linia ciągła, a relacji odwołania zostały oznaczone kreskowaną wierszy.  
  
### <a name="embedding-relationships"></a>Osadzanie relacji  
 Każdy element w modelu, z wyjątkiem elementem głównym jest elementem docelowym jedno łącze osadzania. W związku z tym całego modelu stanowi jedno drzewo osadzenia łącza. Relacja osadzania reprezentuje zawierania lub własność. Dwa elementy modelu, które są powiązane w ten sposób są także nazywane nadrzędnych i podrzędnych. Obiekt podrzędny, jest określany osadzone w obiekcie nadrzędnym.  
  
 Osadzanie łącza nie są zwykle wyświetlane jawnie łączników na diagramie. Zwykle są one jednak reprezentowane przez zawierania. Katalogu głównego modelu jest reprezentowana przez diagramu, a elementy osadzone w nim są wyświetlane jako kształtów na diagramie.  
  
 W tym przykładzie klasy głównym utworów muzycznych ma relacja osadzania MusicHasAlbums do albumów, którego osadzania AlbumHasSongs do utworu. Utworów są wyświetlane jako elementy na liście wewnątrz każdego albumu. Muzyka ma również osadzania MusicHasArtists do klasy wykonawcy, których wystąpienia są również wyświetlane jako kształtów na diagramie.  
  
 Domyślnie osadzone elementy są automatycznie usuwane podczas ich elementów nadrzędnych.  
  
 Jeśli model jest zapisywany do pliku w postaci XML, osadzone elementy są zagnieżdżone wewnątrz ich elementów nadrzędnych, chyba że dostosowano serializacji.  
  
> [!NOTE]
>  Osadzanie nie jest taka sama jak dziedziczenia. Elementy podrzędne w relacja osadzania dziedziczy właściwości elementu nadrzędnego. Osadzanie jest to typ łącza między elementami modelu. Dziedziczenie jest relacja między klasami i nie powoduje utworzenia łącza między elementami modelu.  
  
### <a name="embedding-rules"></a>Osadzanie reguły  
 Wartość każdego elementu w modelu wystąpienie musi być elementem docelowym dokładnie jedno łącze osadzania, z wyjątkiem katalogu głównego modelu.  
  
 Oznacza to co Klasa nieabstrakcyjna domeny, z wyjątkiem klasy głównym musi być elementem docelowym co najmniej jedna relacja osadzania i musi dziedziczyć z osadzanie z klasy podstawowej. Klasa może być celem osadzeń dwóch lub więcej, ale jego wystąpienia modelu elementów naraz może mieć tylko jednego zdarzenia nadrzędnego. Liczebność z docelowym źródłem musi być od 0 do 1 lub 1.. 1.  
  
### <a name="the-explorer-displays-the-embedding-tree"></a>Explorer wyświetla osadzania drzewa  
 Definicja DSL tworzy również Eksploratora, które użytkownicy widzą obok ich diagramu modelu.  
  
 ![Eksploratorze generowane DSL](../modeling/media/music_explorer.png "Music_Explorer")  
  
 Eksplorator zawiera wszystkie elementy w modelu, nawet te, dla których nie zdefiniowano kształtów. Zawiera elementy i osadzania relacji, ale odwołuje się do relacji.  
  
 Aby wyświetlić wartości właściwości domeny elementu, użytkownik wybiera element diagramu modelu lub w Eksploratorze modelu i powoduje otwarcie okna właściwości. Wyświetla wszystkie właściwości domeny, łącznie z tymi, które nie są wyświetlane na diagramie. W tym przykładzie każdy utworu zarówno tytuł i określonego rodzaju, ale tylko wartość tytułu jest wyświetlany na diagramie.  
  
## <a name="reference-relationships"></a>Relacje odwołania  
 Relacja odwołania reprezentuje dowolny rodzaj relacji, która nie jest osadzanie.  
  
 Relacje odwołania zazwyczaj są wyświetlane jako łączniki kształtów na diagramie.  
  
 W modelu reprezentację XML łącza między dwoma elementami jest reprezentowana za pomocą *monikerów.* Oznacza to monikerów są nazwami, które jednoznacznie identyfikują każdego elementu w modelu. Węzeł XML dla każdego elementu modelu zawiera węzeł, który określa nazwę relacji i monikera innego elementu.  
  
## <a name="roles"></a>Role  
 Każdy relacji domeny ma dwie role, rola źródła i rola Serwer obiektów docelowych.  
  
 Na poniższej ilustracji, liniach między **wydawcy** klasy domeny i **PublisherCatalog** relacji domeny jest roli źródłowej. Wiersz między relacji domeny i **albumu** klasy domeny jest rola Serwer obiektów docelowych.  
  
 ![Role i właściwości. ] (../modeling/media/propertycode.png "PropertyCode")  
  
 Nazw skojarzonych z relacji są szczególnie istotne podczas pisania kodu programu, który przechodzi przez model. Na przykład podczas kompilowania rozwiązania DSL wygenerowana klasa wydawcy ma właściwość katalogu, który jest kolekcją albumów. Klasa albumu ma właściwość wydawcy, który jest pojedynczym wystąpieniem klasy wydawcy.  
  
 Po utworzeniu relacji w definicji DSL nazwy właściwości i relacji są podane wartości domyślne. Jednak można je zmienić.  
  
## <a name="multiplicities"></a>Liczebność punktów  
 Liczebność punktów Określ, ile elementów może mieć tego samego elementu role w relacji domeny. W przykładzie zero do wielu (0..\*) liczebność ustawienie na **katalogu** roli Określa, że wszystkie wystąpienia **wydawcy** klasa domeny może mieć tyle  **PublisherCatalog** relacji łączy, które chcesz nadać mu.  
  
 Skonfiguruj Liczebność roli, wpisując na diagramie lub modyfikując `Multiplicity` właściwości w **właściwości** okna. W poniższej tabeli opisano ustawienia dla tej właściwości.  
  
|Liczebność typu|Opis|  
|-----------------------|-----------------|  
|0.. * (zero do wielu)|Każde wystąpienie klasy domeny może mieć wiele wystąpień relacji lub żadnych wystąpień relacji.|  
|Od 0 do 1 (zero do jeden)|Każde wystąpienie klasy domeny może mieć nie więcej niż jedno wystąpienie relacji lub żadnych wystąpień relacji.|  
|1..1 (jeden)|Każde wystąpienie klasy domeny może mieć jedno wystąpienie relacji. Nie można utworzyć więcej niż jedno wystąpienie tej relacji w każdym wystąpieniu klasy roli. Jeśli włączono weryfikację błąd sprawdzania poprawności będą wyświetlane, gdy wszystkie wystąpienia klasy roli ma żadne wystąpienie relacji.|  
|1.. * (jeden do wielu)|Każde wystąpienie klasy na roli, która ma liczebność to może mieć wiele wystąpień relacji, a każde wystąpienie musi mieć co najmniej jedno wystąpienie relacji. Jeśli włączono weryfikację błąd sprawdzania poprawności będą wyświetlane, gdy wszystkie wystąpienia klasy roli ma żadne wystąpienie relacji.|  
  
## <a name="domain-relationships-as-classes"></a>Relacje domeny jako klasy  
 Łącze jest reprezentowana w magazynie jako wystąpienie LinkElement, czyli w klasie pochodnej ModelElement. Te właściwości można zdefiniować diagramu modelu domeny na relacje domeny.  
  
 Należy również wybrać relacji źródłową lub docelową relacje. Na diagramie modelu domeny, kliknij prawym przyciskiem myszy relacji domeny, a następnie kliknij przycisk **Pokaż jako klasa**. Zostanie wyświetlone okno dodatkowe klasy. Relacje można połączyć do niego.  
  
 Można zdefiniować relację częściowo poprzez dziedziczenie, podobnie jak w przypadku klas domeny. Wybierz relację pochodnej i ustaw **relacji podstawowej** w oknie właściwości.  
  
 Pochodne relacji specjalizuje się jego relacji podstawowych. Domena klas ten, który łączy powinien pochodzić z lub taka sama jak klasy, połączone relacji podstawowych. Gdy tworzone jest połączenie pochodny relacji w modelu, jest wystąpieniem pochodnej i relacji podstawowych. W kodzie programu można przejść do przeciwnego końca łącza, za pomocą właściwości generowane przez podstawowym lub klasy pochodnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
