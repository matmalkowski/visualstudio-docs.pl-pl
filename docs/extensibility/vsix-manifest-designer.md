---
title: Projektant manifestu VSIX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0d7af3ab109c922a8182a93db6852a331229ceca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-manifest-designer"></a>Projektant manifestu VSIX
Modyfikuje VSIX pliku manifestu pakietu, który określa zachowanie instalacji określone dla rozszerzenia Visual Studio.  
  
 **Projektanta manifestu VSIX** mapy źródłowej schematu VSIX. Każdy element w schemacie można ustawić przy użyciu odpowiedniego formantu w projektancie. Aby uzyskać więcej informacji o schemacie, zobacz [odwołania 2.0 schematu rozszerzenia VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Aby otworzyć **projektanta manifestu VSIX**, zlokalizuj plik Source.Extension.vsixmanifest,a w **Eksploratora rozwiązań**i otworzyć plik. Jeśli plik nie zawiera prawidłowy kod XML, Projektant manifestu nie zostanie otwarty.  
  
> [!NOTE]
>  Source.Extension.vsixmanifest przekazywane są do extension.vsixmanifest podczas tworzenia pakietu.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Projektanta manifestu VSIX** zawiera cztery sekcje, które odnoszą się do tych elementów najwyższego poziomu schematu:  
  
-   Metadane  
  
-   Instalacji elementów docelowych  
  
-   Zasoby  
  
-   Zależności  
  
 Obszar nagłówek zawiera następujące formanty.  
  
 **Nazwa produktu**  
 W tym artykule opisano Nazwa rozszerzenia.  
  
 **Identyfikator produktu**  
 Określa informacje Unikatowy identyfikator dla tego pakietu.  
  
 **Autor**  
 Określa nazwę autora rozszerzenia.  
  
 **Wersja**  
 Określa numer wersji rozszerzenia.  
  
 **Metadanych** karta zawiera następujące formanty.  
  
 **Opis**  
 Zawiera opis tekstowy rozszerzenia, który będzie wyświetlany w **Menedżera rozszerzenia**.  
  
 **Język**  
 Określa domyślny język dla pakietu, który odpowiada danych tekstowych w manifeście. `Language` Atrybut następuje wspólnej Konwencji kod ustawień regionalnych języka środowiska uruchomieniowego (języka wspólnego CLR) dla zestawów zasobu, na przykład en-us, en, fr-fr. Wartość domyślna to neutralnej; oznacza to, że pakiet zostanie uruchomiony w dowolnej wersji językowej programu Visual Studio.  
  
 **Licencji**  
 Określa plik tekstowy, który zawiera licencji użytkownika, jeśli występuje.  
  
 **Ikona**  
 Określa plik grafiki (.png, bmp, JPEG, .ico), który zawiera ikonę, która ma być wyświetlany w **Menedżera rozszerzenia**, jeśli występuje ikona. Obraz ikony musi być 32 x 32 piksele lub będzie zmieniany na te wymiary. Jeśli brak określonych ikon, **Menedżera rozszerzenia** używa domyślnej ikony.  
  
 **Obraz podglądu**  
 Określa plik grafiki (.png, bmp, JPEG, .ico), który zawiera obraz podglądu, które mają być wyświetlane w **Menedżera rozszerzenia**, jeśli obraz podglądu jest obecny. Obraz podglądu musi być 200 x 200 pikseli. Jeśli nie obraz podglądu jest określony, **Menedżera rozszerzenia** korzysta z domyślnego obrazu.  
  
 **Tagi**  
 Dodaje znaczniki tekst służący do wskazówki dotyczące wyszukiwania.  
  
 **Uwagi do wersji**  
 Określa plik (txt, .rtf), który zawiera informacje o wersji. Ma również adres URL witryny sieci Web, który wyświetla informacje o wersji.  
  
 **Wprowadzenie — przewodnik**  
 Określa plik (txt, RTF), który zawiera informacje o sposobie używania rozszerzenie lub zawartości w pakiecie VSIX. Ten przewodnik jest wyświetlany, gdy instalacja rozszerzenia została ukończona. Ma również adres URL witryny sieci Web wyświetlający przewodnika.  
  
 **Więcej informacji o adresu URL.**  
 Określa adres URL witryny sieci Web, który zawiera dodatkowe informacje o produkcie.  
  
 **Zainstalować obiekty docelowe** karta zawiera następujące formanty.  
  
 **Typ instalacji**  
 Wyświetla listę **rozszerzenie programu Visual Studio** i **zestawu SDK rozszerzenia** jako docelowy typów instalacji. Opcje różnią się zależnie od typu wybranego przez użytkownika.  
  
 **Rozszerzenie programu Visual Studio**  
 Wyświetla listę **InstallationTarget** elementy, które opisują sposób można zainstalować pakietu, i na które produkty Visual Studio można zainstalować tego rozszerzenia. Każdy produkt został zidentyfikowany osobno według nazwy i wersji lub wersji zakresu.  Produkty można dodany do listy, modyfikować i usunięte. Nazwa i wersja produktu odpowiadają **identyfikator** i **wersji** atrybuty skojarzonego **InstallationTarget** elementu.  
  
 **Zakres wersji** jest [12,0, 14,0] i używa notacji następujące:  
  
-   [-minimalna wersja włącznie  
  
-   ]-maksymalna wersja włącznie  
  
-   (-minimalna wersja wyłączności  
  
-   ) — maksymalna wersja wyłączności  
  
-   Jednej wersji # - tylko określona wersja  
  
 **Rozszerzenia zestawu SDK**  
 Określa instalacji globalnej, który nie jest ograniczone do określonych produktów i wersji. **Docelowy identyfikator platformy** to platforma, takie jak "Windows", który docelowych. **Docelowa wersja platformy** wersji, takie jak 8.0 z docelową platformą. **Nazwa zestawu SDK** i **zestawu SDK w wersji** są nazwa i numer wersji zestawu SDK, odpowiednio.  
  
 **Ten plik VSIX jest instalowany dla wszystkich użytkowników (wymaga podniesienia uprawnień dotyczących instalacji)** pole wyboru  
 Jeśli to pole wyboru jest zaznaczone, to rozszerzenie jest zainstalowane dla wszystkich użytkowników. w przeciwnym razie jest ona zainstalowana tylko dla bieżącego użytkownika.  
  
 **Ten plik VSIX jest instalowany przez Instalatora Windows** pole wyboru  
 Jeśli to pole wyboru jest zaznaczone, to rozszerzenie jest zainstalowane przez Instalatora Windows (plik .msi); w przeciwnym razie jest instalowana jako typowy pakiet VSIX (plik .vsix).  
  
 **Zasoby** karta zawiera następujące formanty.  
  
 **Lista zasobów**  
 Wyświetla listę elementów zasobów, które opisano elementy rozszerzenia lub zawartość tego pakietu powierzchni. Każdego rozszerzenia lub zawartości elementu jest wyświetlany osobno według źródła, typu i ścieżkę. Elementy rozszerzeń i zawartości można dodany do listy, modyfikować i usunięte. Typ i ścieżka elementu rozszerzenia lub zawartość odpowiada `Type` i `Path` atrybuty skojarzonego `Asset` elementu. Znane są następujące:  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 Umożliwiają dodawanie lub edytowanie elementu zawartości, należy określić typ zasobu, czy zasób jest projekt w bieżącym rozwiązaniu lub pliku w systemie plików, a nazwa projektu. Można również określić nazwę folderu, w którym ma zostać osadzony.  
  
 Można także tworzenie własnych typów i nadaj im unikatowe nazwy.  
  
 **Zależności** karta zawiera następujące formanty.  
  
 **Nazwa źródła i zakres wersji**  
 Wyświetla listę elementów zależności tego pakietu, które są inne pakiety, których zależy ten pakiet. Jeśli określono pakietu zależności, musi być zainstalowany przed zainstalowaniem tego pakietu; w przeciwnym razie tego pakietu należy go zainstalować.  
  
 Zależności pakietów są określane przez identyfikator, nazwę zakres wersji, źródła i jak ma można rozpoznać zależności. Każdy pakiet zależności jest wyświetlany osobno według nazwy, wersji i źródła. Zależności pakietów można dodany do listy, modyfikować i usunięty.  
  
 Identyfikator musi być zgodna `ID` atrybutu metadane pakietów zależności. Źródło może też być projekt w bieżącym rozwiązaniu, obecnie zainstalowanego rozszerzenia lub pliku. **Jak jest zależności** ustawienie może być ścieżką względną zagnieżdżonych pakietu lub adres URL lokalizacji pobierania dla zależności. Identyfikator wersji i rozpoznawania zależności pakietu odpowiadają `Id`, `Version`, i `Location` atrybuty skojarzonego `Dependency` elementu.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu 2.0 rozszerzenia VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)