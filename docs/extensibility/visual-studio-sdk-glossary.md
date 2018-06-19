---
title: Słownik zestawu SDK programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a08985c4977896e35fa8cd94014385ac32dd8bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148902"
---
# <a name="visual-studio-sdk-glossary"></a>Słownik zestawu SDK programu Visual Studio
Ten słownik zawiera definicje terminów, które są używane w [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] dokumentacji.  
  
## <a name="terms"></a>Warunki  
 Dodatek  
 Aplikacja narzędzia, sterowników lub innego oprogramowania dodanych do aplikacji głównej. W programie Visual Studio zintegrowane środowisko programistyczne (IDE) dodatek jest aplikacji na podstawie automatyzacji, która rozszerza możliwości środowiska IDE.  
  
 model automatyzacji  
 Model automatyzacji, znane w poprzednich wersjach programu Visual Studio jako modelu rozszerzalności jest interfejs programowania, który zapewnia dostęp do podstawowych procedury dysk IDE. Dodatki, kreatorów i makra użyć obiektów w modelu automatyzacji do kontroli lub rozszerzyć funkcjonalność programu IDE.  
  
 kontekst poleceń interfejsu użytkownika  
 Skojarzenie identyfikatora GUID z widoczność polecenia interfejsu użytkownika lub elementu, np. paska narzędzi. W odróżnieniu od kontekst zaznaczenia jest kontekst interfejsu użytkownika poleceń, że nie jest dołączony do okna.  
  
 Kontekst interfejsu użytkownika poleceń może służyć do:  
  
-   Przypisz identyfikatora GUID do paska narzędzi, który jest wyświetlany, gdy aktywowano poszczególnego okna.  
  
-   Przypisz identyfikator GUID dostępności polecenia bez konieczności obciążenia, lub uruchom pakiet VSPackage.  
  
-   Przypisz GUID wpływa na aktywne powiązania klucza.  
  
-   Przypisz identyfikator GUID, aby włączyć funkcję rejestrowania makr.  
  
