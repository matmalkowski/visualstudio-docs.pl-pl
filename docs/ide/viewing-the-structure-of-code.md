---
title: Wyświetlanie struktury kodu przy użyciu widoku klasy, należy wywołać hierarchii, przeglądarka obiektów i okno definicji kodu
ms.date: 05/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.documentoutline.window
- vs.objectbrowser
- vs.classview
- VS.CodeDefinitionView
- VS.CodeDefinitionWindow
- vs.componentpicker
- vs.callbrowser
helpviewer_keywords:
- document outline window
- Visual Studio, object browser
- call hierarchy
- Visual Studio, document outline window
- code definition window [Visual Studio]
- Visual Studio, class view
- Visual Studio, call hierarchy window
- class view
- object browser
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a271dfaba8fe533fee84799a0585a29d97e9c70
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34336142"
---
# <a name="view-the-structure-of-code-using-different-tool-windows"></a>Wyświetlanie struktury kodu przy użyciu innego narzędzia systemu windows

Należy zbadać, klasy i ich elementy członkowskie w programie Visual Studio przy użyciu różnych narzędzi systemu windows, w tym **widoku klasy**, **hierarchii wywołań**, **przeglądarki obiektów**i **Kodu definicji** (tylko C++). Te narzędzia windows można sprawdzić kod w projektach Visual Studio, składników .NET Framework, składniki modelu COM, bibliotek dołączanych dynamicznie (DLL), i wpisz bibliotek (TLB).

Można również użyć **Eksploratora rozwiązań** typów i członków w projektach, wyszukiwanie symboli, przeglądanie metody hierarchii wywołań, Znajdź odwołania do symboli i widoku więcej, bez konieczności przełączania się między wiele okien narzędzi.

Jeśli masz program Visual Studio Enterprise edition, możesz użyć *code map* do wizualizacji struktury kodu i jego zależności między całego rozwiązania. Aby uzyskać więcej informacji, zobacz [zależności mapy przy użyciu map kodu](../modeling/map-dependencies-across-your-solutions.md).

## <a name="class-view-visual-basic-c-c"></a>Widok klas (Visual Basic, C#, C++)

**Widok klasy** jest wyświetlany jako część **Eksploratora rozwiązań** i jako osobne okno. **Widok klasy** Wyświetla elementy aplikacji. Górne okienko wyświetla obszary nazw, typów, interfejsy, wyliczenia i klasy oraz dolne okienko elementów członkowskich, które należą do typu wybranego w górnym okienku. Za pomocą tego okna, można przenieść do definicji elementu członkowskiego w kodzie źródłowym (lub w **przeglądarki obiektów** Jeśli element jest zdefiniowany poza rozwiązania).

Nie masz skompilować projekt, aby wyświetlić jego elementy w **widoku klasy**. Okno jest odświeżany podczas modyfikowania kodu w projekcie.

Można dodać kod do projektu, wybierając węzeł projektu i wybierając pozycję **Dodaj** przycisk, aby otworzyć **Dodaj nowy element** okno dialogowe. Kod zostanie dodany w oddzielnym pliku.

Jeśli projektu jest zaewidencjonowany do kontroli kodu źródłowego, co **widoku klasy** element Wyświetla ikonę, która wskazuje stan kodu źródłowego pliku. Polecenia kontroli kodu źródłowego wspólne, takie jak **Wyewidencjonuj**, **Zaewidencjonuj**, i **Pobierz najnowszą wersję** są także dostępne w menu skrótów dla elementu.

### <a name="class-view-toolbar"></a>Pasek narzędzi widoku klasy

**Widoku klasy** narzędzi zawiera następujące polecenia:

|||
|-|-|
|**Nowy Folder**|Tworzy folder wirtualny lub podfolder, w którym można organizować często używanych elementów. Są one zapisywane w aktywnym rozwiązaniu (*.suo*) pliku. Po zmienić lub usunąć element w kodzie, może się pojawić folder wirtualny jako węzeł błędu. Aby rozwiązać ten problem, Usuń węzeł błędu. Jeśli zmieniono element, możesz go przenieść z hierarchii projektu do folderu ponownie.|
|**Wstecz**|Powoduje przejście do poprzednio wybranego elementu.|
|**Prześlij dalej**|Przechodzi do następnego wybranego elementu.|
|**Wyświetlanie diagramu klas** (tylko dla projektów kod zarządzany)|Stają się dostępne po wybierz obszar nazw lub typ w **widoku klasy**. Po wybraniu przestrzeni nazw diagramu klas są wyświetlane wszystkie typy w nim. Po wybraniu typu diagramu klas zawiera tylko tego typu.|

### <a name="class-view-settings"></a>Ustawienia widoku klas

