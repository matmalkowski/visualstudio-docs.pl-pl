---
title: W programie Visual Studio SDK | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fff6b720c11f3342a5894489186f57d397dd91b5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134565"
---
# <a name="inside-the-visual-studio-sdk"></a>Wewnątrz zestawu Visual Studio SDK
Ta sekcja zawiera szczegółowe informacje na temat rozszerzeń programu Visual Studio, w tym architektura programu Visual Studio, składniki, usługi, schematów, narzędzia i podobne.  
  
## <a name="extensibility-architecture"></a>Rozszerzalność architektury  
 Na poniższej ilustracji przedstawiono architekturę rozszerzalności programu Visual Studio. VSPackages Podaj funkcji aplikacji, który jest współużytkowany przez IDE jako usługi. Standardowa IDE oferuje szeroką gamę usług, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, które zapewniają dostęp do funkcji okien IDE.  
  
 ![Ilustracja architektury środowiska](../../extensibility/internals/media/environment.gif "środowiska")  
Ogólny widok architektury programu Visual Studio  
  
## <a name="vspackages"></a>VSPackages  
 Pakiety VSPackage są modułów oprogramowania, które tworzą i rozszerzenia programu Visual Studio z elementów interfejsu użytkownika, usług, projektów, edytory i projektantów. Pakiety VSPackage są jednostki centralnej architektury programu Visual Studio. Aby uzyskać więcej informacji, zobacz [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 Visual Studio shell zapewnia podstawowe funkcje i obsługuje cross komunikacji między rozszerzeniami pakiety VSPackage i MEF składnika. Aby uzyskać więcej informacji, zobacz [programu Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Wskazówki dotyczące interfejsu użytkownika  
 Jeśli planujesz projektowanie nowych funkcji dla programu Visual Studio, należy podjąć przyjrzeć się te wskazówki dotyczące projektowania i użyteczność porady: [dotyczące środowiska użytkownika w usłudze Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Polecenia  
 Polecenia są funkcje, których wykonywanie zadań, takich jak drukowanie dokumentu, odświeżenie widoku lub utworzenie nowego pliku.  
  
 Podczas rozszerzania programu Visual Studio, można utworzyć polecenia i zarejestrować ich przy użyciu powłoki programu Visual Studio. Można określić, jak te polecenia będzie wyświetlana w IDE, na przykład w menu lub pasek narzędzi. Zazwyczaj polecenia niestandardowych wyświetlane **narzędzia** menu i polecenia do wyświetlania okna narzędzia, które będą widoczne w **inne okna** podmenu **widoku** menu.  
  
 Podczas tworzenia polecenia należy także utworzyć program obsługi zdarzeń dla niego. Program obsługi zdarzeń określa, kiedy polecenie jest widoczny, czy włączone, można zmodyfikować jego tekstu i gwarantuje, że polecenie odpowiednio reaguje po aktywowaniu. W większości przypadków środowiska IDE programu obsługi poleceń za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Polecenia w programie Visual Studio są obsługiwane począwszy od kontekstu polecenia najbardziej wewnętrznego, na podstawie zaznaczenia lokalne i nastąpi przejście najbardziej zewnętrznego kontekst, w oparciu o wybór globalne. Polecenia dodane do menu głównego są natychmiast dostępne dla skryptów.  
  
 Aby uzyskać więcej informacji, zobacz [polecenia, menu i pasków narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Menu i pasków narzędzi  
 Menu i pasków zadań umożliwiają użytkownikom wywołują polecenia. Menu są wierszy lub kolumn poleceń, które zwykle są wyświetlane jako elementy poszczególnych tekst u góry okna narzędzia. Podmenu są dodatkowej menu, które są wyświetlane, gdy użytkownik kliknie poleceń, które zawierają małą strzałką. Menu kontekstowe pojawiają się po kliknięciu niektórych elementów interfejsu użytkownika. Niektóre typowe nazwy menu to **pliku**, **Edytuj**, **widoku**, i **okna**. Aby uzyskać więcej informacji, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).  
  
 Paski narzędzi są wierszy lub kolumn, przycisków i innych kontrolek, takich jak pola kombi, pola listy i pól tekstowych. Przyciski paska narzędzi zwykle mają ikonę obrazy, takie jak ikony folderu **Otwórz plik** polecenia lub drukarki dla **drukowania** polecenia. Wszystkie elementy paska narzędzi są skojarzone z poleceń. Po kliknięciu przycisku paska narzędzi jego skojarzone polecenie jest uruchamiane. W przypadku kontrolka listy rozwijanej każdy element na liście rozwijanej jest skojarzony z innego polecenia. Niektóre formanty paska narzędzi, takich jak kontrola podziału, są hybryd. Po jednej stronie formantu jest przycisku paska narzędzi i drugiej stronie jest wyświetlany kilku poleceń, po kliknięciu strzałkę w dół.  
  
## <a name="tool-windows"></a>Okna narzędzi  
 Narzędzia systemu windows są używane w środowisku IDE do wyświetlania informacji. **Przybornik**, **Eksploratora rozwiązań**, **właściwości** okno i **przeglądarki sieci Web** przedstawiono okna narzędzi.  
  
 Narzędzia windows oferują zwykle różnych formantów, z którymi interakcji użytkownika. Na przykład **właściwości** okna pozwala użytkownikowi na ustawienie właściwości obiektów, które służą do określonego celu. **Właściwości** okno jest specjalne w tym sensie, ale również ogólne, ponieważ mogą być używane w wielu różnych sytuacjach. Podobnie **dane wyjściowe** okna jest specjalizowany, ponieważ zapewnia wyjściowego na podstawie tekstu, ale ogólne ponieważ wiele podsystemów w programie Visual Studio służy do konwertowania danych wyjściowych do użytkownika programu Visual Studio.  
  
 Należy wziąć pod uwagę następujące obrazów programu Visual Studio, który zawiera kilka okien narzędzi.  
  
 ![Zrzut ekranu](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Niektóre z okien narzędzi są zadokowanych w jednego okienka, który wyświetla okna narzędzia Eksplorator rozwiązań i ukrywa innych okien narzędzi, ale udostępnia, klikając karty. Na ilustracji przedstawiono dwie inne okna narzędzi **listy błędów** i **dane wyjściowe** okna zadokowanych w jeden.  
  
 Także wyświetlane jest okienko głównego dokumentu, które zawiera kilka okien edytora. Chociaż narzędzia windows mają zwykle tylko jedno wystąpienie (na przykład można otworzyć tylko jeden **Eksploratora rozwiązań**), okna edytora może mieć wiele wystąpień, z których każdy jest używany do edytowania innego dokumentu, ale które są zadokowane tym samym okienku. Na ilustracji przedstawiono panelu dokumentu, która ma dwa okna edytora, jedno okno projektanta formularza oraz okna przeglądarki, które zawiera strony początkowej. Wszystkie okna w panelu dokumentu są dostępne po kliknięciu karty, ale okno edytora, który zawiera plik EditorPane.cs jest widoczny i aktywne.  
  
 Podczas rozszerzania programu Visual Studio, można utworzyć narzędzia systemu windows, które pozwalają użytkownikom programu Visual Studio interakcję z rozszerzeniem. Można też utworzyć własne edytory umożliwiające edytowanie dokumentów użytkowników programu Visual Studio. Ponieważ narzędzia systemu windows, a edytory zintegrowania do programu Visual Studio, nie trzeba ich dock lub poprawnie wyświetlany na karcie program. Gdy są one poprawnie zarejestrowany w programie Visual Studio, zostanie automatycznie ma typowe funkcje narzędzia systemu windows i windows dokument w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [rozszerzanie i dostosowywanie okien narzędzi](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Okna dokumentów  
 Okno dokumentu jest oknem podrzędnym ramce okna interfejsu wielu dokumentów (MDI). Okna dokumentów są zazwyczaj używane do hostowania edytory tekstów, edytory formularza (znanej także jako projektantów) lub formantów edycji, ale może to również obsługiwać inne typy funkcjonalności. **Nowy plik** okno dialogowe zawiera przykłady okna dokumentów, których program Visual Studio udostępnia.  
  
 Większość edytorów specyficznych języka programowania lub typ plików, takich jak strony HTML, zestawy ramek, C++ plików lub pliki nagłówkowe. Po wybraniu szablonu w **nowy plik** okno dialogowe użytkownik dynamicznie tworzy okno dokumentu edytora dla danego typu pliku, który jest skojarzony z szablonem. Okno dokumentu tworzona jest również, gdy użytkownik otwiera istniejący plik.  
  
 Okna dokumentów są ograniczone do obszaru klienta MDI. Każde okno dokumentu ma kartę u góry, a kolejność tabulacji jest połączony z innymi oknami, które może być otwarty w obszarze MDI. Prawym przyciskiem myszy kartę elementu okno dokumentu Wyświetla menu skrótów, która obejmuje opcje do dzielenia obszaru MDI do wielu grup kartę pozioma lub pionowa. Dzielenie obszaru MDI umożliwia wielu plików, można go wyświetlić w tym samym czasie. Aby uzyskać więcej informacji, zobacz [okna dokumentów](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Edytory  
 Edytor programu Visual Studio umożliwia dostosować go i użyć go dla typu zawartości za pomocą Framework Managed Extensibility (MEF). W wielu przypadkach będzie trzeba utworzyć pakiet VSPackage rozszerzania edytora, jeśli chcesz dołączyć funkcje z powłoki (na przykład polecenia menu lub klawisza skrótu), łącząc rozszerzenia MEF z pakiet VSPackage.  
  
 Również można utworzyć niestandardowego edytora, na przykład, jeśli chcesz odczytu i zapisu do bazy danych lub jeśli chcesz użyć projektanta. Można również użyć zewnętrznego edytora, takiego jak Notatnik lub Microsoft WordPad. Aby uzyskać więcej informacji, zobacz [edytora i rozszerzenia usługi języka](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Usługi językowe  
 Jeśli chcesz edytorze programu Visual Studio do obsługi nowych słów kluczowych programowania lub nawet nowy język programowania, tworzenia usługi języka. Każda usługa języka może wprowadzić niektóre funkcje edycji pełni, częściowo lub w ogóle. W zależności od sposobu jego konfiguracji usługi języka zapewniają wyróżnianie składni, pasujących nawiasów klamrowych, obsługę funkcji IntelliSense i inne funkcje w edytorze.  
  
 Istotą usługi języka są analizatora składni i skanera. Skaner (lub lexer) dzieli pliku źródłowego na elementy, które są nazywane tokenów, a analizatorem ustanawia relacje tych tokenów. Podczas tworzenia usługi języka musi implementować analizatora i skanera tak, aby tokeny i gramatyki języka zrozumiałe dla programu Visual Studio. Można utworzyć usługi języka zarządzane lub niezarządzane. Aby uzyskać więcej informacji, zobacz [rozszerzalność usługi języka starszych](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Projekty  
 W programie Visual Studio projekty są kontenerami, które deweloperzy umożliwia organizowanie i kompilacja kodu źródłowego i innych zasobów. Projekty umożliwiają organizowanie, tworzenia, debugowania i wdrażania kodu źródłowego, odwołuje się do usług sieci Web i baz danych i innych zasobów. VSPackages można rozszerzyć system projektu programu Visual Studio, zapewniając typów projektów, podtypów projektu i narzędzi niestandardowych.  
  
 Może również zbierać projekty do rozwiązania, która to grupa składająca się z jednego lub więcej projektów, które współpracują ze sobą, aby utworzyć aplikację. Projekt oraz informacje o stanie dotyczących rozwiązania jest przechowywane w dwóch plików rozwiązania, plik tekstowy rozwiązania (sln) i plik binarny rozwiązania użytkownika opcji (.suo). Te pliki są podobne do plików grupy (.vbg), które były używane w starszych wersjach [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], a obszaru roboczego (.dsw) i użytkownika opcji plików (.opt), które były używane w starszych wersjach [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Aby uzyskać więcej informacji, zobacz [projekty](../../extensibility/internals/projects.md) i [rozwiązań](../../extensibility/internals/solutions.md).  
  
## <a name="project-and-item-templates"></a>Szablony projektów i elementów  
 Visual Studio zawiera szablony projektów wstępnie zdefiniowanych oraz szablony elementów projektu. Można również utworzyć własne szablony lub uzyskać szablony przez społeczność i integrowanie je do programu Visual Studio. [Galerii kodu MSDN](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) jest miejscem, aby przejść do szablonów i rozszerzenia.  
  
 Szablony zawierają projektu strukturę i podstawowe pliki, które są wymagane do utworzenia określonego rodzaju aplikacji, kontrolki, biblioteki lub klasy. Do opracowywania oprogramowania podobny do jednego z szablonów, należy utworzyć projekt, który jest oparty na szablonie, a następnie zmodyfikować plików w tym projekcie.  
  
> [!NOTE]
>  Taka architektura szablonu nie jest obsługiwana dla [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektów. Aby uzyskać informacje o sposobie tworzenia [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] szablony projektu, zobacz [projektowanie kreatora](/cpp/ide/designing-a-wizard).  
  
 Aby uzyskać więcej informacji, zobacz [Dodawanie projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Właściwości i opcje  
 **Właściwości** Wyświetla okna właściwości jednego lub wielu elementów wybranych: [rozszerzanie właściwości](../../extensibility/internals/extending-properties.md) strony opcji zawierają zestawy opcje, które odnoszą się do poszczególnych składników, takich jak Programowanie języka lub pakiet VSPackage: [opcje i opcje strony](../../extensibility/internals/options-and-options-pages.md). Ustawienia są zwykle interfejsu użytkownika funkcjach, które mogą być zaimportowane i wyeksportowane: [Obsługa ustawień użytkowników](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Usługi w programie Visual Studio  
 Usługa zawiera określony zbiór interfejsów dla składników można używać. Program Visual Studio oferuje zestaw usług, które mogą być używane przez wszystkie elementy, w tym rozszerzenia. Na przykład usługi Visual Studio umożliwiają narzędzia windows można wyświetlić lub ukryte dynamicznie, Włącz dostęp do pomocy paska stanu i zdarzeń interfejsu użytkownika. Edytor programu Visual Studio udostępnia usługi, które mogą być importowane przez rozszerzenia edytora. Aby uzyskać więcej informacji, zobacz [Using i dostarczanie usług](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Debugger  
 Debuger jest interfejs użytkownika ze składnikami debugowania specyficzny dla języka. Po utworzeniu nowej usługi języka, należy utworzyć aparat debugowania określonych na utworzenie punktu zaczepienia w debugera. Aby uzyskać więcej informacji, zobacz [programu Visual Studio Extensibility debugera](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Kontrola źródła  
 Aby uzyskać informacje o implementacji wtyczka do kontroli źródła lub pakiet VSPackage, zobacz [kontroli źródła](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Kreatorzy  
 Kreatora można utworzyć w połączeniu z nowym typem projektu, tak, aby kreator pomoże użytkownikom podjęcie prawidłowych decyzji podczas tworzenia nowego projektu tego typu. Aby uzyskać więcej informacji, zobacz [kreatorów](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Narzędzia niestandardowe  
 Niestandardowe narzędzia pozwalają skojarzyć narzędzie z elementu w projekcie i uruchamiania tego narzędzia, zawsze, gdy plik jest zapisywany. Aby uzyskać więcej informacji, zobacz [niestandardowego narzędzia](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>Narzędzia VSSDK  
 VSSDK obejmuje zestaw narzędzi, które mogą wymagać zapewnienia ich współdziałania z różnych aspektów VSPackages. Aby uzyskać więcej informacji, zobacz [VSSDK narzędzia](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>Za pomocą Instalatora Windows  
 W niektórych przypadkach może być konieczne użycie Instalatora Windows zamiast Instalatora VSIX: na przykład konieczne może być zapisu do rejestru. Aby dowiedzieć się, jak za pomocą Instalatora systemu Windows z rozszerzeń, zobacz [instalowanie VSPackages z Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Podgląd pomocy  
 Można zintegrować własne pomocy i stron F1 podglądu pomocy. Aby uzyskać więcej informacji, zobacz [podglądu pomocy firmy Microsoft w zestawie SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).