-   Przypisz identyfikatora GUID, aby aktywować tryb debugowania lub aby przełączyć między projektowania i w trybie uruchamiania w edytorze.  
  
 składnik  
 Fragment oprogramowania, które można wprowadzić część funkcji aplikacji bez tej aplikacji o wszelkie istniejące informacje o implementacji oprogramowania. Komunikacja między składnikiem i aplikacji jest wyłącznie za pośrednictwem interfejsów styl OLE.  
  
 Menedżer składników  
 Usługa `SOleComponentManager`, który udostępnia interfejs użytkownika z systemem innym niż koordynacji usługi składników najwyższego poziomu. `SOleComponentManager` Usługa implementuje `IOleComponentManager` interfejsu.  
  
 Menedżer składników interfejsu użytkownika  
 Usługa `SOleComponentUIManager`, który udostępnia usługi koordynacji interfejsu użytkownika. `SOleComponentUIManager` Usługa implementuje `IOleComponentUIManager` i `IOleInPlaceComponentUIManager` interfejsów.  
  
 kontekst zbioru  
 `IVsUserContext` Object (obiekt COM) dołączona do składnika środowiska. Ten obiekt zawiera słowa kluczowe wyszukiwania, słów kluczowych F1 i atrybuty, które odnoszą się do składnika. Torebki kontekstu wskaż Ponadto wszelkie torebki kontekst podrzędny powiązanych z nimi.  
  
 Dostawca kontekstu  
 Składnik IDE, który ma zbiór kontekst skojarzony z nim. Takie składniki obejmują okna narzędzia, Edytor lub projekt hierarchii.  
  
 projektant  
 Interfejs programowania, który umożliwia użytkownikom modyfikowania elementów interfejsu użytkownika (formularze, przycisków i innych kontrolek).  
  
 Danych dokumentu  
 Obiekt COM, hermetyzując danych dokumentu w świecie przypadku separacji dokument/widok (na przykład w przypadku edytora tekstu, to buforu tekstu podstawowego we wszystkich widokach Edytor tekstu). Jeśli element EditorFactory nie dostarcza tego obiektu, IDE będzie produkcji, co w jej imieniu. Odpowiedzialność tego obiektu jest, aby zarządzać trwałości danych i semantykę udostępniania wielu widoków przez to samo `DocData`. Jeśli `DocData` obiekt obsługuje `IOleCommandTarget` interfejsu, zostanie uwzględniona w routing poleceń UIShell.  
  
 DocObject  
 Technologia używana do obsługi interfejsu użytkownika w ramce dostarczone przez hosta. W szczególności, określenie to odnosi się do żadnych osadzania, który obsługuje `IOleDocument` i interfejsy powiązane. Ta technologia ma wiele potencjalnych aplikacji, takich jak szczegóły implementacji COM dokumentów, okien narzędzi języka Visual Basic w wersji 5.0, projektantów ActiveX w Visual Basic 6.0 i tak dalej.  
  
 dokument  
 Ogólnie odnoszących się do całego dokumentu — zarówno `DocData` i `DocView`. Na przykład zawiera DocumentFrame `DocView`, zachowując jednak również odwołanie do `DocData` do obsługi trwałości.  
  
 Widok dokumentu  
 DocObject/Embedding/WindowPane, z którą użytkownik wchodzi w interakcję na wyświetlanie i manipulowanie odpowiadającego `DocData`. Należy pamiętać, że użytkownicy nie wykorzystują separacji dokument/widok, który jest częścią `DocObject` interfejsu projektu. Użytkownicy używać całego DocObject do działania jako widok zamiast bardziej abstrakcyjny (i mniej formalny) pojęcie danych, nazywane `DocData`. `DocView` obiekty zawsze są osadzone w obiekty ramki dokumentów (okien podrzędnych MDI) IDE.  
  
 DTE  
 `DTE` Obiektu (rozszerzalność narzędzi rozwoju) jest punktem dostępu najwyższy w modelu automatyzacji programu Visual Studio, dzięki czemu można programowo zautomatyzować i rozszerzania środowiska IDE.  
  
 Dynamiczne okna Pomoc  
 Okna narzędzia, która jest zaimplementowana IDE i wyświetla listę tematów pomocy F1 lub słowo kluczowe wyszukiwania.  
  
 edytor  
 Kod (klasa CLSID), który implementuje `DocView`. Implementuje również `DocData` Jeśli separację widoku/danych jest obsługiwana.  
  
 rozszerzenie  
 Funkcja, która modyfikuje dostosowuje i dodaje do środowiska IDE. Możesz utworzyć rozszerzeń przy użyciu modelu automatyzacji lub VSPackages.  
  
 edytor zewnętrzny  
 Edytor, który nie jest specyficzne dla IDE, takich jak Microsoft Word. Został zarejestrowany za pomocą własnych mechanizmów, a można użyć poza IDE. Jeśli można ją osadzić tego edytora, pojawi się w obrębie okna w środowisku IDE. Jeśli nie można osadzić, tworzona jest osobnym oknie najwyższego poziomu.  
  
 hierarchia  
 Drzewo węzłów, każdy węzeł skojarzonej z zestawem właściwości.  
  
 niezależnie od składnika najwyższego poziomu  
 Składnik, który korzysta z niemodalnego okna najwyższego poziomu może efektywnie działać jako okno aplikacji autonomicznej, ale jest zaimplementowany jako obiekt w procesie. W związku z tym niezależne składnik najwyższego poziomu musi koordynować modalność i usługi Pętla wiadomości z IDE. Obiekty w procesie nie mają własnych pętli komunikatów.  
  
 Dostawca informacji o  
 Dostawca informacji jest moduł, który można wyszukać słowa kluczowe i zwraca listę tematów, w formie `IVsUserContextItem` obiektów. Aby zapewnić elementy słów kluczowych F1 i wyszukiwania dla dostawcy informacji, należy zarejestrować skompilowanego pliku pomocy (. HxS) w systemie. Tematy pomocy w tych plikach są używane do zawierają listę tematów wyświetlane w oknie Pomoc dynamiczna i wyświetlany, czy użytkownik naciśnie klawisz F1.  
  
 składnik w miejscu  
 Obiekt pakiet VSPackage, który implementuje `IOleInPlaceComponent` interfejsu do zarządzania okno będzie zawarty w okno dokumentu własnością IDE. Składniki w miejscu nie uczestniczą w standardowe OLE-scalania menu; Zamiast tego one zintegrować ich elementy interfejsu użytkownika IDE.  
  
 Istnieją dwa typy składników w miejscu: hardwired w miejscu składników i formantów składników.  
  
 Składniki w miejscu Hardwired mają menu, pasków narzędzi i poleceń, które są ściśle zintegrowane interfejs użytkownika IDE stanowiący, jeśli zostały one wbudowana bezpośrednio w IDE.  
  
 Formanty składników nie ma żadnych własne elementy interfejsu użytkownika, zintegrowane środowisko IDE; Zamiast tego użyć ich menu, poleceń i paski narzędzi programu IDE. Na przykład polecenie Bold może posłużyć do pogrubienie zaznaczonego wyrazu w formancie tekstu sformatowanego osadzone w formularzu. Jednak formantów składników mogą żądać, że dynamicznie zainstalowanych składników interfejsu użytkownika elementy mają być wyświetlane.  
  
 Usługa języka  
 Zestaw obiektów, który umożliwia deweloperom pakiet VSPackage implementowania funkcji edytora kodu języka komputera, takiego jak tekst oznaczenie i oznaczanie kolorami.  
  
 Projekt różne pliki  
 Projekt używany do domu otwartych plików, które nie są w żadnym projekcie. Na liście elementów w tym projekcie nie jest trwały.  
  
 projekt  
 Projekty składają się obiekty w hierarchii, lub obiektów COM, które implementują `IVsHierarchy` interfejsu.  
  
 specyficzne dla projektu projektancie lub edytorze  
 Projektant, której nie można użyć niezależnie od typu projektu. Wszystkie projektantów specyficznego dla projektu należy wprowadzić swoje informacje fabryki edytora w rejestrze. IDE następnie można utworzyć wystąpienia projektanta przy każdym otwarciu określonego typu plików w danym projekcie.  
  
 Okno typu projektu  
 Okno stale śledzi hierarchii aktualnie aktywnego projektu i elementu z kontekst zaznaczenia globalnych. Użyj typu projektu windows `SVsTrackSelectionEx` Usługa alertów IDE zmian oraz wyświetlanie opinii dla użytkownika. Eksplorator rozwiązań jest to przykład okna typu projektu.  
  
 Okno właściwości  
 Wcześniej przeglądarce właściwości.  
  
 Projekty oparte na odwołanie  
 Projekt, który nie wymaga plików dla projektu w tym samym katalogu. Zamiast tego odwołania do plików z innych katalogów niepowiązanych są przechowywane i obsługiwane przez sam projekt.  
  
 uruchomionej tabeli dokumentu  
 Struktury wewnętrznej, za pomocą którego IDE przechowuje listę wszystkich aktualnie otwarte dokumenty. Ta lista zawiera wszystkie otwarte dokumenty w pamięci, niezależnie od tego, czy dokumenty są obecnie edytowany. Dokument jest dowolnego elementu, który jest zapisywana, w tym procedur składowanych otwarty w edytorze, pliki w projekcie lub głównego pliku projektu (na przykład plik *.vcproj).  
  
 Kontekst zaznaczenia  
 Dane, które jest częścią szczegóły każdego okna w środowisku IDE i służy do śledzenia aktywnych zaznaczeń. Kontekst zaznaczenia obejmuje:  
  