**Ustawienia widoku klasy** przycisk na pasku narzędzi ma następujące ustawienia:

|||
|-|-|
|**Pokaż typy podstawowe**|Typy podstawowe są wyświetlane.|
|**Pokaż typy pochodne**|Typy pochodne są wyświetlane.|
|**Pokaż ukryte typy i składniki**|Ukryte typy i składniki (nie przeznaczony do użycia przez klientów) są wyświetlane w szary tekst.|
|**Pokaż publiczne elementy członkowskie**|Publiczne elementy członkowskie są wyświetlane.|
|**Pokaż chronione elementy członkowskie**|Elementy chronione są wyświetlane.|
|**Pokaż prywatne elementy członkowskie**|Prywatne elementy członkowskie są wyświetlane.|
|**Pokaż inne elementy członkowskie**|Inne rodzaje elementów członkowskich są wyświetlane, uwzględniając wewnętrzny (lub Friend w języku Visual Basic) elementy członkowskie.|
|**Pokaż dziedziczone elementy członkowskie**|Dziedziczone elementy członkowskie są wyświetlane.|
|**Pokaż metody rozszerzenia**|Metody rozszerzenia są wyświetlane.|

### <a name="class-view-shortcut-menu"></a>Menu skrótów klasy widoku

W menu skrótów **widoku klasy** może zawierać następujące polecenia, w zależności od typu wybranego projektu:

