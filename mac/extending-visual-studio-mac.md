---
title: Rozszerzanie programu Visual Studio dla komputerów Mac
Description: Visual Studio for Mac's features and functionality can be extended with modules called extension packages. The first part of this guide creates a simple Visual Studio for Mac extension package to insert the date and time into a document. The second part of this guide introduces the fundamentals of the extension package system and some of the core APIs that form the foundation of Visual Studio for Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 589663fff7caa46899fe8f4213f5d29fe2772611
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="extending-visual-studio-for-mac"></a>Rozszerzanie programu Visual Studio dla komputerów Mac

Visual Studio for Mac zawiera zestaw modułów o nazwie *pakietów rozszerzenia*. Pakiety rozszerzeń umożliwia wprowadzenie nowych funkcji dla programu Visual Studio dla komputerów Mac, takie jak obsługa dodatkowych języków lub nowego szablonu projektu.

Pakiety rozszerzeń kompilacji z *rozszerzenia* punkty pozostałych pakietów rozszerzenia. Punkty rozszerzenia symboli zastępczych dla obszarów, które można rozszerzać, np. menu lub listę poleceń IDE. Pakiet rozszerzenia można tworzyć z punktu rozszerzenia rejestrując węzłem danych strukturalnych rozszerzenie, np. nowy element menu lub nowe polecenie. Każdy punkt rozszerzenia akceptuje niektóre typy rozszerzeń, takich jak *polecenia*, *konsoli*, lub *FileTemplate*. Moduł, który zawiera punkty rozszerzenia jest nazywany *dodatku hosta*, jak można rozszerzyć przez inne pakiety rozszerzenia.

Aby dostosować Visual Studio dla komputerów Mac, można utworzyć pakiet rozszerzenia, która tworzy z punktów rozszerzenia zawarte w hostach dodatku w istniejącym bibliotek w programie Visual Studio dla komputerów Mac, jak pokazano na poniższym diagramie:

![Architektura dodatków](media/extending-visual-studio-mac-addin1.png)

Aby pakietu rozszerzenia do kompilacji z programu Visual Studio dla komputerów Mac musi mieć rozszerzeń, które kompilacji z istniejącym punktów rozszerzenia w programie Visual Studio dla komputerów Mac IDE. Gdy pakiet rozszerzenia opiera się na punkt rozszerzenia obsługi, jest ono mieć _zależności_ na ten pakiet rozszerzenia.

Zaletą tego modularny projekt jest czy programu Visual Studio for Mac jest rozszerzalny — istnieje wiele punktów rozszerzenia, które mogą być wbudowane w system z pakietami rozszerzenia niestandardowego. Przykładami bieżących pakietów rozszerzenia obsługę języka C# i F #, debuger narzędzia i szablony projektów.

