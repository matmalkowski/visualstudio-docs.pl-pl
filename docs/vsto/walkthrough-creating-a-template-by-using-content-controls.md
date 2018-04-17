---
title: 'Wskazówki: Tworzenie szablonu za pomocą formantów zawartości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8c7f5026d4cbe8b7c38b8163ce00d893e1e406f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-template-by-using-content-controls"></a>Wskazówki: tworzenie szablonu za pomocą formantów zawartości
  Ten przewodnik przedstawia sposób tworzenia dostosowania poziomie dokumentu, który używa formantów zawartości do utworzenia zawartości strukturalnych i do ponownego użycia w szablonie programu Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word umożliwia tworzenie kolekcji części dokumentu wielokrotnego użytku, o nazwie *bloków konstrukcyjnych*. W tym przewodniku przedstawiono sposób tworzenia tabel jako bloków konstrukcyjnych. Każda tabela zawiera kilka formantów zawartości, które mogą zawierać różne typy zawartości, takich jak zwykły tekst lub daty. Jedną z tabel zawiera informacje dotyczące pracowników, a drugiej tabeli opinie klientów.  
  
 Po utworzeniu dokumentu z szablonu, można dodać tabel do dokumentu za pomocą kilku <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> obiekty, do których wyświetlania dostępnych bloków konstrukcyjnych w szablonie.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie tabel, które zawierają zawartość kontrolki w programie szablonu w czasie projektowania.  
  
-   Wypełnianie programowo formantu zawartości pola kombi i kontrolki zawartości listy rozwijanej.  
  
-   Uniemożliwianie użytkownikom edytowanie określonej tabeli.  
  
-   Dodawanie tabel do kolekcji bloków konstrukcyjnych szablonu.  
  
-   Tworzenie zawartości formantu, który wyświetla dostępne bloków konstrukcyjnych w szablonie.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Word.  
  
## <a name="creating-a-new-word-template-project"></a>Tworzenie nowego projektu szablon programu Word  
 Utwórz szablon programu Word, dzięki czemu użytkownicy mogą łatwo tworzyć własne kopie.  
  
#### <a name="to-create-a-new-word-template-project"></a>Aby utworzyć nowy projekt szablonu programu Word  
  
1.  Tworzenie projektu szablon programu Word o nazwie **MyBuildingBlockTemplate**. W kreatorze tworzenia nowego dokumentu w rozwiązaniu. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zostanie otwarty nowy szablon programu Word w Projektancie i dodaje **MyBuildingBlockTemplate** projektu do **Eksploratora rozwiązań**.  
  
## <a name="creating-the-employee-table"></a>Tworzenie tabeli pracowników  
 Utwórz tabelę, która zawiera cztery różne typy formantów zawartości, w którym użytkownik może wprowadzić informacje o pracownika.  
  
#### <a name="to-create-the-employee-table"></a>Aby utworzyć tabelę pracownika  
  
1.  W szablonie programu Word, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, na wstążce kliknij **Wstaw** kartę.  
  
2.  W **tabel** kliknij przycisk **tabeli**i wstawić tabelę z kolumnami 2 i 4 wiersze.  
  
3.  Wpisz tekst w pierwszej kolumnie, dzięki czemu jest on podobny następujące kolumny:  
  
    ||  
    |-|  
    |**Nazwa pracownika**|  
    |**Data zatrudnienia**|  
    |**Tytuł**|  
    |**Obraz**|  
  
4.  Kliknij w pierwszej komórki w drugiej kolumnie (obok **nazwa pracownika**).  
  
5.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, należy go najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  W **formanty** kliknij przycisk **tekst** przycisk ![PlainTextContentControl —](../vsto/media/plaintextcontrol.gif "PlainTextContentControl —") można dodać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>do pierwszej komórki.  
  
7.  Kliknij komórkę drugi w drugiej kolumnie (obok **Data zatrudnienia**).  
  
