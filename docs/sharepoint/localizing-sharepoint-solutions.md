---
title: Lokalizowanie rozwiązań SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 855e8b708f3f3c5748a87406cdb2d66596bf3e77
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237773"
---
# <a name="localizing-sharepoint-solutions"></a>Lokalizowanie rozwiązań SharePoint

Proces przygotowywania aplikacji, dzięki czemu mogą być używane na całym świecie nosi nazwę lokalizacji. Lokalizacja jest tłumaczenie zasobów na określoną kulturę. Aby uzyskać więcej informacji, zobacz [Globalizing i lokalizacja aplikacji](../ide/globalizing-and-localizing-applications.md). Ten temat zawiera omówienie dotyczące lokalizowanie rozwiązań programu SharePoint.

Do zlokalizowania rozwiązania, Usuń ustalony ciągów z kodu i abstrakcyjnej je do plików zasobów. Plik zasobów jest [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]— na podstawie pliku z rozszerzeniem resx. Plik zasobów zawiera wersje przetłumaczone ciągi używane w rozwiązaniu. Aby uzyskać więcej informacji, zobacz [zasobów w aplikacjach](http://go.microsoft.com/fwlink/?LinkID=155844).

> [!NOTE]
> Dodaj tylko zasobów ciągu do plików zasobów rozwiązania programu SharePoint. Edytor zasobów umożliwia dodawanie zasobów innych niż ciąg, innych niż ciąg zasobów nie są wdrażane w programie SharePoint.

## <a name="resource-files"></a>Pliki zasobów

Istnieją trzy typy plików zasobów: domyślny, niezależny od języka i specyficzny dla języka.

|Typ plików zasobów|Opis|
|------------------------|-----------------|
|Domyślny|Znanej także jako zasób rezerwowy domyślne pliki zasobów zawiera ciągi zlokalizowane dla kultury domyślnej, takich jak angielski. Są one używane, jeśli można znaleźć żadnych plików zlokalizowanych zasobów dla określonego języka. Zasoby domyślne nie mają oddzielne pliki, są przechowywane w zestawie głównym aplikacji.|
|Niezależny od języka|Plik zasobu, który zawiera ciągi zlokalizowanej w innym języku, ale nie określoną kulturę. Na przykład "fr" francuski.|
|Specyficzne dla języka|Plik zasobu, który zawiera ciągi zlokalizowane dla języka i kultury. Na przykład "fr-CA" dla kanadyjskich francuski.|

 Aby uzyskać więcej informacji, zobacz [hierarchiczna organizacja zasobów do lokalizacji](http://go.microsoft.com/fwlink/?LinkId=178360).

 Aby określić domyślne pliki zasobów w projektach programu SharePoint, tworzonych w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wybierz **Język niezmienny (kraj niezmienny)** na liście kultury **dodawania zasobów** okna dialogowego, gdy użytkownik Dodawanie pliku zasobów.

## <a name="localizing-visual-studio-sharepoint-solutions"></a>Lokalizowanie rozwiązań SharePoint w Visual Studio
 Lokalizowanie rozwiązanie, należy rozważyć wszystkie rozwiązania wyświetlane użytkownikom informacje tekstowe. Komunikaty informacyjne, komunikaty o błędach i [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] muszą być przetłumaczone ciągi i tych tłumaczeń umieszczone w pliki zasobów.

 Każdy ciąg znaków w pliku zasobu ma unikatowy identyfikator. Użyj tego samego identyfikatora przetłumaczonego ciągu w każdym pliku zasobów. Na przykład jeśli "Ciąg1" identyfikator pierwszy ciąg domyślnego pliku zasobów, użyj tego samego identyfikatora dla pierwszy ciąg pliki zasobów specyficzne dla języka.

 Istnieją trzy obszary zwykle localize w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikacji programu SharePoint: funkcje, znaczników strony ASPX i kodu. Na potrzeby przykładu sekcje założono, że rozwiązania programu SharePoint, które chcesz przetłumaczyć na język niemiecki i japoński. Domyślnym językiem jest angielski.

### <a name="localizing-features"></a>Lokalizowanie funkcji
 Aby lokalizowanie funkcji, należy zastąpić ustalony tytuł i opis funkcji z wyrażeniem, które odwołuje się do ciągu przetłumaczonego tytuł i w pliku zlokalizowanych zasobów. Można to zrobić w **projektanta funkcji** w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md).

 Do zlokalizowania z funkcji angielskiej wersji językowej na niemiecki, japoński, Dodaj trzy elementy projektu pliku zasobu do projektu: jeden dla języka angielskiego, jeden na język niemiecki i jeden dla języka japońskiego. Pliki zasobów funkcji nie może służyć do lokalizowanie znacznika ASPX lub kodu. pliki zasobów oddzielne są wymagane dla nich.

 Po utworzeniu funkcję pliki zasobów, należy dodać przetłumaczone ciągi do nich. Dostęp do zlokalizowanych ciągów za pomocą wyrażenia w następującym formacie:

```aspx-csharp
$Resources:String ID
```

 Funkcja zasobów w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawsze o nazwie zasobów. Wybranie języka innego niż język niezmienny, następnie kultury [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] jest dodawany do nazwy pliku zasobu. Na przykład jeśli dodasz pliku zasobów funkcji języka niezmienną (ustawienie domyślne), jest nazywana Resources.resx. Jeśli dodasz zasobów funkcji specyficzne dla języka, wybierając kultury japoński (Japonia), plik jest nazywany Resources.ja JP.resx. Nazwy plików zasobów funkcji są przypisywane automatycznie i nie można zmienić.

 Zakres funkcji zasobów jest lokalny dla funkcji, które są dodawane do. Aby utworzyć zasoby, które mogą być używane przez dowolnego pliku funkcji lub element w rozwiązaniu, dodać **globalnego pliku zasobów** elementu projektu zamiast pliku zasobu funkcji. **Globalnego pliku zasobów** elementu projektu znajduje się w **2010** folder **SharePoint** w **Dodaj nowy element** okno dialogowe. Pliki zasobów globalnych wdrażania w folderze \Resources folderu głównego programu SharePoint.

### <a name="localizing-aspx-page-markup"></a>Lokalizowanie znacznika ASPX strony
 Do zlokalizowania [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stron, Dodaj trzy elementy projektu pliku zasobów do projektu: jeden dla języka angielskiego, jeden na język niemiecki i jeden dla języka japońskiego. Jeśli nie masz lokalizowanie kodu oprócz kod znaczników, zamiast tego można dodać pliki zasoby globalne.

 Podaj nazwę pliku zasobów języka domyślnego. Nadaj plików zlokalizowanych zasobów taką samą nazwę, dołączony kultury specyficzny dla języka [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Na przykład MyAppResources.de-DE.resx na język niemiecki i MyAppResources.ja-JP.resx dla języka japońskiego.

 Ustaw **typu wdrożenia** właściwości każdego pliku zasobu do **AppGlobalResource**. Powoduje to pliki zasobów do wdrożenia w folderze App_GlobalResources, gdy są dostępne dla wszystkich strony ASPX i kontrolki w rozwiązaniu. W folderze App_GlobalResources znajduje się w C:\inetpub\wwwroot\wss\VirtualDirectories\\< numer portu\>\App_GlobalResources.

> [!NOTE]
>  Pliki zasobów — globalne używane, przenieś je do folderu elementu projektu, aby włączyć właściwości typu wdrożenia i inne właściwości specyficzne dla programu SharePoint.

 Pliki zasobów znacznika ASPX mogą służyć do zlokalizowania kodu. Jeśli używane są zasoby do zlokalizowania kodu oprócz znacznika ASPX, pozostaw Akcja kompilacji właściwości ustawienie każdego pliku jako osadzonego zasobu powoduje zasobu do kompiluje się do zestawu satelickiego. Jednak jeśli używane są pliki zasobów tylko do zlokalizowania znaczników, opcjonalnie można zmienić Akcja kompilacji do zawartości, aby zapobiec kompilowany do zestawu aplikacji głównej pliku.

 Zastąp wszystkie ciągi ustalony właściwości w znaczniku strony i kontrolki ASPX wyrażenia w następującym formacie:

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Na przykład:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 ASPX jako tekst można użyć w wyrażeniu w następującym formacie:

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Na przykład:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 Aby uzyskać więcej informacji, zobacz [porady: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md).

### <a name="localizing-code"></a>Lokalizacja kodu
 Oprócz lokalizowanie funkcji ciągów i [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] znaczników, masz również do zlokalizowania ciągi komunikatów i ciągów błędów, które są widoczne w kodzie rozwiązania. Zlokalizowane informacyjne i komunikaty o błędach są zawarte w zestawy satelickie. Zestawy satelickie zawierają ciągi, które są widoczne dla użytkowników, takich jak [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] wyjątki, takich jak wiadomości tekstowe i danych wyjściowych.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wykorzystuje standardowe model gwiazdy .NET Framework. Koncentrator lub zestawu głównego programu zawiera zasoby język domyślny. Partnerzy lub zestawy satelickie zawierają zasoby specyficzne dla języka. Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie zasobów](http://go.microsoft.com/fwlink/?LinkId=179280). Zestawy satelickie są kompilowane z plików zasobów (resx). Po dodaniu plików źródłowych określonego języka do projektu i pakietu rozwiązania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kompiluje pliki zasobów do zestawów satelickich o nazwie *Nazwa projektu*. resources.dll.

 Podobnie jak w przypadku znacznika ASPX lokalizowanie kodu aplikacji programu SharePoint, dodając oddzielny plik zasobów — elementy projektu do projektu. jeden język domyślny i jeden dla każdego zlokalizowanego języka. Jednakże jak wspomniano wcześniej, jeśli masz już plików zasobów dla lokalizowanie znacznika ASPX, można użyć ponownie je dla Lokalizacja kodu. Jeśli musisz utworzyć pliki zasobów, nadaj nazwę wybraną dołączany z rozszerzeniem .resx pliku zasobów języka domyślnego. Nazwy plików zlokalizowanych zasobów takiej samej nazwie dołączony kultury specyficzny dla języka [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Ustaw dla właściwości Build Action każdego pliku zasobu osadzonego zasobu, aby włączyć tworzenie zestawów satelickich zasobów.

 Aby utworzyć zestawy satelickie, skompiluj projekt, a następnie dodać pliki jako dodatkowe zestawy za pomocą **zaawansowane** karcie **projektanta pakietów**. Podczas dodawania zestawy, dołączy kultury [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] folderu na ścieżkę lokalizacji, takich jak de-DE\\*nazwy elementu projektu*. resources.dll. Umożliwia to pakiet zawierający pliki, które mają taką samą nazwę.

 W kodzie, Zamień ustalony ciągi wywołań <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metodę przy użyciu następującej składni:

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 Aby uzyskać więcej informacji, zobacz [porady: Lokalizowanie kodu](../sharepoint/how-to-localize-code.md).

#### <a name="web-part-code-localization"></a>Lokalizacja kodu części sieci Web
 Części sieci Web obejmują funkcja edytora właściwości niestandardowej, która zawiera atrybuty kodu, korzystających z wpisaną na stałe ciągów, takich jak WebDisplayName, kategorii i WebDescription. Aby zastąpić ciąg wartości tych atrybutów, Utwórz oddzielne klasy, która pochodzi z klasy atrybutów. W tych klas ustaw właściwość ten atrybut. Właściwość atrybutu zależy od klasy podstawowej. Na przykład właściwość atrybutu WebDisplayName jest DisplayNameValue i właściwości atrybutu WebDescription jest DescriptionValue.

 W klasie pochodnej identyfikator ciągu odwołania z pliku zasobu oraz obiektu ResourceManager można pobrać zlokalizowaną wartość identyfikatora ciągu. Zwraca tę wartość do atrybutu edytora właściwości.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md)
- [Instrukcje: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Instrukcje: Lokalizowanie kodu](../sharepoint/how-to-localize-code.md)
- [Instrukcje: Dodawanie pliku zasobu](../sharepoint/how-to-add-a-resource-file.md)
- [Instrukcje: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)