> [!NOTE]
> **Uwaga**: Jeśli projekt Maker dodatku, który został utworzony przed dodatku Maker 1.2, trzeba przeprowadzać migracji projektu, jak opisano w krokach [tutaj](https://mhut.ch/addinmaker/1.2).

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

W tej sekcji analizuje pliki różnych wygenerowanych przez producenta dodatku i wymaga danych rozszerzenia polecenia.

## <a name="attribute-files"></a>Atrybut plików

Pakiety rozszerzeń przechowywania metadanych dotyczących ich nazwy, wersji, zależności i inne informacje w języku C# atrybutów. Maker dodatku tworzy dwa pliki `AddinInfo.cs` i `AssemblyInfo.cs` do przechowywania i organizowania tych informacji. Pakiety rozszerzeń musi mieć unikatowy identyfikator i przestrzeń nazw określona w ich *atrybutu Addin*:

```
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Pakiety rozszerzeń musi również deklarować zależności od pakietów rozszerzenia, które posiadają punktów rozszerzenia, które są podłączane. Odwołuje się to automatycznie podczas kompilacji.

Ponadto dodatkowe informacje można dodać za pomocą dodatku węzeł odniesienia w konsoli rozwiązania dla projektu, ponieważ są określone przez na poniższej ilustracji:

![Wstaw Data zrzut ekranu](media/extending-visual-studio-mac-addin13.png)

Również mają odpowiednie `assembly:AddinDependency ` atrybuty dodawane na czas kompilacji. Po deklaracji metadanych i zależności w miejscu, można skupić się na podstawowych bloków konstrukcyjnych pakietu rozszerzenia.

## <a name="extensions-and-extension-points"></a>Rozszerzenia i punkty rozszerzenia

Punkt rozszerzenia to symbol zastępczy, który definiuje to struktura danych (typ), gdy rozszerzenie definiuje dane były zgodne do struktury określony przez punkt określonym rozszerzeniem. Punkty rozszerzenia określić, jaki typ rozszerzenia mogą akceptować w deklaracji. Rozszerzenia są deklarowane jako przy użyciu nazwy typu lub rozszerzenie ścieżki. Zobacz [odwołania do rozszerzenia punktu](http://monoaddins.codeplex.com/wikipage?title=Extension%20Points&referringTitle=Description%20of%20Add-ins%20and%20Add-in%20Roots) uzyskać szczegółowe informacje na temat tworzenia punkt rozszerzenia, które są potrzebne.

Architektura punktu rozszerzenia/rozszerzenia zachowuje programowanie programu Visual Studio for Mac szybka, modularna. 

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Rozszerzenia poleceń

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Polecenie rozszerzenia są rozszerzenia, które wskazują metod, które są wywoływane każdorazowo po wykonaniu.

Polecenie rozszerzenia są definiowane przez dodanie wpisów `/MonoDevelop/Ide/Commands` punkt rozszerzenia. Zdefiniowanego w naszym rozszerzenie `Manifest.addin.xml` następującym kodem:

 ```
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

Atrybut ścieżki, która określa punkt rozszerzenia, który jest ona w tym przypadku podłączyć do, zawiera węzeł rozszerzenia `/MonoDevelop/Ide/Commands/Edit`. Ponadto działa jako węzeł nadrzędny do polecenia. Polecenie węzeł ma następujące atrybuty:

*   **Identyfikator** — Określa identyfikator dla tego polecenia. Identyfikatory poleceń musi być zadeklarowany jako elementy członkowskie wyliczenia i są używane do nawiązania połączenia Commanditem poleceń.
*   **_label** — tekst, który ma być wyświetlany w menu.
*   **_description** — tekst, który ma być wyświetlany jako etykietka narzędzia dla przycisków paska narzędzi.
*   **defaultHandler** — Określa `CommandHandler` klasy, która obsługuje polecenie

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

Rozszerzenia CommandItem, które podłącza się do `/MonoDevelop/Ide/MainMenu/Edit` punkt rozszerzenia jest przedstawiona w poniższy fragment kodu:

```
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

CommandItem umieszcza polecenie określony w jej atrybutu id w menu. Rozszerza to CommandItem `/MonoDevelop/Ide/MainMenu/Edit` punkt rozszerzenia, dzięki czemu etykiety polecenia są wyświetlane w **Menu Edycja**. Należy pamiętać, że **identyfikator** CommandItem odpowiada identyfikator węzła polecenia `InsertDate`. Jeśli masz zamiar usunąć CommandItem **Wstaw datę** zniknie opcji z Menu Edycja.

### <a name="command-handlers"></a>Programy obsługi poleceń

`InsertDateHandler` Jest rozszerzeniem `CommandHandler` klasy. Zastępuje on dwie metody `Update` i `Run`. `Update` Metody jest poddawany kwerendzie zawsze, gdy polecenie jest wyświetlany w menu lub wykonywane przy użyciu powiązań klucza. Zmieniając obiekt informacji, można wyłączyć polecenia lub je ukryć, wypełnić tablicy poleceń i inne. To `Update` metody wyłącza polecenie, jeśli nie można znaleźć aktywnego *dokumentu* z *TextEditor* Wstawianie tekstu do:

```
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Należy zastąpić `Update` metody, gdy mają specjalne logikę Włączanie lub ukrywanie polecenia. `Run` Metoda wykonuje zawsze, gdy użytkownik wykonuje polecenie, które w tym przypadku występuje, gdy użytkownik wybierze polecenie z Menu Edycja. Ta metoda Wstawia datę i godzinę na karetki w edytorze tekstu:

```
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Zadeklarowana jako elementu członkowskiego wyliczenia w ramach polecenia `DateInserterCommands`:

```
public enum DateInserterCommands
{
  InsertDate,
}
```

To wiąże ze sobą polecenia i CommandItem — CommandItem wywołuje polecenia w przypadku wybrania CommandItem z **Menu Edycja**.

## <a name="ide-apis"></a>Interfejsy API środowiska IDE

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Informacje w zakresie obszarów, które są dostępne do tworzenia aplikacji, zobacz [odwołania do rozszerzenia drzewa](http://monodevelop.com/Developers/Articles/Extension_Tree_Reference) i [Przegląd interfejsu API](http://monodevelop.com/Developers/Articles/API_Overview). Podczas tworzenia pakietów zaawansowane rozszerzenia, należy także zapoznać się [artykuły Developer](http://monodevelop.com/Developers/Articles). Poniżej przedstawiono listę częściowe obszary do dostosowania:

*   Tablety
*   Schematy powiązań klucza
*   Zasady
*   Elementy formatujące kodu
*   Formaty plików projektu
*   Preferencje paneli
*   Opcje paneli
*   Protokoły debugera
*   Wizualizatory debugera
*   Układy obszaru roboczego
*   Węzły drzewa konsoli rozwiązania
*   Marginesy edytora źródła
*   Aparaty testów jednostkowych
*   Generatory kodu
*   Wstawki kodu
*   Docelowych platform
*   Docelowe środowisko uruchomieniowe
*   Zapleczy VC
*   Refaktoryzacja
*   Wykonanie procedury obsługi
*   wyróżnianie składni

## <a name="additional-information"></a>Dodatkowe informacje

> [!NOTE]
Obecnie pracujemy nad poprawy scenariusze rozszerzalności programu Visual Studio dla komputerów Mac. Jeśli tworzysz rozszerzenia i uzyskać dodatkowe informacje lub chcesz wyrazić swoją opinię, wypełnij [programu Visual Studio do tworzenia rozszerzenia Mac](https://aka.ms/vsmac-extensions-survey) formularza.