---
title: "Opracowywanie testów na podstawie modelu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- tests and requirements
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a2937edee2040d8e48938b9cbbf8e78e48780884
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="develop-tests-from-a-model"></a>Opracowywanie testów na podstawie modelu
Aby ułatwić organizowanie testów systemu i jej elementów można użyć wymagań i architektury modeli. Takie rozwiązanie pomaga, sprawdź, czy test wymagań, które są ważne dla użytkowników oraz innych zainteresowanych osób i ułatwia szybkie aktualizowanie testów zmiany wymagań. Jeśli używasz [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], można również Obsługa łącza między modelami i testy.  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują tych funkcji, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="system-and-subsystem-testing"></a>System i testowania podsystemu  
 *Testowanie systemowe,* znanej także jako *testów akceptacyjnych*, środków sprawdzenie, czy spełnione są wymagania użytkowników. Testy te niepokoi się widoczne na zewnątrz zachowanie systemu zamiast wewnętrzny projektu.  
  
 Testów systemowych są bardzo przydatne, gdy rozszerzanie lub zmianę projektu systemu. Pomagają uniknąć wprowadzenia usterki po zmianie kodu.  
  
 Planując wszelkie zmiany lub rozszerzenie do systemu, warto uruchomić zestaw testów systemowych, które są uruchamiane w istniejącym systemie. Następnie można rozszerzyć lub Dostosuj testów do testowania nowych wymagań, wprowadzić zmiany w kodzie i ponownie uruchom pełny zestaw testów.  
  
 Podczas opracowywania nowego systemu można rozpocząć tworzenie testów, jak rozpoczyna się programowanie. Definiując testy przed opracowanie każdej funkcji, można przechwycić dyskusji wymagania w bardzo określony sposób.  
  
 Testowanie podsystemu dotyczą te same zasady głównych składników systemu. Każdy składnik jest testowane oddzielnie od innych składników. Podsystem testy fokus na zachowanie widoczne na interfejsy użytkownika składnika lub interfejsu API.  
  
## <a name="deriving-system-tests-from-a-requirements-model"></a>Wyprowadzanie z modelu wymagania testów systemowych  
 Można utworzyć i zarządzać relację między testów systemowych i wymagań dotyczących modelu. Aby ustalić tę relację, zapisywania testy, które odpowiadają główne elementy modelu wymagania. Visual Studio ułatwiają zarządzanie relacji przez umożliwienie tworzenia łącza między testów i części modelu. Aby uzyskać więcej informacji o modelach wymagania, zobacz [modelu wymagania użytkownika](../modeling/model-user-requirements.md).  
  
### <a name="write-tests-for-each-use-case"></a>Pisanie testów dla każdego przypadku użycia  
 Jeśli używasz [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], można utworzyć grupę testów dla każdego przypadku użycia, zdefiniowanego w modelu wymagania. Na przykład jeśli przypadek użycia kolejności zawierają najważniejsze nowości, w tym tworzenie zlecenia i Dodaj element do zlecenia, można utworzyć testów dla obu ogólnych i bardziej szczegółowe te przypadki użycia. 
  
 Wskazówki te mogą być pomocne:  
  
-   Każdego przypadku użycia powinna mieć wiele testów dla głównych ścieżek i wyjątkowe wyniki.  
  
-   Opisywane przypadek użycia w modelu wymagania jest ważniejsze do definiowania jego warunku końcowego, oznacza to, że cel zostanie osiągnięty, niż opisujący szczegółowo procedury użytkownik wykonuje, aby osiągnąć cel. Na przykład może być warunku końcowego zlecenia zawierają najważniejsze nowości który restauracji przygotowuje zawierają najważniejsze Nowości dla danego klienta, a klient ma płatnej. Warunku końcowego jest kryterium, które testy należy sprawdzić.  
  
-   Podstawowy oddzielne testy na oddzielnych klauzulami warunku końcowego. Na przykład utworzyć osobne testy powiadamiania restauracji kolejność i do wykonywania płatności od klienta. Ta separacja ma następujące zalety:  
  
    -   Zmiany w różnych aspektów wymagania często występują niezależnie. Dzieląc testy na różne aspekty w ten sposób, można ułatwić aktualizowania testy w przypadku zmiany wymagań.  
  
    -   Jeśli plan rozwoju implementuje jednym aspekcie przed inny przypadek użycia, możesz je włączyć testy oddzielnie w trakcie rozwoju.  
  