|||
|-|-|
|**Przejdź do definicji**|Wyszukuje definicji elementu w kodzie źródłowym lub **przeglądarki obiektów**, jeśli element nie jest zdefiniowany w otwartego projektu.|
|**Przejdź do definicji**|Wyświetla wybrany element w **przeglądarki obiektów**.|
|**Znajdź wszystkie odwołania**|Wyszukuje element aktualnie zaznaczony obiekt i wyświetla wyniki w **znaleźć wyników** okna.|
|**Typ filtru** (tylko kod zarządzany)|Wyświetla tylko wybranego typu lub przestrzeni nazw. Filtr można usunąć, wybierając **znaleźć wyczyść** (**X**) znajdujący się obok **znaleźć** pole.|
|**Kopiuj**|Kopiuje w pełni kwalifikowana nazwa elementu.|
|**Sortuj alfabetycznie**|Wyświetla listę typów i członków alfabetycznie według nazwy.|
|**Sortuj według typu członka**|Wyświetla listę typów i członków w kolejności według typu (taki sposób, że interfejsy poprzedzać klasy, interfejsy poprzedzać delegatów i metody poprzedzać właściwości).|
|**Sortuj według dostępu do elementu członkowskiego**|Typy list i elementów członkowskich w kolejności według dostępu typ, takich jak publicznych lub prywatnych.|
|**Grupuj według typu członka**|Sortowane typów i członków do grupy według typu obiektu.|
|**Przejdź do deklaracji** (tylko kod C++)|Wyświetla deklaracji typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do definicji**|Wyświetla definicji typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do odwołania**|Wyświetla odwołanie do typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Wyświetlanie hierarchii wywołań**|Wyświetla w wybranej metody **hierarchii wywołań** okna.|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Wywołaj okno hierarchii (Visual Basic, C#, C++)

**Hierarchii wywołań** okna pokazuje, gdzie jest wywoływany danej metody lub właściwości. Wyświetlane są również metody, które są wywoływane z tej metody. Można wyświetlić wiele poziomów wykresu wywołań, przedstawiający relacje wywołujący wywoływany metody w podanym zakresie.

Można wyświetlić **hierarchii wywołań** okno Wybieranie w edytorze — metoda (lub właściwości lub konstruktora), a następnie wybierając **hierarchii wywołań widoku** menu skrótów. Wyświetlanie powinien wyglądać na poniższej ilustracji:

![Okno hierarchii wywołań w programie Visual Studio](../ide/media/multiplenodes.png)

Za pomocą listy rozwijanej na pasku narzędzi, można określić zakres poziomu hierarchii: rozwiązania, bieżącego projektu lub bieżącego dokumentu.

W okienku głównym Wyświetla wywołania do i z metody i **wywołać witryn** okienko Wyświetla lokalizację wybranego wywołania. Dla elementów członkowskich, które są wirtualne lub abstrakcyjne **nazwę metody zastąpienia** węzeł jest dostępny. Dla członków interfejsu **nazwę metody implementuje** węzeł jest dostępny.

**Hierarchii wywołań** okna nie znaleźć metody odwołania do grup, które obejmują miejscach, gdzie metoda jest dodawana jako program obsługi zdarzeń lub jest przypisany do delegata. Aby znaleźć te odwołania, należy użyć **Znajdź wszystkie odwołania** polecenia.

W menu skrótów **hierarchii wywołań** okna zawiera następujące polecenia:

|||
|-|-|
|**Dodaj jako nowy element główny**|Dodaje wybrany węzeł jako nowego węzła głównego.|
|**Usuwanie głównego**|Usuwa wybrany główny węzeł w okienku widoku drzewa.|
|**Przejdź do definicji**|Przechodzi do oryginalnej definicji metody.|
|**Znajdź wszystkie odwołania**|Znajduje w projekcie wszystkie odwołania do wybranej metody.|
|**Kopiuj**|Kopiuje wybranego węzła (ale nie jego węzłami podrzędnymi).|
|**Odśwież**|Odświeża informacje.|

## <a name="BKMK_ObjectBrowser"></a> Przeglądarka obiektów

**Przeglądarki obiektów** okno Wyświetla opisy kodu w projektach.

Można filtrować składniki, które chcesz wyświetlić za pomocą listy rozwijanej w górnej części okna. Niestandardowe składniki mogą być pliki wykonywalne kodu zarządzanego, zestawy bibliotek, biblioteki typów i *.ocx* plików. Nie jest możliwie dodanie niestandardowych składników C++. Ustawienia niestandardowe są zapisywane w katalogu aplikacji programu Visual Studio użytkownika *%APPDATA%\Microsoft\VisualStudio\15.0\ObjBrowEX.dat*.

W lewym okienku **przeglądarki obiektów** pokazuje zestawy. Można rozwinąć do wyświetlenia przestrzeni nazw, które zawierają zestawy, a następnie rozwiń przestrzeni nazw, aby wyświetlić typy, które zawierają. Po wybraniu typu jej elementów członkowskich (na przykład właściwości i metody) są wyświetlane w okienku po prawej stronie. Dolnym okienku po prawej stronie wyświetla szczegółowe informacje na temat wybranego elementu.

Możesz wyszukać konkretny element za pomocą **wyszukiwania** u góry okna. Wyszukiwanie jest rozróżniana wielkość liter. Wyniki wyszukiwania są wyświetlane w okienku po lewej stronie. Aby wyczyścić wyszukiwanie, wybierz **Wyczyść wyszukiwanie** (**X**) znajdujący się obok **wyszukiwania** pole.

**Przeglądarki obiektów** śledzi zaznaczeń zostały wykonane, a można przechodzić między opcje przy użyciu **do przodu** i **ponownie** przycisków na pasku narzędzi.

Można użyć **przeglądarki obiektów** można dodać odwołania do zestawu otwartego rozwiązania zaznaczenie elementu (zestawu, przestrzeni nazw, typu lub elementu członkowskiego) i wybierając pozycję **Dodaj odwołanie** przycisk na pasku narzędzi.

### <a name="object-browser-settings"></a>Ustawienia przeglądarki obiektów

Za pomocą **ustawienia przeglądarki obiektów** przycisk na pasku narzędzi, można określić jeden z następujących widoków:

|||
|-|-|
|**Widok przestrzenie nazw**|Wyświetla obszary nazw, a nie fizycznych kontenerów, w okienku po lewej stronie. Przestrzenie nazw przechowywanych w wielu fizycznych kontenerów zostaną scalone.|
|**Kontenery widoku**|Wyświetla fizycznych kontenerów, a nie w przestrzeni nazw, w okienku po lewej stronie. **Wyświetlanie nazw** i **kontenery widoku** ustawień wykluczają się wzajemnie.|
|**Pokaż typy podstawowe**|Wyświetla typy podstawowe.|
|**Pokaż typy pochodne**|Wyświetlanie typów pochodnych.|
|**Pokaż ukryte typy i składniki**|Wyświetla ukryte typy i składniki (nie przeznaczony do użycia przez klientów), w szary tekst.|
|**Pokaż publiczne elementy członkowskie**|Wyświetla publiczne elementy członkowskie.|
|**Pokaż chronione elementy członkowskie**|Wyświetla chronione elementy członkowskie.|
|**Pokaż prywatne elementy członkowskie**|Wyświetla prywatne elementy członkowskie.|
|**Pokaż inne elementy członkowskie**|Wyświetla innych typów elementów członkowskich, w tym wewnętrzny (lub Friend w języku Visual Basic) elementy członkowskie.|
|**Pokaż dziedziczone elementy członkowskie**|Wyświetla dziedziczone elementy członkowskie.|
|**Pokaż metody rozszerzenia**|Zawiera metody rozszerzenia.|

### <a name="object-browser-shortcut-menu-commands"></a>Polecenia menu skrótów przeglądarki obiektów

W menu skrótów **przeglądarki obiektów** może zawierać następujące polecenia, w zależności od rodzaju elementu wybranych:

|||
|-|-|
|**Przejdź do definicji**|Pokazuje węzła podstawowego dla wybranego elementu.|
|**Znajdź wszystkie odwołania**|Wyszukuje element aktualnie zaznaczony obiekt i wyświetla wyniki w **znaleźć wyników** okna.|
|**Filtrowanie do typu**|Wyświetla tylko wybranego typu lub przestrzeni nazw. Filtr można usunąć, wybierając **Wyczyść wyszukiwanie** przycisku.|
|**Kopiuj**|Kopiuje w pełni kwalifikowana nazwa elementu.|
|**Usuń**|Jeśli zakres jest zbiór niestandardowych składników, spowoduje usunięcie wybranego składnika, z zakresu.|
|**Sortuj alfabetycznie**|Wyświetla listę typów i członków alfabetycznie według nazwy.|
|**Sortuj według typu obiektu**|Wyświetla listę typów i członków w kolejności według typu (taki sposób, że interfejsy poprzedzać klasy, interfejsy poprzedzać delegatów i metody poprzedzać właściwości).|
|**Sortuj według dostępu do obiektów**|Typy list i elementów członkowskich w kolejności według dostępu typ, takich jak publicznych lub prywatnych.|
|**Grupuj według typu obiektu**|Sortowane typów i członków do grupy według typu obiektu.|
|**Przejdź do deklaracji** (tylko w języku C++ projektów)|Wyświetla deklaracji typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do definicji**|Wyświetla definicji typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do odwołania**|Wyświetla odwołanie do typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Wyświetlanie hierarchii wywołań**|Wyświetla w wybranej metody **hierarchii wywołań** okna.|

## <a name="code-definition-window-c"></a>Okno definicji kodu (C++)

**Definicji kodu** okno wyświetla definicji wybranego typu C++ lub elementu członkowskiego w aktywnym projekcie. W edytorze kodu lub w oknie widoku kodu można wybrać typu lub elementu członkowskiego.

Mimo że to okno jest tylko do odczytu, można ustawić punktów przerwania lub zakładki w nim. Aby zmodyfikować definicję wyświetlanych, wybierz **edycji definicji** menu skrótów. To powoduje otwarcie pliku źródłowego w edytorze kodu i przenosi punkt wstawiania do wiersza, w którym rozpoczyna się definicji.

> [!NOTE]
> Począwszy od programu Visual Studio 2015, **definicji kodu** okna można używać tylko z kodem C++.

### <a name="code-definition-shortcut-menu"></a>Menu skrótów definicji kodu

W menu skrótów **definicji kodu** okna może zawierać następujące polecenia:

|||
|-|-|
|**Szybkie akcje i Refaktoryzacje**||
|**Zmiana nazwy**||
|**Generowanie grafu plików dołączanych**||
|**Definicji wglądu**||
|**Przejdź do definicji**|Wyszukuje definicji (lub definicji klasy częściowe) i wyświetla je w **znaleźć wyników** okna.|
|**Przejdź do deklaracji**||
|**Znajdź wszystkie odwołania**|Wyszukuje odwołania do typu lub elementu członkowskiego w rozwiązaniu.|
|**Wyświetlanie hierarchii wywołań**|Wyświetla metodę w **hierarchii wywołań** okna.|
|**Przełącznik nagłówek / plik kodu**||
|**Uruchom testy**|W przypadku testów jednostkowych w projekcie, uruchamiane testy dla wybranego kodu.|
|**Debuguj testy**||
|**Punkt przerwania**|Wstawia punkt przerwania (lub śledzenia).|
|**Uruchom do kursora**|Uruchamia program w trybie debugowania w lokalizacji kursora.|
|**fragment kodu**||
|**Wytnij**, **kopiowania**, **wklejania**||
|**Adnotacja**||
|**Obramowanie**|Polecenia standardowe zwijania.|
|**Ponowne skanowanie**||
|**Edytowanie definicji**|Przenosi punkt wstawiania do definicji w oknie kodu.|
|**Wybierz kodowanie**|Otwiera **kodowanie** okna tak, aby można ustawić kodowanie dla tego pliku.|

## <a name="document-outline-window"></a>Okno konspektu dokumentu

Można użyć **konspekt dokumentu** okna w połączeniu z projektanta widoków, takich jak projektant strony XAML lub projektanta formularzy systemu Windows lub stron HTML. To okno wyświetla elementy w widoku drzewa, dzięki czemu można wyświetlać struktury logicznej formularza lub strony i Znajdź formantów, które są głęboko osadzone lub ukryte.

## <a name="see-also"></a>Zobacz także

- [Widok klasy i Przeglądarka obiektów, ikony](../ide/class-view-and-object-browser-icons.md)