8.  W **formanty** kliknij przycisk **wyboru daty** przycisk ![DatePickerContentControl —](../vsto/media/datepicker.gif "DatePickerContentControl —") można dodać <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do drugiej komórki.  
  
9. Kliknij komórkę trzeci w drugiej kolumnie (obok **tytuł**).  
  
10. W **formanty** kliknij przycisk **pola kombi** przycisk ![comboboxcontentcontrol —](../vsto/media/combobox.gif "comboboxcontentcontrol —") można dodać <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>trzeci komórką.  
  
11. Kliknij przycisk ostatniej komórki w drugiej kolumnie (obok **obraz**).  
  
12. W **formanty** kliknij przycisk **formant zawartości obrazu** przycisk ![PictureContentControl —](../vsto/media/pictcontentcontrol.gif "PictureContentControl —") do dodania <xref:Microsoft.Office.Tools.Word.PictureContentControl> do ostatniej komórki.  
  
## <a name="creating-the-customer-feedback-table"></a>Tworzenie tabeli opinie klientów  
 Utwórz tabelę, która zawiera trzy różne typy formantów zawartości, w którym użytkownik może wprowadzić informacje o opinii klientów.  
  
#### <a name="to-create-the-customer-feedback-table"></a>Aby utworzyć tabelę opinie klientów  
  
1.  W szablonie programu Word kliknij wiersz po tabeli pracowników dodanego wcześniej, a następnie naciśnij klawisz ENTER, aby dodać nowy akapit.  
  
2.  Na wstążce kliknij **Wstaw** kartę.  
  
3.  W **tabel** kliknij przycisk **tabeli**i wstawić tabelę z kolumnami 2 i 3 wiersze.  
  
4.  Wpisz tekst w pierwszej kolumnie, dzięki czemu jest on podobny następujące kolumny:  
  
    ||  
    |-|  
    |**Nazwa klienta**|  
    |**Wskaźnik zadowolenia**|  
    |**Komentarze**|  
  
5.  Kliknij w pierwszej komórki drugiej kolumny (obok **nazwy klienta**).  
  
6.  Na wstążce kliknij **Developer** kartę.  
  
7.  W **formanty** kliknij przycisk **tekst** przycisk ![PlainTextContentControl —](../vsto/media/plaintextcontrol.gif "PlainTextContentControl —") można dodać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>do pierwszej komórki.  
  
8.  Kliknij komórkę drugi drugiej kolumny (obok **klasyfikacji zadowolenia**).  
  
9. W **formanty** kliknij przycisk **listy rozwijanej** przycisk ![DropDownListContentControl —](../vsto/media/dropdownlist.gif "DropDownListContentControl —") do dodania <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do drugiej komórki.  
  
10. Kliknij komórkę ostatniego drugiej kolumny (obok **komentarze**).  
  
11. W **formanty** kliknij przycisk **tekstu sformatowanego** przycisk ![RichTextContentControl —](../vsto/media/richtextcontrol.gif "RichTextContentControl —") można dodać <xref:Microsoft.Office.Tools.Word.RichTextContentControl>do ostatniej komórki.  
  
## <a name="populating-the-combo-box-and-drop-down-list-programmatically"></a>Pole kombi wypełnianie pola i listy rozwijanej liście programowo  
 Formanty zawartości można zainicjować w czasie projektowania, za pomocą **właściwości** okna w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Również można zainicjować w czasie wykonywania, dzięki czemu można ustawić ich stan początkowy dynamicznie. W ramach tego przewodnika, użyj kodu w celu wypełnienia wpisy w <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> i <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> w czasie wykonywania, aby mogli przeglądać, działanie tych obiektów.  
  
#### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Aby zmodyfikować programowo interfejsu użytkownika dla formantów zawartości  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument.cs** lub **ThisDocument.vb**, a następnie kliknij przycisk **kod widoku**.  
  