-   Podczas projektowania testy należy oddzielić wybór dane testowe od kod lub skrypt, który określa, czy osiągnięte zostały warunku końcowego. Na przykład może być testu prostych funkcji arytmetyczne: dane wejściowe 4; Sprawdź, czy dane wyjściowe 2. Zamiast tego należy projektować skryptu jako: Wybierz wejściem; mnożenia danych wyjściowych przez samego siebie i sprawdź, czy wynik jest oryginalne dane wejściowe. Ten styl umożliwia różnią się dane wejściowe testu bez zmieniania główną testu.  
  
#### <a name="linking-tests-to-use-cases"></a>Łączenie testów do przypadki użycia  
 Jeśli używasz [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] do projektowania i uruchamiania testów, możesz organizować testów w obszarze wymaganie, przypadków użycia lub elementów pracy scenariusza użytkownika. Te można łączyć elementów roboczych, aby użyć przypadków w modelu. Dzięki temu można szybko śledzenia zmiany w testach i pomaga śledzić postęp każdego przypadku użycia.  
  
###### <a name="to-link-tests-to-a-use-case"></a>Aby połączyć testy z przypadkiem użycia  
  
1.  W [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], należy utworzyć wymaganie i podstawą zestawu testów.
  
     Wymaganie, tworzona jest elementu roboczego w [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Może być elementem pracy scenariusza użytkownika, wymagań lub przypadek użycia, w zależności od szablonu procesu, który projekt korzysta z [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Aby uzyskać więcej informacji, zobacz [śledzenie pracy za pomocą programu Visual Studio Team Services lub program Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Element roboczy wymaganie należy połączyć jednego lub więcej przypadków użycia w modelu.  
  
     W diagram przypadku użycia, kliknij prawym przyciskiem myszy przypadek użycia, a następnie kliknij przycisk **łącze do elementu roboczego**. 
  
3.  Dodaj do zestawu testów, przypadków testowych, które pozwalają sprawdzić przypadki użycia.  
  
 Zwykle każdy element roboczy użytkownika, jak wątku lub wymaganie połączy się z kilku przypadków użycia w modelu i każdego przypadku użycia połączy się z kilku przypadków użycia lub wymagań. Jest to spowodowane każdego scenariusza użytkownika lub wymaganie obejmuje zestaw zadań, które opracowanie kilka przypadków użycia. Na przykład w iteracji wczesne projektu mogą opracowywać scenariusza użytkownika podstawowego, w którym klient można wybrać elementy z wykazu i je dostarczyć. W późniejszym iteracji wątku może być, czy użytkownik płaci po zakończeniu kolejność i dostawca otrzymuje pieniądze po wysłaniu towarów.  Każdy wątek doda klauzulę do warunku końcowego w przypadku użycia towarów kolejności.  
  
 Można utworzyć oddzielne łącza z wymagań dla klauzul warunku końcowego pisząc tych klauzul w oddzielnych komentarze na diagram przypadku użycia. Łączenie każdego komentarza do elementu roboczego wymaganie i połącz komentarz z przypadek użycia na diagramie.  
  
### <a name="base-tests-on-the-requirements-types"></a>Podstawowe testy na typy wymagań  
 Typy, które jest klasy, interfejsy i wyliczenia modelu wymagania opisano pojęcia i relacje pod względem sposobu użytkowników wziąć pod uwagę i komunikacji dotyczących firmy. Nie obejmuje on typów danych tylko z wewnętrznego projektowania systemu.  
  
 Projektowanie testów pod względem typów te wymagania. Pomaga to upewnij się, że w przypadku zmiany wymagań dotyczących omówiono, jest prosty do dotyczą zmiany niezbędne zmiany w testach. Powoduje możliwość omówienia testy i ich zamierzone wyniki bezpośrednio z użytkownicy końcowi i inni uczestnicy projektu. To oznacza, że użytkowników wymaga można zarządzać poza procesem rozwoju i pozwala uniknąć przypadkowej projektowania testów wokół możliwych błędów w projekcie.  
  
 Dla testów ręcznych takie rozwiązanie wymaga przestrzegać słownictwa wymagania modelu w skryptach testu. Dla testów automatycznych takie rozwiązanie polega na przy użyciu diagramów klas wymagania jako podstawa dla kodu testowego i tworzenia metody dostępu i updater funkcje połączyć wymaganie modelu kodu.  
  
 Na przykład wymagania, które mogą obejmować modelu typy Menu, element Menu kolejności i skojarzenia między nimi. Ten model reprezentuje informacje są przechowywane i zajmują zawierają najważniejsze nowości porządkowanie systemu, ale nie reprezentuje złożoności jego wykonania. W systemie pracy może być kilka różnych realizations każdego typu, w przypadku baz danych w interfejsów użytkownika i interfejsów API. W rozproszonym systemie może być kilka wariantów każde wystąpienie przechowywane w innej części systemu w tym samym czasie.  
  
 Aby przetestować przypadek użycia, np. Dodaj element do zlecenia, metody testowej może zawierać kod podobny do poniższego:  
  
```  
Order order = ... ; // set up an order  
// Store prior state:  
int countBefore = order.MenuItems.Count;   
// Perform use case:  
MenuItem chosenItem = ...; // choose an item  
AddItemToOrder (chosenItem, order);   
// Verify part of postcondition:  
int countAfter = order.MenuItems.Count;  
Assert (countAfter == countBefore = 1);   
```  
  
 Należy zauważyć, że ta metoda korzysta z klas modelu wymagania. Skojarzenia i atrybuty, są realizowane jako właściwości platformy .NET.  
  
 Aby umożliwić użycie tych wartości, właściwości klasy musi być zdefiniowany jako tylko do odczytu funkcji lub metod dostępu, do których dostęp do systemu, aby pobrać informacje o bieżącym stanie. Przypadki użycia metod symulujących, takie jak AddItemToOrder musi dysków systemu za pośrednictwem jej interfejsu API lub warstwy poniżej interfejs użytkownika. Konstruktory obiektów testu kolejność i MenuItem musi również stacji systemu do utworzenia odpowiednich elementów w systemie.  
  
 Wiele metod dostępu i metod aktualizowania już będą dostępne za pośrednictwem interfejsu API normalne aplikacji. Ale niektóre dodatkowe funkcje mogą mieć do zapisania w celu umożliwienia testy. Te dodatkowe metody dostępu i metod aktualizowania są czasami znana jako "test Instrumentacji". Ponieważ są one zależne od wewnętrznego projektu systemu, jest zobowiązany deweloperzy systemu, aby zapewnić użytkownikom, podczas gdy testerów napisać kod testów pod względem modelu wymagania.  
  
 Podczas pisania testów automatycznych, można użyć podczas testów generycznych do opakowywania metody dostępu i metod aktualizowania.
  
### <a name="tests-for-business-rules"></a>Testy w przypadku reguł biznesowych  
 Niektóre wymagania nie są bezpośrednio związane z dowolnego przypadku użycia jednej. Na przykład umożliwia klientom wybierz z menu wiele firm DinnerNow, ale wymaga, aby w każdej kolejności, wszystkie wybrane elementy są od jednego Menu. Tę regułę biznesową może zostać wyrażona jako niezmiennej o skojarzenia zleceń, menu i elementów w modelu klasy wymagania.  
  
 Reguła niezmiennej tego rodzaju reguluje nie tylko wszystkich przypadków użycia, które są obecnie zdefiniowane, ale również wszystkie inne przypadki użycia są definiowane później. W związku z tym jest przydatne, zapisz je oddzielnie z dowolnego przypadku użycia i przetestować go niezależnie od przypadków użycia.  
  
## <a name="deriving-subsystem-tests-from-models"></a>Wyprowadzanie podsystemu testy z modeli  
 Wysokiego poziomu projektu systemu dużych w można zidentyfikować elementów lub podzespołów. Reprezentuje on elementy, które mogą być oddzielnie zaprojektowane, znajdują się na różnych komputerach lub moduły wielokrotnego użytku, które mogą być odtwarzane na wiele sposobów. 
  
 Można zastosować do poszczególnych głównych składników te same zasady jak używa do całego systemu. W dużych projektów każdego składnika może mieć własny model wymagania. W mniejszych projektów architektury modelu lub struktury wysokiego poziomu można tworzyć pokazanie główne składniki i ich interakcje. Aby uzyskać więcej informacji, zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).  
  
 W obu przypadkach można ustanowić relacji między elementami modelu, jak i testy podsystemu w taki sam sposób jak w przypadku między modelu wymagań i testów systemowych.  
  
### <a name="isolate-components-with-provided-and-required-interfaces"></a>Izolowanie składniki z interfejsami podana i jest wymagana  
 Zaleca się, aby zidentyfikować wszystkie zależności, które ma składnik na inne części z systemu lub usług zewnętrznych, a do reprezentowania je jako wymaganych interfejsów. Tego ćwiczenia zwykle prowadzi do niektórych zmianom, pozostawiając składnika bardziej rozdzielonymi i łatwo rozdzielić od pozostałej części projektu.  
  
 Zaletą to oddzielenie jest, że składnik mogą być wykonywane do testowania przez zamianę zasymulować obiektów usługi, które są zazwyczaj używane. Są to składniki, które są skonfigurowane na potrzeby testowania. Składnik zasymulować udostępnia interfejs, który wymaga składnika odpowiada na zapytania z danymi symulowane. Składniki zasymulować częścią przewodów ukończenia testowej, czy możesz połączyć ze wszystkimi interfejsami składnika.  
  
 Korzyści z testowania zasymulować jest opracowanie składnika podczas inne składniki, których będzie używać usługi są nadal w fazie tworzenia.  
  
## <a name="maintain-the-relationships-between-tests-and-model"></a>Obsługa relacje między testów i modelu  
 W typowych projektu, który wykonuje iterację co kilka tygodni Przejrzyj wymagania odbywa się na początku każdej iteracji. Spotkanie w tym artykule omówiono funkcje, które mają zostać dostarczone w następnej iteracji. Wymagania modelu może służyć do pomocy omówiono pojęcia, scenariusze i sekwencje działań, które zostaną rozwinięte. Uczestników firm Ustawianie priorytetów, deweloperzy tworzą szacuje i testerów upewnij się, że oczekiwane zachowanie każdej funkcji jest przechwytywany poprawnie.  
  
 Pisanie testów jest najbardziej efektywny sposób definiowania wymagania i jest również efektywnym sposobem zapewnienia, że osoba ma przejrzysty, co jest wymagane. Jednak należy pisania testów trwa zbyt długo podczas workshop specyfikacji, tworzenia modeli może odbywać się znacznie szybciej.  
  
 Z testowania punktu widzenia modelu wymagania są widoczne jako skróconą formą testy. Dlatego jest ważne zachować relację między testów i modelu w projekcie.  
  
##  <a name="Attaching"></a>Dołączanie przypadków testowych do modelowania elementów  
 Jeśli projekt używa [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], testy można połączyć elementy w modelu. Pozwala szybko znaleźć testów, który wpływa zmiana w wymaganiach i pomaga śledzić zakresu, do którego zostały zrealizowane wymagania.  
  
 Testy można połączyć wszelkiego rodzaju elementu. Oto kilka przykładów:  
  
-   Łączenie przypadków użycia w testach, które jego wykonywania.  
  
-   Zapis klauzule warunku końcowego przypadków użycia lub celem na komentarze, które są połączone z przypadek użycia, a następnie połącz testy każdego komentarza.  
  
-   Niezmienna reguły są pisane w komentarzach diagramy klas lub diagramy aktywności i połącz je do testów.  
  
-   Testy łącze diagram działania lub poszczególnych działań.  
  
-   Zestaw testów połączyć składnik lub podsystemu, który go testów.  
  
#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Aby połączyć testy elementu modelu lub relacji  
  
1.  W [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], należy utworzyć wymaganie i podstawą zestawu testów. 
  
     Wymaganie, tworzona jest elementu roboczego w [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Może być elementem pracy scenariusza użytkownika, wymagań lub przypadek użycia, w zależności od szablonu procesu, który projekt korzysta z [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Aby uzyskać więcej informacji, zobacz [śledzenie pracy za pomocą programu Visual Studio Team Services lub program Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Połączyć elementu roboczego wymaganie co najmniej jeden element w modelu.  
  
     Na diagramie modelowania kliknij prawym przyciskiem myszy element, komentarza lub relacji, a następnie kliknij przycisk **łącze do elementu roboczego**.
  
3.  Dodaj do zestawu testów, przypadków testowych, które Sprawdź wymagania wyrażone w elementu modelu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)   
 [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)   
 [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)   
 [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)
