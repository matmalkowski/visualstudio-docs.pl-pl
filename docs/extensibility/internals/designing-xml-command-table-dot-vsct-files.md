---
title: Projektowanie tabeli polecenia XML (. Pliki Vsct) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 865baa3f7b4b0fe4cbbaf2cdf34e9e8041d5c121
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="designing-xml-command-table-vsct-files"></a>Projektowanie tabeli polecenia XML (. Pliki Vsct)
Plik XML polecenia tabeli (vsct) opisano układ i wygląd elementów polecenia pakiet VSPackage. Polecenie elementy obejmują przyciski, pola kombi, menu, paski narzędzi i grupy elementów polecenia. W tym temacie opisano XML pliki tabeli poleceń, ich wpływ na elementy poleceń i menu oraz sposób ich tworzenia.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Polecenia, menu, grup i pliku vsct
 vsct pliki są zorganizowane wokół polecenia, menu oraz grup polecenia. Tagi XML w pliku vsct reprezentują każdy z tych elementów, oraz innych skojarzonych elementów, jak przyciski poleceń, rozmieszczenia polecenia i map bitowych.

 Podczas tworzenia nowego pakietu VSPackage uruchamiając [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] szablonu pakietu szablon generuje plik vsct niezbędne dla polecenia menu, okna narzędzia lub edytora niestandardowego, w zależności od ustawień. Następnie można zmodyfikować tego pliku vsct, aby spełnić wymagania określone pakiet VSPackage. Przykłady sposobu modyfikowania pliku vsct, można znaleźć w przykładach w [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

 Aby utworzyć plik vsct nowy, pusty, zobacz [porady: tworzenie. Pliku Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Po utworzeniu Dodaj elementy, atrybuty i wartości XML do pliku do opisywania układu elementu polecenia. Aby uzyskać szczegółowe schematu XML, zobacz [odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Różnice między plikami .ctc i vsct
 Gdy znaczenie za tagi XML w pliku vsct są takie same, jak te, w obecnie przestarzały format pliku .ctc, ich implementacja będzie nieco inny.

-   Nowy  **\<extern >** tag jest, gdzie możesz odwoływać się inne pliki .h kompilację, takich jak te dotyczące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] paska narzędzi.

-   Podczas obsługi plików vsct **/ include** instrukcji, jak pliki .ctc zawiera również funkcje nowy \< **zaimportować >** elementu. Różnica polega na tym, **/ include** w przypadku **wszystkie** informacji, ale \< **zaimportować >** w przypadku tylko nazwy.

-   Podczas gdy pliki .ctc wymagają pliku nagłówka, w którym można zdefiniować Twojej dyrektywy preprocesora, co nie jest wymagane dla vsct plików. Należy umieścić w tabeli symboli, znajduje się w sieci dyrektywy  **\<Symbol >** elementów znajdujących się w dolnej części pliku vsct.

-   Funkcja pliki vsct  **\<adnotacji >** tagu, który umożliwia osadzanie informacji o żadnych Ci się podoba, takie jak informacje o lub nawet obrazy.

-   Wartości są przechowywane jako atrybuty w elemencie.

-   Flagi polecenie może być przechowywanych oddzielnie lub stos.  IntelliSense, jednak nie działa na flagi skumulowany polecenia. Aby uzyskać więcej informacji o flagach polecenia, zobacz [Element Command flagi](../../extensibility/command-flag-element.md).

-   Można określić wiele typów, takie jak podział listę rozwijaną, kombinacje itp.

-   Identyfikatory GUID nie weryfikacji.

-   Każdy element interfejsu użytkownika ma ciąg reprezentujący tekst, który jest wyświetlany z nim.

-   Elementem nadrzędnym jest opcjonalne. Przypadku jego pominięcia jest używana wartość "Grupy nieznany".

-   Ikona argument jest opcjonalny.

-   Sekcja mapy bitowej — taka sama jak .ctc pliku, z wyjątkiem tego, że można teraz określić nazwę pliku za pośrednictwem href, który będzie można dołączana przez kompilator vsct.exe w czasie kompilacji.

-   ResID — stary identyfikator zasobu mapy bitowej mogą być używane i nadal działa tak samo, jak pliki .ctc.

-   HRef — nowej metody, która pozwala określić nazwę pliku zasobu mapy bitowej. Przyjęto założenie, że wszystkie są używane, tak, można pominąć sekcji używane. Kompilator zasobów lokalnych dla pliku, następnie na net udziałów, a wszelkie zasoby zdefiniowane przez przełącznik /I najpierw umożliwia wyszukiwanie.

-   Keybinding — Nie należy określić emulator. Jeśli określisz, kompilator przyjmie założenie, że edytor i emulatora są takie same.

-   Keychord — został odrzucony. Nowy format jest klucz1, Mod1, Key2, Mod2.  Można określić znak, szesnastkowo lub stała VK.

 Nowy kompilator, vsct.exe, kompiluje pliki zarówno .ctc i vsct. Starego kompilatora ctc.exe, jednak nie rozpoznaje ani nie Kompiluj pliki vsct.

 Kompilatora vsct.exe służy do konwertowania istniejącego pliku .cto do pliku vsct. Aby uzyskać więcej informacji na ten temat, zobacz [porady: tworzenie. Plik Vsct z istniejącego. Pliku Cto](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Elementy pliku vsct
 Tabela polecenie ma następujące hierarchii i elementy:

 [CommandTable Element](../../extensibility/commandtable-element.md) — reprezentuje wszystkie polecenia, grupy menu i menu skojarzone z pakiet VSPackage.

 [Zewnętrzny Element](../../extensibility/extern-element.md) — odwołuje się do scalenia z pliku vsct pliki .h zewnętrznych.

 [Umieść Element](../../extensibility/include-element.md) — odwołuje się do żadnych plików dodatkowych nagłówków (.h) do skompilowania wraz z pliku your.vsct. Pliku vsct może zawierać pliki .h zawierające stałe definiujące poleceń, grupy menu i menu udostępniające IDE lub inny pakiet VSPackage.

 [Polecenia Element](../../extensibility/commands-element.md) — reprezentuje wszystkie poszczególnych poleceń, które mogą być wykonywane. Każde polecenie ma następujące elementy podrzędne cztery:

 [Element menu](../../extensibility/menus-element.md) — reprezentuje wszystkie menu i pasków zadań w pakiecie VSPackage. Menu są kontenerami dla grupy poleceń.

 [Grupuje Element](../../extensibility/groups-element.md) — reprezentuje wszystkich grup w pakiecie VSPackage. Grupy są kolekcjami poszczególnych poleceń.

 [Przyciski Element](../../extensibility/buttons-element.md) — reprezentuje wszystkie przyciski poleceń i elementów menu w pakiecie VSPackage. Przyciski są visual formanty, które mogą być związane z poleceniami.

 [Element map bitowych](../../extensibility/bitmaps-element.md) — reprezentuje wszystkie mapy bitowe dla wszystkich przycisków w pakiecie VSPackage. Mapy bitowe są obrazów wyświetlanych obok lub na przycisku polecenia, w zależności od kontekstu.

 [CommandPlacements Element](../../extensibility/commandplacements-element.md) — dodatkowe lokalizacje wskazuje, gdzie poszczególne polecenia powinien znajdować się w menu VSPackage.

 [VisibilityConstraints Element](../../extensibility/visibilityconstraints-element.md) — Określa, czy polecenie wyświetla cały razy lub tylko w niektórych kontekstach, np. gdy zostanie wyświetlony określonego okna dialogowego lub okna. Menu i poleceń, które mają wartość dla tego elementu spowoduje wyświetlenie tylko wtedy, gdy określony kontekst jest aktywny. Domyślnym zachowaniem jest do wyświetlenia polecenia przez cały czas.

 [Element powiązania klawiszy](../../extensibility/keybindings-element.md) — określa powiązań kluczy dla poleceń. Oznacza to, co najmniej jeden kombinacji klawiszy, które muszą zostać naciśnięte, można wykonać polecenia, takich jak **CTRL + S**.

 [UsedCommands Element](../../extensibility/usedcommands-element.md) — Informs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska, że chociaż określone polecenie jest implementowany przez inny kod, gdy bieżący pakiet VSPackage jest aktywny, zapewnia wykonania polecenia.

 `Symbols Element` — Zawiera symbol nazwy i identyfikatory GUID dla wszystkich poleceń w pakiecie.

## <a name="vsct-file-design-guidelines"></a>. Wytyczne dotyczące projektowania pliku Vsct
 Aby pomyślnie zaprojektować pliku vsct, zgodna z tymi wytycznymi.

-   Polecenia można umieścić tylko w grupach, grupy można umieścić tylko w menu i menu można umieścić tylko w grupach. W IDE grup są wyświetlane tylko menu i poleceń nie są.

-   Podmenu nie można przypisać bezpośrednio do menu, ale musi być przypisany do grupy, która z kolei jest przypisana do menu.

-   Polecenia, podmenu i grup można przypisać do jednej grupy element nadrzędny lub menu za pomocą pola nadrzędnego ich definiującego dyrektywy.

-   Organizowanie tabeli polecenia wyłącznie za pomocą pola nadrzędnego dyrektywy ma znaczne ograniczenie. Dyrektywy, które definiują obiekty może zająć nadrzędnego tylko jeden argument.

-   Ponowne użycie polecenia, grupy lub podmenu wymaga użycia nowej dyrektywy do utworzenia nowego wystąpienia obiektu z własną `GUID:ID` pary.

-   Każdy `GUID:ID` para musi być unikatowa. Ponowne użycie polecenia, który na przykład został umieszczony w menu, paska narzędzi, lub w menu kontekstowym, jest obsługiwane przez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu.

-   Polecenia i podmenu można również przypisać do wielu grup i grup można przypisać do wielu menu za pomocą [polecenia Element](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>. Informacje o pliku Vsct
 Jeśli wprowadzisz zmiany w pliku vsct po zarówno go skompilować i umieścić go w macierzystym satelitarnej biblioteki DLL, należy uruchomić **/nosetupvstemplates/Setup devenv.exe**. W ten sposób wymusza zasoby pakiet VSPackage określone w eksperymentalnym rejestru można odczytać i wewnętrznej bazy danych, który opisuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odbudowania.

 Podczas tworzenia jest możliwe w dla wielu projektów pakiet VSPackage utworzona i zarejestrowana w gałęzi rejestru eksperymentalna, która może prowadzić do mylące nieład w IDE. Aby rozwiązać ten problem, można przywrócić ustawienia domyślne, aby usunąć wszystkich zarejestrowanych VSPackages i wszelkie zmiany, które mogły zostać wprowadzone do środowiska IDE programu eksperymentalne hive. Aby zresetować eksperymentalne hive, narzędzie CreateExpInstance.exe dołączoną do programu Visual Studio SDK. Można znaleźć w

 **% PROGRAMFILES (x 86) %\Visual Studio \<wersji > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**

 Uruchom narzędzie przy użyciu wiersza polecenia **/reset CreateExpInstance**. Należy pamiętać, że to narzędzie usuwa z gałęzi eksperymentalne zarejestrowanych VSPackages, nie jest zainstalowane z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Zobacz też
 [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)