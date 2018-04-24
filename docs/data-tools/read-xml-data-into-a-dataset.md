---
title: Odczytywanie danych XML do zestawu danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c6c2ea2b46fcd05360e079dc84da9bfe807ff489
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="read-xml-data-into-a-dataset"></a>Odczytywanie danych XML do zestawu danych
ADO.NET udostępnia prosty metody pracy z danymi XML. W tym przewodniku tworzenia aplikacji systemu Windows, który ładuje dane XML do zestawu danych. Zestaw danych są następnie wyświetlane <xref:System.Windows.Forms.DataGridView> formantu. Na koniec schematu XML na podstawie zawartości pliku XML jest wyświetlana w polu tekstowym.

 Ten przewodnik zawiera pięć głównych kroków:

1.  Tworzenie nowego projektu

2.  Tworzenie pliku XML do odczytu do zestawu danych

3.  Tworzenie interfejsu użytkownika

4.  Tworzenie zestawu danych, odczytywania pliku XML i wyświetlania w <xref:System.Windows.Forms.DataGridView> formantu

5.  Dodawanie kodu do wyświetlenia schematu XML oparty na pliku XML w <xref:System.Windows.Forms.TextBox> formantu

> [!NOTE]
>  Okna dialogowe i poleceń menu, widocznej mogą różnić się od opisanych w pomocy w zależności od ustawienia active lub wersja jest używana. Aby zmienić ustawienia, na **narzędzia** menu, wybierz opcję **Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 W tym kroku utworzysz projekt programu Visual Basic lub Visual C#, który zawiera ten przewodnik.

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt dla systemu Windows

1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.

4. Nazwij projekt **ReadingXML**, a następnie wybierz pozycję **OK**.

     **ReadingXML** projektu jest tworzony i dodawany do **Eksploratora rozwiązań**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generowanie pliku XML do odczytu do zestawu danych
 Ponieważ ten przewodnik koncentruje się na odczytywanie danych XML do zestawu danych, zawartość pliku XML jest dostępne.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Aby utworzyć plik XML, który będzie można ich odczytać w zestawie danych

1.  Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

2.  Wybierz **pliku XML**, nadaj nazwę plikowi `authors.xml`, a następnie wybierz **Dodaj**.

     Plik XML ładuje do projektanta i jest gotowy do edycji.

3.  Wklej następujący kod do edytora poniżej deklaracja XML:

    ```xml
    <Authors_Table>
      <authors>
        <au_id>172-32-1176</au_id>
        <au_lname>White</au_lname>
        <au_fname>Johnson</au_fname>
        <phone>408 496-7223</phone>
        <address>10932 Bigge Rd.</address>
        <city>Menlo Park</city>
        <state>CA</state>
        <zip>94025</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>213-46-8915</au_id>
        <au_lname>Green</au_lname>
        <au_fname>Margie</au_fname>
        <phone>415 986-7020</phone>
        <address>309 63rd St. #411</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94618</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>238-95-7766</au_id>
        <au_lname>Carson</au_lname>
        <au_fname>Cheryl</au_fname>
        <phone>415 548-7723</phone>
        <address>589 Darwin Ln.</address>
        <city>Berkeley</city>
        <state>CA</state>
        <zip>94705</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>267-41-2394</au_id>
        <au_lname>Hunter</au_lname>
        <au_fname>Anne</au_fname>
        <phone>408 286-2428</phone>
        <address>22 Cleveland Av. #14</address>
        <city>San Jose</city>
        <state>CA</state>
        <zip>95128</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>274-80-9391</au_id>
        <au_lname>Straight</au_lname>
        <au_fname>Dean</au_fname>
        <phone>415 834-2919</phone>
        <address>5420 College Av.</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94609</zip>
        <contract>true</contract>
      </authors>
    </Authors_Table>
    ```

4.  Na **pliku** menu, wybierz opcję **zapisać authors.xml**.

## <a name="create-the-user-interface"></a>Tworzenie interfejsu użytkownika
 Interfejs użytkownika dla tej aplikacji składa się z następujących czynności:

-   A <xref:System.Windows.Forms.DataGridView> formant, który wyświetla zawartość pliku XML jako dane.

-   A <xref:System.Windows.Forms.TextBox> kontrolkę wyświetlającą schematu XML w pliku XML.

-   Dwa <xref:System.Windows.Forms.Button> kontrolki.

    -   Jeden z przycisków odczytuje plik XML do zestawu danych i wyświetla je w <xref:System.Windows.Forms.DataGridView> formantu.

    -   Drugi przycisk wyodrębnia schematu z elementu dataset i za pośrednictwem <xref:System.IO.StringWriter> wyświetla go w <xref:System.Windows.Forms.TextBox> formantu.

