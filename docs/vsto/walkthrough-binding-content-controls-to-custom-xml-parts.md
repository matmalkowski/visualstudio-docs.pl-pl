---
title: "Wskazówki: Powiązywanie kontrolek zawartości do niestandardowych części XML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1a8c8eff138e2c736750040dc896e610975c25ab
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-binding-content-controls-to-custom-xml-parts"></a>Wskazówki: powiązywanie kontrolek zawartości do niestandardowych części XML
  W tym przewodniku pokazano, jak można powiązać formantów zawartości w dostosowaniu poziomie dokumentu dla programu Word do danych XML, który jest przechowywany w dokumencie.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word umożliwia przechowywanie danych XML o nazwie *niestandardowe elementy XML*, w dokumencie. Można kontrolować wyświetlania tych danych przez powiązanie formantów zawartości do elementów z niestandardowym elementem XML. Przykładowy dokument w tym przewodniku Wyświetla informacje dotyczące pracowników, który jest przechowywany w niestandardowym elementem XML. Po otwarciu dokumentu formantów zawartości Wyświetl wartości elementów XML. Wszelkie zmiany wprowadzone w tekście formantów zawartości są zapisywane w niestandardowym elementem XML.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie formantów zawartości do dokumentu programu Word w projektach na poziomie dokumentu w czasie projektowania.  
  
-   Tworzenie pliku danych XML i schemat XML, definiujący elementy, które można powiązać z formantami zawartości.  
  
-   Dołączanie schematu XML do dokumentów w czasie projektowania.  
  
-   Dodawanie zawartości pliku XML z niestandardowym elementem XML w dokumencie w czasie wykonywania.  
  
-   Powiązanie formantów zawartości do elementów w niestandardowym elementem XML.  
  
-   Powiązanie <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do zestawu wartości, które są zdefiniowane w schemacie XML.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Word.  
  
## <a name="creating-a-new-word-document-project"></a>Tworzenie nowego projektu dokument programu Word  
 Utwórz dokument programu Word, która będzie używana w tym przewodnikiem.  
  
#### <a name="to-create-a-new-word-document-project"></a>Aby utworzyć nowy projekt dokument programu Word  
  
1.  Tworzenie projektu dokument programu Word o nazwie **EmployeeControls**. Utwórz nowy dokument dla rozwiązania. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]zostanie otwarty nowy dokument programu Word w Projektancie i dodaje **EmployeeControls** projektu do **Eksploratora rozwiązań**.  
  
## <a name="adding-content-controls-to-the-document"></a>Dodawanie formantów zawartości do dokumentu  
 Utwórz tabelę, która zawiera trzy różne typy formantów zawartości, gdy użytkownik umożliwia wyświetlenie i edytowanie informacji na temat pracownika.  
  
#### <a name="to-add-content-controls-to-the-document"></a>Do dodawania formantów zawartości do dokumentu  
  
1.  W dokumencie programu Word, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, na Wstążce wybierz **Wstaw** kartę.  
  
2.  W **tabel** grupy, wybierz **tabeli**i wstawić tabelę z kolumnami 2 i 3 wiersze.  
  
3.  Wpisz tekst w pierwszej kolumnie, dzięki czemu jest on podobny następujące kolumny:  
  
    ||  
    |-|  
    |**Nazwa pracownika**|  
    |**Data zatrudnienia**|  
    |**Tytuł**|  
  
4.  W drugiej kolumnie tabeli, wybierz pierwszy wiersz (obok **nazwa pracownika**).  
  
5.  Na Wstążce wybierz **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, należy go najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  W **formanty** grupy, wybierz **tekst** przycisk ![PlainTextContentControl —](../vsto/media/plaintextcontrol.gif "PlainTextContentControl —") można dodać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>do pierwszej komórki.  
  
7.  W drugiej kolumnie tabeli, wybierz pozycję drugiego wiersza (obok **Data zatrudnienia**).  
  
8.  W **formanty** grupy, wybierz **wyboru daty** przycisk ![DatePickerContentControl —](../vsto/media/datepicker.gif "DatePickerContentControl —") można dodać <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do drugiej komórki.  
  
9. W drugiej kolumnie tabeli, wybierz trzeciego wiersza (obok **tytuł**).  
  