-   Wskaźnik do `IVsHierarchy` interfejsu hierarchii projektu  
  
-   Identyfikator elementu elementu projektu.  
  
-   Wskaźnik do `ISelectionContainer` interfejsu, zapewniając dostęp do właściwości dla obiektów active.  
  
-   Tablica wartości elementu.  
  
 usługa  
 Kontrakt dla zestawu interfejsów modelu COM, które znajdują się w jednym obiekcie COM. Podczas tworzenia usługi, który jest identyfikowany przez identyfikator GUID, możesz zdefiniować zestaw interfejsów modelu COM, wykonujące usługi. Obiekty COM za pomocą usług do komunikowania się ze sobą.  
  
 Rozwiązania  
 Grupa powiązane projekty, z których użytkownik pracuje.  
  
 Standardowa projektanta  
 Projektanta, który można niezależnie od typu projektu. Wszystkie standardowe projektantów wprowadzić informacje o fabryki edytora w rejestrze. IDE następnie można utworzyć wystąpienia projektanta przy każdym otwarciu plików z określonym rozszerzeniem. Dane muszą zostać zachowane w pliku.  
  
 standardowego edytora  
 Edytor, który może służyć jako niezależne od dowolnego typu określonego projektu. Takie edytory ma EditorFactories zarejestrowany w rejestrze. Dzięki temu IDE do lokalizowania i wywołać edytora.  
  
 Standardowy Edytor systemu operacyjnego  
 Osadzanie nie jest Visual Studio określone. Jest on zarejestrowany za pomocą dobrze znanych klucze Win32 (na przykład Eksploratora Win32 potrafi do wywołania). Jeśli można ją osadzić takie edytora, Edytor nadal będą uwzględniane w jego miejsce w IDE. W przeciwnym razie dla takich edytory tworzony jest osobnym oknie najwyższego poziomu.  
  
 kontekst podrzędny w zbiorze  
 `IVsUserContext` Obiekt połączony zbiór kontekstu. Ten obiekt zawiera słowa kluczowe wyszukiwania, słów kluczowych F1 i atrybuty do wyboru w składniku IDE. Kontekst podrzędny przykładami polecenie w oknie narzędzi lub słów kluczowych w edytorze.  
  
 Lista zadań  
 Okna narzędzia, która jest zaimplementowana IDE i wyświetla listę aktywnych zadań.  
  
 Bufor tekstowy  
 Nazwa pospolita dla obiekt `VSTextBuffer`.  
  
 Wyświetlanie tekstu  
 Nazwa pospolita dla obiekt `VSTextView`.  
  
 Narzędzie składnik najwyższego poziomu  
 Składnik, który działa jako okna podręcznego niemodalne, ściśle koordynowanie przy użyciu interfejsu użytkownika IDE. Podobnie jak niezależne składniki najwyższego poziomu składników najwyższego poziomu narzędzia muszą również koordynować modalność i usługi Pętla wiadomości z IDE.  
  
 składnik najwyższego poziomu  
 Obiekt pakiet VSPackage, który zarządza niemodalne okno najwyższego poziomu zamiast obszaru klienckiego okna IDE. Składniki najwyższego poziomu wdrożenia `IOleComponent` interfejsu, aby móc korzystać z usługi Pętla wiadomości, takich jak dostęp do czasu bezczynności.  
  
 Aktywne interfejsu użytkownika  
 Obiekt pakiet VSPackage, który jest widoczny i aktualnie ma fokus.  
  
 Hierarchia interfejsu użytkownika  
 Obiekt COM, który implementuje `IVsUIHierarchy` interfejsu, aby umożliwić wyświetlanie hierarchii. Implementuje oknie hierarchii interfejsu użytkownika `ISelectionContainer` interfejsu zaktualizować okna właściwości; innych okien typu projektu można użyć tej implementacji, w razie potrzeby.  
  
 VSCT  
 Tabela polecenia programu Visual Studio. Plik vsct zawiera informacje o zachowania elementów menu, pasków narzędzi i poleceń w formacie XML i umieszczania.  
  
 Pakiet VSPackage  
 Instalowalnych część oprogramowania, rozszerzający środowiska IDE programu Visual Studio, podając przynajmniej jednej z następujących czynności: interfejs użytkownika, usług, typów projektów lub Edytor/projektanta. Pakiet VSPackage składa się z obiektu COM, który implementuje `IVsPackage` interfejsu i co najmniej jeden innych obiektów COM, które implementuje inne interfejsy do obsługi wybór i innych funkcji. Ponadto pakiet VSPackage ma wymagania dotyczące określonej rejestracji.