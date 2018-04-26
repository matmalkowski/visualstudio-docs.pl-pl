---
title: Powiązanie formantów WPF z danymi w Visual Studio — część 1 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7674656c9a4995b853753e12b19fd71bf77a3c9f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Powiązanie formantów WPF z danymi w Visual Studio
Można wyświetlić dane dla użytkowników aplikacji przez wiązanie danych do [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] kontrolki. Aby utworzyć takie formanty powiązane z danymi, można przeciągnij elementy z **źródeł danych** okna na [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. W tym temacie opisano niektóre z najbardziej typowych zadań, narzędzia i klasy, które umożliwia tworzenie powiązanych z danymi [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] aplikacji.

 Aby uzyskać ogólne informacje o sposobie tworzenia formantów powiązanych z danymi w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], zobacz [powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] dane powiązanie, zobacz [omówienie powiązania danych](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Zadania związane z powiązywanie kontrolek WPF z danymi
 W poniższej tabeli wymieniono zadania, które można wykonywać przez przeciąganie elementów z **źródeł danych** okna [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].

|Zadanie|Więcej informacji|
|----------|----------------------|
|Utwórz nowe formanty związane z danymi.<br /><br /> Powiąż istniejące formant z danymi.|[Powiązywanie kontrolek WPF z zestawem danych](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Utwórz formant, które wyświetlają pokrewne dane w relacji nadrzędny podrzędny: kiedy użytkownik wybierze nadrzędny rekord danych w jednym formancie, inny formant wyświetli powiązane dane podrzędne dla wybranego rekordu.|[Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Utwórz *tabeli odnośników* wyświetlający informacje z jednej tabeli na podstawie wartości pola klucza obcego w innej tabeli.|[Tworzenie tabel wyszukiwania w aplikacjach WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Powiąż formant z obrazem w bazie danych.|[Powiązywanie kontrolek z obrazami z bazy danych](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Nieprawidłowa miejsc docelowych
 Możesz przeciągnąć elementów w **źródeł danych** okna tylko prawidłowe miejsc docelowych w [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Istnieją dwa główne rodzaje z prawidłowych miejsc upuszczania: kontenery i formanty. Kontener jest element interfejsu użytkownika, który zwykle zawiera formanty. Na przykład siatka jest kontenerem i podobnie okno.

## <a name="generated-xaml-and-code"></a>Wygenerowany XAML i kodem
 Gdy przeciągnąć element z **źródeł danych** okna [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] definiuje nowy formant powiązany z danymi (lub wiąże istniejącego formantu źródła danych). Dla niektórych źródeł danych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] również generuje kod w pliku związanym z kodem, który wypełnia źródła danych przy użyciu danych.

 W poniższej tabeli wymieniono [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] i kod, który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generuje dla każdego typu źródła danych w **źródeł danych** okna.

|Źródło danych|Generowanie pliku XAML, która wiąże formant ze źródłem danych|Generowanie kodu, który wypełnia źródło danych danymi|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Zestaw danych|Tak|Tak|
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Tak|Tak|
|Usługa|Tak|Nie|
|Obiekt|Tak|Nie|

### <a name="datasets"></a>Zestawy danych
 Przeciągnięcie tabeli lub kolumny z **źródeł danych** okna do projektanta, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] który wykonuje następujące czynności:

-   Dodaje zestaw danych i nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera przeciągnąć element. <xref:System.Windows.Data.CollectionViewSource> Jest obiekt, który może służyć do nawigacji i wyświetlania danych w zestawie danych.

-   Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Przeciągnięcie elementu do kontenera XAML tworzy kontrolkę, które zostały wybrane do przeciąganego elementu i do elementu tworzy ona powiązanie formantu. Formant nie zostanie utworzony w nowej <xref:System.Windows.Controls.Grid>.

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do pliku CodeBehind również wprowadza następujące zmiany:

-   Tworzy <xref:System.Windows.FrameworkElement.Loaded> programu obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] element zawierający formant. Program obsługi zdarzeń wypełnia tabelę z danymi, pobiera <xref:System.Windows.Data.CollectionViewSource> z kontenera zasobów, a następnie sprawia, że pierwsze dane elementu bieżącego elementu. Jeśli <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń już istnieje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dodaje ten kod do istniejącego programu obsługi zdarzeń.

### <a name="entity-data-models"></a>Modeli danych jednostki
 Przeciągnięcie jednostki lub właściwości jednostki z **źródeł danych** okna do projektanta, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] który wykonuje następujące czynności:

-   Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera przeciągnąć element. <xref:System.Windows.Data.CollectionViewSource> Jest obiekt, który może służyć do nawigowania i wyświetlić dane w jednostce.

-   Tworzy wiązania danych dla formantu. Jeśli przeciągnij element do istniejącego formantu w Projektancie [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] wiąże formantu do elementu. Przeciągnięcie elementu do kontenera, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] tworzy kontrolkę, która została wybrana dla przeciąganego elementu i do elementu tworzy ona powiązanie formantu. Formant nie zostanie utworzony w nowej <xref:System.Windows.Controls.Grid>.

Visual Studio wprowadza następujące zmiany w pliku powiązanym z kodem:

-   Dodaje nową metodę, która zwraca kwerendy dla elementu, który został przeciągnięty do projektanta (lub elementu zawierającego właściwość, która została przeciągnięta do projektanta). Nowa metoda ma nazwę Get*EntityName*kwerendy, gdzie *EntityName* to nazwa jednostki.

-   Tworzy <xref:System.Windows.FrameworkElement.Loaded> programu obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] element zawierający formant. Pobierz wywołuje program obsługi zdarzeń*EntityName*metody, aby wypełnić jednostka danych, pobiera zapytania <xref:System.Windows.Data.CollectionViewSource> z kontenera zasobów, a następnie sprawia, że pierwsze dane elementu bieżącego elementu. Jeśli <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń już istnieje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dodaje ten kod do istniejącego programu obsługi zdarzeń.