10. W **formanty** grupy, wybierz **listy rozwijanej** przycisk ![DropDownListContentControl —](../vsto/media/dropdownlist.gif "DropDownListContentControl —") do dodania <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do ostatniej komórki.  
  
 To cały interfejs użytkownika dla tego projektu. Po uruchomieniu projektu można teraz, wpisz tekst w pierwszym wierszu i wybierz datę w drugim wierszu. Następnym krokiem jest, aby dołączyć dane, które mają być wyświetlane w dokumencie w pliku XML.  
  
## <a name="creating-the-xml-data-file"></a>Tworzenie pliku danych XML  
 Zazwyczaj uzyska dane XML mają być przechowywane w niestandardowym elementem XML ze źródła zewnętrznego, takiego jak plik lub bazy danych. W tym przewodniku należy utworzyć plik XML, który zawiera dane dotyczące pracowników, oznaczone przez elementy powiązane z formantami zawartości w dokumencie. Aby udostępnić dane w czasie wykonywania, Osadź plik XML jako zasób w zestawie dostosowania.  
  
#### <a name="to-create-the-data-file"></a>Aby utworzyć plik danych  
  
1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
2.  W **szablony** okienku wybierz **pliku XML**.  
  
3.  Nadaj nazwę plikowi **employees.xml**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     **Employees.xml** plik zostanie otwarty w edytorze kodu.  
  
4.  Zastąp zawartość **employees.xml** pliku z następującym tekstem.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  W **Eksploratora rozwiązań**, wybierz **employees.xml** pliku.  
  
6.  W **właściwości** wybierz **Akcja kompilacji** właściwości, a następnie zmień wartość na **osadzonego zasobu**.  
  
     Ten krok plik XML są osadzony jako zasób w zestawie podczas kompilowania projektu. Dzięki temu można uzyskać dostęp do zawartości pliku XML w czasie wykonywania.  
  
## <a name="creating-an-xml-schema"></a>Tworzenie schematu XML  
 Jeśli chcesz powiązać formant zawartości do pojedynczego elementu w niestandardowym elementem XML, nie trzeba użyć schematu XML. Jednak aby powiązać <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> zbiór wartości, należy utworzyć schemat XML, która weryfikuje pliku danych XML, który został utworzony wcześniej. Schemat XML definiuje możliwe wartości `title` elementu. Zostanie powiązany <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do tego elementu w dalszej części tego przewodnika.  
  
#### <a name="to-create-an-xml-schema"></a>Aby utworzyć schematu XML  
  
1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
2.  W **szablony** okienku wybierz **schematu XML**.  
  
3.  Nazwa schematu **employees.xsd** i wybierz polecenie **Dodaj** przycisku.  
  
     Zostanie otwarty projektant schematu.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **employees.xsd**, a następnie wybierz pozycję **kod widoku**.  
  
