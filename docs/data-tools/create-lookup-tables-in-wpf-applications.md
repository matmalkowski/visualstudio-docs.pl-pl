---
title: Tworzenie tabel wyszukiwania w aplikacjach WPF
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fa14d9e2327288729bd97dd8a656f894e9fcef5d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757139"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Tworzenie tabel wyszukiwania w aplikacjach WPF
Termin *tabeli odnośników* (nazywane również *powiązania wyszukiwania*) opisano formant, który wyświetla informacje dotyczące jednego danych tabeli na podstawie wartości pola klucza obcego w innej tabeli. Można utworzyć tabeli odnośników przeciągając węzeł główny tabeli nadrzędnej lub obiekt w **źródeł danych** okna na formant, który jest już powiązany z kolumną lub właściwości w tabeli podrzędnych.

Na przykład rozważmy tabelę `Orders` w bazie danych sprzedaży. Każdy rekord w `Orders` tabela zawiera `CustomerID` wskazujące, którego odbiorcy umieszczone kolejności. `CustomerID` Jest kluczem obcym wskazujący rekord klienta w `Customers` tabeli. Po wyświetleniu listę zleceń `Orders` tabeli, może zajść potrzeba wyświetlana nazwa rzeczywista klienta zamiast `CustomerID`. Ponieważ nazwy klienta znajduje się w `Customers` tabeli, należy utworzyć tabeli odnośników, aby wyświetlić nazwy klienta. Używa tabeli odnośników `CustomerID` wartość w `Orders` rekordów do nawigacji relacji i zwracać nazwy klienta.

## <a name="to-create-a-lookup-table"></a>Można utworzyć tabeli odnośników

1.  Dodaj jeden z następujących typów źródeł danych z powiązanych danych do projektu:

    -   Zestaw danych lub modelu Entity Data Model.

    -   Usługi danych WCF, usługi WCF lub usługi sieci Web. Aby uzyskać więcej informacji, zobacz [porady: łączenie z danymi w usłudze](../data-tools/how-to-connect-to-data-in-a-service.md).

    -   Obiekty. Aby uzyskać więcej informacji, zobacz [powiązanie do obiektów w programie Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    >  Przed utworzeniem tabeli odnośników dwóch tabel powiązanych lub obiektów musi istnieć jako źródła danych dla projektu.

2.  Otwórz **projektanta WPF**i upewnij się, że projektant zawiera kontener, który jest prawidłowy miejsca docelowego dla elementów w **źródeł danych** okna.

     Aby uzyskać więcej informacji na temat prawidłowy miejsc docelowych, zobacz [kontrolki powiązania WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych** otworzyć **źródeł danych** okna.

4.  Rozwiń węzły w **źródeł danych** okna, aż zobaczysz tabeli nadrzędnej lub obiektu i podrzędnych tabeli lub obiektu.

    > [!NOTE]
    >  Podrzędnych tabeli lub obiektu jest węzeł, który jest wyświetlany jako rozwijania węzeł podrzędny węzła nadrzędnego tabeli lub obiektu.

5.  Kliknij menu rozwijane dla węzła podrzędnego, a następnie wybierz **szczegóły**.

6.  Rozwiń węzeł podrzędny.

7.  W obszarze węzła podrzędnego kliknij menu rozwijane dla elementu, który dotyczy danych nadrzędnym a podrzędnym. (W powyższym przykładzie jest to **CustomerID** węzła.) Wybierz jedną z następujących typów formantów, które obsługują powiązanie wyszukiwania:

    -   **ComboBox**

    -   **ListBox**

    -   **ListView**

        > [!NOTE]
        >  Jeśli **ListBox** lub **ListView** formant nie jest wyświetlany na liście tych kontrolek można dodać do listy. Aby uzyskać informacje, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    -   Kontrolka niestandardowa, która jest pochodną <xref:System.Windows.Controls.Primitives.Selector>.

        > [!NOTE]
        >  Informacje o sposobie dodawania niestandardowych określa się na liście kontroli można wybrać dla elementów w **źródeł danych** okna, zobacz [dodawanie formantów niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8.  Przeciągnij węzeł podrzędny z **źródeł danych** okna na kontenera w Projektancie WPF. (W tym przykładzie jest węzeł podrzędny **zamówień** węzła.)

     Program Visual Studio generuje XAML, która tworzy nowe formanty powiązane z danymi dla poszczególnych elementów, które możesz przeciągnąć. XAML dodaje również nowe <xref:System.Windows.Data.CollectionViewSource> obiektu do zasobów obiektu docelowego upuszczania lub tabeli podrzędnej. Dla niektórych źródeł danych programu Visual Studio generuje kod, aby załadować dane do tabeli lub obiektu. Aby uzyskać więcej informacji, zobacz [kontrolki powiązania WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Przeciągnij węzeł nadrzędny z **źródeł danych** okna w formancie powiązanie wyszukiwania, który został utworzony wcześniej. (W tym przykładzie jest węzeł nadrzędny **klientów** węzła).

     Visual Studio ustawia niektóre właściwości formantu do konfigurowania wiązania wyszukiwania. W poniższej tabeli wymieniono właściwości, które modyfikuje Visual Studio. Jeśli to konieczne, możesz zmienić te właściwości w pliku XAML lub w **właściwości** okna.

    |Właściwość|Wyjaśnienie ustawienia|
    |--------------|----------------------------|
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Ta właściwość określa powiązania, który jest używany do pobierania danych, który jest wyświetlany w formancie lub kolekcji. Visual Studio ustawia tę właściwość na <xref:System.Windows.Data.CollectionViewSource> danych nadrzędnej przeciągnąć do formantu.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Ta właściwość określa ścieżkę elementu danych, który jest wyświetlany w formancie. Visual Studio ustawia tę właściwość na pierwszej kolumny lub właściwości w danych nadrzędnej po klucz podstawowy, który ma typ danych ciągu.<br /><br /> Jeśli chcesz wyświetlić innej kolumny lub właściwości w danych nadrzędnej, należy zmienić tej właściwości na ścieżkę inną właściwość.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio wiąże tej właściwości do kolumny lub właściwości danych podrzędne, które przeciągnąć do projektanta. Jest to klucz obcy danych nadrzędnej.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio ustawia tę właściwość na ścieżce kolumny lub właściwość danych podrzędne, które jest kluczem obcym danych nadrzędnej.|

## <a name="see-also"></a>Zobacz także

- [Powiązanie formantów WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md)
- [Wskazówki: Wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/display-related-data-in-wpf-applications.md)