### <a name="services"></a>Usługi
 Przeciągnięcie obiektu usługi lub właściwość z **źródeł danych** okna do projektanta, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] tworzy kontrolkę powiązanych z danymi (lub wiąże formant do obiektu lub właściwości). Jednak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie generuje kod, który wypełnia obiekt usługi Serwer proxy przy użyciu danych. Musisz napisać ten kod samodzielnie. Na przykład, który pokazuje, jak to zrobić, zobacz [powiązania WPF kontrolki do usługi danych WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Visual Studio generuje plik XAML, który wykonuje następujące czynności:

-   Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> zasobów kontenera, w którym możesz przeciągnąć element. <xref:System.Windows.Data.CollectionViewSource> Jest obiekt, który może służyć do nawigowania i wyświetlić dane w obiekcie, który jest zwracany przez usługę.

-   Tworzy wiązania danych dla formantu. Jeśli przeciągnij element do istniejącego formantu w Projektancie [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] wiąże formantu do elementu. Przeciągnięcie elementu do kontenera, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] tworzy kontrolkę, która została wybrana dla przeciąganego elementu i do elementu tworzy ona powiązanie formantu. Formant nie zostanie utworzony w nowej <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Obiekty
 Podczas przeciągania obiektu lub właściwości z **źródeł danych** okna do projektanta, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] tworzy kontrolkę powiązanych z danymi (lub wiąże formant do obiektu lub właściwości). Jednak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie generuje kod, aby wypełnić obiektu danych. Musisz napisać ten kod samodzielnie.

> [!NOTE]
>  Niestandardowe klasy musi być publiczny i domyślnie ma konstruktora bez parametrów. One can'tbe zagnieżdżone klasy, które mają "kropkę" w ich składni. Aby uzyskać więcej informacji, zobacz [XAML oraz klas niestandardowych dla WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] który wykonuje następujące czynności:

-   Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> zasobów kontenera, w którym możesz przeciągnąć element. <xref:System.Windows.Data.CollectionViewSource> To obiekt, który może służyć do nawigowania i wyświetlić dane w obiekcie.

-   Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Przeciągnięcie elementu do kontenera XAML tworzy kontrolkę, które zostały wybrane do przeciąganego elementu i do elementu tworzy ona powiązanie formantu. Formant nie zostanie utworzony w nowej <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Zobacz także

- [Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)