2.  Dodaj następujący kod do `ThisDocument` klasy. Ten kod deklaruje kilka obiektów, które będą używane w dalszej części tego przewodnika.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy. Ten kod dodaje wpisy do <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> i <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> w tabelach i ustawia tekst wyświetlany w każdym z tych kontrolek, zanim użytkownik edytuje je.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="preventing-users-from-editing-the-employee-table"></a>Uniemożliwianie użytkownikom edycji tabeli pracowników  
 Użyj <xref:Microsoft.Office.Tools.Word.GroupContentControl> obiekt zadeklarowano wcześniej, aby chronić tabeli pracowników. Po objęciu ochroną w tabeli, można nadal edytować formantów zawartości w tabeli. Jednak nie można edytować tekst w pierwszej kolumnie lub zmodyfikuj inne sposoby, takie jak dodawanie lub usuwanie wierszy i kolumn tabeli. Aby uzyskać więcej informacji o sposobie używania <xref:Microsoft.Office.Tools.Word.GroupContentControl> chronić części dokumentu, zobacz [formantów zawartości](../vsto/content-controls.md).  
  
#### <a name="to-prevent-users-from-editing-the-employee-table"></a>Aby uniemożliwić użytkownikom edytowanie tabeli pracowników  
  
1.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod uniemożliwia użytkownikom edytowanie tabeli pracowników przez umieszczenie w tabeli wewnątrz <xref:Microsoft.Office.Tools.Word.GroupContentControl> obiektu zgłoszonego wcześniej.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="adding-the-tables-to-the-building-block-collection"></a>Dodawanie tabel do kolekcji bloków konstrukcyjnych  
 Dodać tabele do kolekcji bloków konstrukcyjnych dokumentu w szablonie, dzięki czemu użytkownicy mogą wprowadzać tabel, które zostały utworzone do dokumentu. Aby uzyskać więcej informacji na temat moduły konstrukcyjne dokumentów, zobacz [formantów zawartości](../vsto/content-controls.md).  
  
#### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Aby dodać tabele do bloków konstrukcyjnych w szablonie  
  
1.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod dodaje nowe bloki konstrukcyjne, zawierających tabele do kolekcji Microsoft.Office.Interop.Word.BuildingBlockEntries, który zawiera wszystkie wielokrotnego użytku bloków konstrukcyjnych w szablonie. Nowe bloki są definiowane w nową kategorię o nazwie **pracownika oraz informacje o kliencie** i przypisano typu bloków konstrukcyjnych Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod usuwa tabel z szablonu. Tabele nie są już konieczne, ponieważ mają być dodane do galerii wielokrotnego użytku bloków konstrukcyjnych w szablonie. Kod najpierw umieszcza dokumentu w trybie projektowania tak, aby można go usunąć z tabeli pracowników chronionych.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="creating-a-content-control-that-displays-the-building-blocks"></a>Tworzenie zawartości formantu, który wyświetla bloki konstrukcyjne  
 Utwórz formant zawartości, która zapewnia dostęp do bloków konstrukcyjnych (tabele), które zostały utworzone wcześniej. Kliknięcie tego formantu, aby dodać tabele do dokumentu.  
  
#### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Aby utworzyć formant zawartości, który wyświetla bloki konstrukcyjne  
  
1.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod inicjuje <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> obiektu zgłoszonego wcześniej. <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> Wyświetla wszystkie bloki konstrukcyjne, które są zdefiniowane w kategorii **pracownika oraz informacje o kliencie** , które mają typ bloku konstrukcyjnego Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="testing-the-project"></a>Testowanie projektu  
 Użytkownicy mogą kliknąć formantów galerii bloków konstrukcyjnych w dokumencie, aby wstawić tabeli pracowników lub tabeli opinii klientów. Użytkownicy mogą wpisz lub wybierz odpowiedzi w formantach zawartości w obu tabel. Użytkownicy mogą modyfikować inne części tabeli opinie klientów, ale nie powinien być można modyfikować inne części tabeli pracowników.  
  