5.  Zastąp zawartość **employees.xsd** pliku z następującego schematu.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"   
        targetNamespace="http://schemas.microsoft.com/vsto/samples"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema"  
        elementFormDefault="qualified">  
      <xs:element name="employees" type="EmployeesType"></xs:element>  
      <xs:complexType name="EmployeesType">  
        <xs:all>  
          <xs:element name="employee" type="EmployeeType"/>  
        </xs:all>  
      </xs:complexType>  
      <xs:complexType name="EmployeeType">  
        <xs:sequence>  
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>  
        </xs:sequence>  
      </xs:complexType>  
      <xs:simpleType name="TitleType">  
        <xs:restriction base="xs:string">  
          <xs:enumeration value ="Engineer"/>  
          <xs:enumeration value ="Designer"/>  
          <xs:enumeration value ="Manager"/>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:schema>  
    ```  
  
6.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** Aby zapisać zmiany, aby **employees.xml** i **employees.xsd** plików.  
  
## <a name="attaching-the-xml-schema-to-the-document"></a>Dołączanie schematu XML do dokumentu  
 Należy dołączyć schematu XML do dokumentu, aby powiązać <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> prawidłowe wartości z `title` elementu.  
  
#### <a name="to-attach-the-xml-schema-to-the-document-includeword15shortvstoincludesword-15-short-mdmd"></a>Aby dołączyć do dokumentu schematu XML ([!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])  
  
1.  Aktywuj **EmployeeControls.docx** w projektancie.  
  
2.  Na Wstążce wybierz **Developer** karcie, a następnie wybierz pozycję **Add-Ins** przycisku.  
  
3.  W **szablony i dodatki** oknie dialogowym wybierz **schematu XML** karcie, a następnie wybierz pozycję **Dodaj schemat** przycisku.  
  
4.  Przejdź do **employees.xsd** schemat został utworzony wcześniej, który znajduje się w katalogu projektu, a następnie wybierz **Otwórz** przycisku.  
  
5.  Wybierz **OK** przycisk **schemat ustawień** okno dialogowe.  
  
6.  Wybierz **OK** przycisk, aby zamknąć **szablony i dodatki** okno dialogowe.  
  
#### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Aby dołączyć schematu XML do dokumentu (Word 2010)  
  
1.  Aktywuj **EmployeeControls.docx** w projektancie.  
  
2.  Na Wstążce wybierz **Developer** kartę.  
  
3.  W **XML** grupy, wybierz **schematu** przycisku.  
  
4.  W **szablony i dodatki** oknie dialogowym wybierz **schematu XML** karcie, a następnie wybierz pozycję **Dodaj schemat** przycisku.  
  
5.  Przejdź do **employees.xsd** schemat utworzony wcześniej, który znajduje się w katalogu projektu, a następnie wybierz pozycję **Otwórz** przycisku.  
  
6.  Wybierz **OK** przycisk **schemat ustawień** okno dialogowe.  
  
7.  Wybierz **OK** przycisk, aby zamknąć **szablony i dodatki** okno dialogowe.  
  
     **Struktury XML** otwiera w okienku zadań.  
  
8.  Zamknij **struktury XML** okienka zadań.  
  
## <a name="adding-a-custom-xml-part-to-the-document"></a>Dodawanie części niestandardowy plik XML do dokumentu  
 Aby można powiązać formantów zawartości do elementów w pliku XML, należy dodać zawartość pliku XML nowe niestandardowym elementem XML w dokumencie.  
  
#### <a name="to-add-a-custom-xml-part-to-the-document"></a>Aby dodać z niestandardowym elementem XML do dokumentu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ThisDocument.cs** lub **ThisDocument.vb**, a następnie wybierz pozycję **kod widoku**.  
  
2.  Dodaj następujące deklaracje `ThisDocument` klasy. Ten kod deklaruje kilka obiektów, które będą używane w celu dodania niestandardowych części XML do dokumentu.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]  
  
3.  Dodaj następującą metodę do `ThisDocument` klasy. Ta metoda pobiera zawartość pliku danych XML, który jest osadzony jako zasób w zestawie i zwraca zawartość jako ciąg XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]  
  
4.  Dodaj następującą metodę do `ThisDocument` klasy. `AddCustomXmlPart` Metoda tworzy nowy niestandardowym elementem XML, który zawiera ciąg XML, który jest przekazywany do metody.  
  
     Aby upewnić się, że niestandardowym elementem XML jest tworzony tylko raz, ta metoda tworzy niestandardowy plik XML części tylko wtedy, gdy z niestandardowym elementem XML za pomocą dopasowywania identyfikatora GUID nie istnieje w dokumencie. Ta metoda jest wywoływana, po raz pierwszy zapisuje wartość <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> właściwości `employeeXMLPartID` ciągu. Wartość `employeeXMLPartID` ciągu jest utrwalona w dokumencie, ponieważ zostało zadeklarowane przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]  
  
## <a name="binding-the-content-controls-to-elements-in-the-custom-xml-part"></a>Powiązanie formantów zawartości do elementów w ramach niestandardowy plik XML  
 Powiązanie każdego formantu zawartości elementu w niestandardowym elementem XML przy użyciu **XMLMapping** właściwości każdego formantu zawartości.  
  
#### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Powiązanie formantów zawartości do elementów w niestandardowym elementem XML  
  
1.  Dodaj następującą metodę do `ThisDocument` klasy. Ta metoda wiąże każdego formantu zawartości elementu w niestandardowym elementem XML i ustawia format wyświetlania daty <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]  
  
## <a name="running-your-code-when-the-document-is-opened"></a>Uruchamianie swój kod gdy dokument jest otwarty.  
 Tworzenie niestandardowych części XML i powiązanie formantów niestandardowych do danych, po otwarciu dokumentu.  
  
#### <a name="to-run-your-code-when-the-document-is-opened"></a>Aby uruchomić kod po otwarciu dokumentu  
  
1.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy. Ten kod pobiera ciąg XML z **employees.xml** plik, dodaje nowe niestandardowym elementem XML w dokumencie ciągu XML i wiąże formantów zawartości do elementów w niestandardowym elementem XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]  
  
## <a name="testing-the-project"></a>Testowanie projektu  
 Po otwarciu dokumentu formantów zawartości wyświetlane dane z elementów w niestandardowym elementem XML. Możesz kliknąć <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> można wybrać jedną z trzech prawidłowymi wartościami dla `title` element, który zdefiniowano w **employees.xsd** pliku. Po zmodyfikowaniu dane w jednym z formantów zawartości nowe wartości są zapisywane w niestandardowym elementem XML w dokumencie.  
  
#### <a name="to-test-the-content-controls"></a>Aby przetestować formanty zawartości  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Sprawdź, czy tabela w dokumencie przypomina poniższej tabeli. Każdy z ciągów w drugiej kolumnie są uzyskiwane z elementu w niestandardowym elementem XML w dokumencie.  
  
    |||  
    |-|-|  
    |**Nazwa pracownika**|**Karina Leal**|  
    |**Data zatrudnienia**|**1 kwietnia 1999 r.**|  
    |**Tytuł**|**Menedżer**|  
  
3.  Wybierz komórkę z prawej strony **nazwa pracownika** komórki, a następnie wpisz inną nazwę.  
  
4.  Wybierz komórkę z prawej strony **Data zatrudnienia** komórek i wybierz inną datę w formancie.  
  
5.  Wybierz komórkę z prawej strony **tytuł** komórki, a następnie wybierz nowy element z listy rozwijanej.  
  
6.  Zapisz i zamknij dokument.  
  
7.  W Eksploratorze plików otwórz folder \bin\Debug znajdujące się w lokalizacji projektu.  
  
8.  Otwórz menu skrótów **EmployeeControls.docx** , a następnie wybierz **zmienić**.  
  
9. Nadaj nazwę plikowi **EmployeeControls.docx.zip**.  
  
     **EmployeeControls.docx** dokumentu jest zapisywany w formacie Open XML. Zmieniając tego dokumentu z rozszerzeniem nazwy pliku zip, można sprawdzić zawartość dokumentu. Aby uzyskać więcej informacji na temat Open XML, zobacz artykuł techniczny [wprowadzenie (2007) formaty Office Open XML pliku](http://msdn.microsoft.com/en-us/96018532-f62c-4da7-bbff-16b96a483fbf).  
  
10. Otwórz **EmployeeControls.docx.zip** pliku.  
  
11. Otwórz **customXml** folderu.  
  
12. Otwórz menu skrótów **item2.xml** , a następnie wybierz **Otwórz**.  
  
     Ten plik zawiera niestandardowym elementem XML, który został dodany do dokumentu.  
  
13. Sprawdź, czy `name`, `hireDate`, i `title` elementy zawierają nowe wartości, które zostały wprowadzone do formantów zawartości w dokumencie.  
  
14. Zamknij **item2.xml** pliku.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz można dowiedzieć się więcej o sposobie używania formantów zawartości z tych tematów:  
  
-   Aby utworzyć szablon, należy użyć wszystkich dostępnych formantów zawartości. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie szablonu za pomocą formantów zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Modyfikowanie danych w niestandardowe elementy XML, gdy dokument zostanie zamknięty. Przy następnym otwarciu dokumentu, formantów zawartości, które są powiązane elementy XML będą wyświetlane nowe dane.  
  
-   Użyj formantów zawartości do ochrony części dokumentu. Aby uzyskać więcej informacji, zobacz [porady: ochrona części dokumentów za pomocą formantów zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Formanty zawartości](../vsto/content-controls.md)   
 [Porady: dodawanie formantów zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Porady: ochrona części dokumentów za pomocą formantów zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  