#### <a name="to-add-controls-to-the-form"></a>Do dodawania formantów do formularza

1.  Otwórz `Form1` w widoku Projekt.

2.  Z **przybornika**, przeciągnij następujących formantów na formularzu:

    -   Jeden <xref:System.Windows.Forms.DataGridView> formantu

    -   Jeden <xref:System.Windows.Forms.TextBox> formantu

    -   Dwa <xref:System.Windows.Forms.Button> formantów

3.  Ustaw następujące właściwości:

    |Formant|Właściwość|Ustawienie|
    |-------------|--------------|-------------|
    |`TextBox1`|**Wiele linii**|`true`|
    ||**Paski przewijania**|**Pionowe**|
    |`Button1`|**Nazwa**|`ReadXmlButton`|
    ||**Tekst**|`Read XML`|
    |`Button2`|**Nazwa**|`ShowSchemaButton`|
    ||**Tekst**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Tworzenie zestawu danych, który odbiera dane XML
 W tym kroku zostanie utworzony nowy zestaw danych o nazwie `authors`. Aby uzyskać więcej informacji na temat zestawów danych, zobacz [narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that-receives-the-xml-data"></a>Aby utworzyć nowy zestaw danych, który odbiera dane XML

1.  W **Eksploratora rozwiązań**, wybierz plik źródłowy **Form1**, a następnie wybierz **Projektant widoków** znajdującego się na **Eksploratora rozwiązań** pasek narzędzi.

2.  Z [przybornik, karta dane](../ide/reference/toolbox-data-tab.md), przeciągnij **DataSet** na **Form1**.

3.  W **Dodaj zestaw danych** okno dialogowe, wybierz opcję **Nietypizowanego zestawu danych**, a następnie wybierz **OK**.

     **DataSet1** jest dodawany do składnika na pasku zadań.

4.  W **właściwości** ustaw **nazwa** i <xref:System.Data.DataSet.DataSetName%2A> właściwości`AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Tworzenie obsługi zdarzeń do odczytania pliku XML do zestawu danych
 **Odczytu XML** przycisk odczytuje plik XML do zestawu danych. Następnie ustawia właściwości na <xref:System.Windows.Forms.DataGridView> formant, który powiązać go z zestawu danych.

#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>Aby dodać kod do obsługi zdarzeń ReadXmlButton_Click

1.  W **Eksploratora rozwiązań**, wybierz pozycję **Form1**, a następnie wybierz **Projektant widoków** znajdującego się na **Eksploratora rozwiązań** narzędzi.

2.  Wybierz **odczytu XML** przycisku.

     **Edytora kodu** otwiera w `ReadXmlButton_Click` obsługi zdarzeń.

3.  Wpisz następujący kod do `ReadXmlButton_Click` obsługi zdarzeń:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4.  W `ReadXMLButton_Click` kod obsługi zdarzenia, zmiany `filepath =` wpisu na prawidłową ścieżkę.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Tworzenie obsługi zdarzeń, aby wyświetlić schemat w polu tekstowym
 **Pokaż schematu** przycisk tworzy <xref:System.IO.StringWriter> obiekt jest wypełniany schemat, który jest wyświetlany w <xref:System.Windows.Forms.TextBox>formantu.

#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Aby dodać kod do obsługi zdarzeń ShowSchemaButton_Click

1.  W **Eksploratora rozwiązań**, wybierz pozycję **Form1**, a następnie wybierz **Widok projektanta** przycisku.

2.  Wybierz **Pokaż schematu** przycisku.

     **Edytora kodu** otwiera w `ShowSchemaButton_Click` obsługi zdarzeń.

3.  Wpisz następujący kod do `ShowSchemaButton_Click` obsługi zdarzeń.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Przetestuj formularz
 Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

1.  Wybierz **F5** do uruchomienia aplikacji.

2.  Wybierz **odczytu XML** przycisku.

     Formant DataGridView Wyświetla zawartość pliku XML.

3.  Wybierz **Pokaż schematu** przycisku.

     Pole tekstowe zawiera schematu XML w pliku XML.

## <a name="next-steps"></a>Następne kroki
 Ten przewodnik zawiera podstawowe informacje dotyczące odczytywania pliku XML do zestawu danych, a także tworzenie schematu na podstawie zawartości pliku XML. Poniżej przedstawiono niektóre zadania, które może zrobić dalej:

-   Edytowanie danych w zestawie danych i zapisu Wycofaj go jako XML. Aby uzyskać więcej informacji, zobacz <xref:System.Data.DataSet.WriteXml%2A>.

-   Edytowanie danych w zestawie danych i zapisać go do bazy danych. Aby uzyskać więcej informacji, zobacz [zapisywania danych](../data-tools/saving-data.md).

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Narzędzia XML w Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)