#### <a name="to-test-the-employee-table"></a>Aby przetestować tabeli pracowników  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Kliknij przycisk **wybierz pierwszym bloku konstrukcyjnego** do wyświetlenia pierwszego bloku konstrukcyjnego galerii zawartości formantu.  
  
3.  Kliknij strzałkę listy rozwijanej obok pola **niestandardowy galerii 1** nagłówka w formancie i wybierz **tabeli pracowników**.  
  
4.  Kliknij komórkę z prawej strony **nazwa pracownika** komórki, a następnie wpisz nazwę.  
  
     Sprawdź, czy można dodać tylko tekst do tej komórki. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> Umożliwia użytkownikom dodanie tylko tekst nie innych typów zawartości, takich jak grafik lub tabeli.  
  
5.  Kliknij komórkę z prawej strony **Data zatrudnienia** komórki, a następnie wybierz datę w formancie.  
  
6.  Kliknij komórkę z prawej strony **tytuł** komórki, a następnie wybierz jedno z tytułów zadania w polu kombi.  
  
     Opcjonalnie wpisz nazwę stanowisko, który nie jest na liście. Jest to możliwe, ponieważ <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> umożliwia użytkownikom, wybierz z listy wpisów lub wpisz własny wpisów.  
  
7.  Kliknij ikonę komórkę z prawej strony **obraz** komórki, a następnie przejdź do obrazu, aby go wyświetlić.  
  
8.  Spróbuj dodać wierszy lub kolumn do tabeli, a następnie spróbuj usunąć wiersze i kolumny z tabeli. Upewnij się, że nie można zmodyfikować tabeli. <xref:Microsoft.Office.Tools.Word.GroupContentControl> Uniemożliwia dokonaniem jakichkolwiek modyfikacji.  
  
#### <a name="to-test-the-customer-feedback-table"></a>Aby przetestować tabeli opinie klientów  
  
1.  Kliknij przycisk **Wybierz drugi bloku konstrukcyjnego** do wyświetlania drugi bloków konstrukcyjnych galerii zawartości formantu.  
  
2.  Kliknij strzałkę listy rozwijanej obok pola **niestandardowy galerii 1** nagłówka w formancie i wybierz **tabeli klienta**.  
  
3.  Kliknij komórkę z prawej strony **nazwy klienta** komórki, a następnie wpisz nazwę.  
  
4.  Kliknij komórkę z prawej strony **klasyfikacji zadowolenia** komórki, a następnie wybierz jedną z dostępnych opcji.  
  
     Upewnij się, że nie można wpisać własny tekst. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> Umożliwia użytkownikom tylko wybierz z listy wpisów.  
  
5.  Kliknij komórkę z prawej strony **komentarze** komórki, a następnie wpisz niektóre komentarze.  
  
     Opcjonalnie dodaj część zawartości innego niż tekstu, na przykład grafik lub osadzonej tabeli. Jest to możliwe, ponieważ <xref:Microsoft.Office.Tools.Word.RichTextContentControl> pozwala użytkownikom na dodawanie zawartości innego niż tekstu.  
  
6.  Sprawdź, można dodać wierszy lub kolumn w tabeli i że możesz usunąć wiersze i kolumny z tabeli. Jest to możliwe, ponieważ nie został zabezpieczony tabeli przy <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Zamknij szablon.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz można dowiedzieć się więcej o sposobie używania formantów zawartości z tego tematu:  
  
-   Powiązanie formantów zawartości do elementów XML o nazwie niestandardowe elementy XML, które są osadzone w dokumencie. Aby uzyskać więcej informacji, zobacz [wskazówki: wiązanie formantów zawartości do niestandardowych części XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Formanty zawartości](../vsto/content-controls.md)   
 [Porady: dodawanie formantów zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Porady: ochrona części dokumentów za pomocą formantów zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  