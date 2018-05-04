---
title: 'Wskazówki: Tworzenie wstawek kodu'
ms.date: 10/27/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6a9890be18e3d43f4c036da72bf2794801e5ec70
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-create-a-code-snippet"></a>Wskazówki: Tworzenie wstawek kodu
Fragment kodu można utworzyć tylko kilka prostych kroków. To wszystko, co należy zrobić, tworzenie pliku XML, wypełnij odpowiednie elementy i Dodaj swój kod do niego. W kodzie, można dodać odniesienia i parametry zamiany. Fragment kodu można dodać do instalacji programu Visual Studio za pomocą **importu** znajdującego się na **Menedżerze fragmentów kodu** (**narzędzia**  >   **Menedżer wstawek kodu**).

## <a name="snippet-template"></a>Fragment kodu szablonu
 Poniżej przedstawiono szablon fragment podstawowe:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

### <a name="create-a-code-snippet"></a>Tworzenie wstawek kodu

1.  Utwórz nowy plik XML w Visual Studio i dodać szablon przedstawionych powyżej.

2.  Wypełnij tytuł wstawki kodu, np. "Tekst hello World VB" w **tytuł** elementu.

3.  Wypełnij fragmentu kodu w języku **języków** atrybutu **kod** elementu. Na przykład użyć "VB".

4.  Dodaj kod w **CDATA** sekcji wewnątrz **kod** element, na przykład:

    ```xml
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>
    ```

5.  Zapisz fragment jako *VBCodeSnippet.snippet*.

### <a name="add-a-code-snippet-to-visual-studio"></a>Dodawanie wstawki kodu programu Visual Studio

1.  Można dodać własne wstawki na instalację programu Visual Studio za pomocą Menedżera wstawki kodu. Otwórz **Menedżerze fragmentów kodu** (**narzędzia** > **Menedżerze fragmentów kodu**).

2.  Kliknij przycisk **importu** przycisku.

3.  Przejdź do lokalizacji, w której zapisano fragmentu kodu w poprzedniej procedurze, zaznacz go, a następnie kliknij przycisk **Otwórz**.

4.  **Fragment kodu importu** zostanie otwarte okno dialogowe monitem o wybierz miejsce dodać fragment kodu z możliwości w okienku po prawej stronie. Jedną z opcji powinna być **Moje wstawki kodu**. Zaznacz go i kliknij **Zakończ**, następnie **OK**.

5.  Fragment kodu jest kopiowany do następującej lokalizacji:

     *Wstawki kodu Basic\My Snippets\Visual 2017\Code %USERPROFILE%\Documents\Visual studio*

6.  Przetestuj wstawkę otwierania projektu Visual Basic i otwieranie pliku kodu. W pliku wybierz **wstawki** > **wstawić fragment** z menu kontekstowego, następnie **Moje wstawki kodu**. Powinny pojawić się fragment o nazwie **Moje wstawki kodu programu Visual Basic**. Kliknij go dwukrotnie.

    `Console.WriteLine("Hello, World!")` dodaje się w pliku kodu.

### <a name="add-description-and-shortcut-fields"></a>Dodaj pola Opis i skrótów

1.  Opis elementu pola podać więcej informacji na temat wstawki kodu programu wyświetlony w Menedżerze fragmentów kodu. Skrót jest tag, który użytkownicy mogą wprowadzić, aby można było wstawić wstawkę. Edytuj fragment zostały dodane, otwierając plik *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My kod Snippet\VBCodeSnippet.snippet*.

2.  Dodaj **autora** i **opis** elementy do **nagłówka** elementu i wypełnić je.

3.  **Nagłówka** element powinien wyglądać następująco:

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>
    ```

4.  Otwórz **Menedżerze fragmentów kodu** i wybierz wstawki kodu programu. W okienku po prawej stronie powinna zostać wyświetlona który **opis** i **autora** pola teraz są wypełnione.

5.  Aby dodać skrót, Dodaj **skrótów** elementu obok **autora** i **opis** elementu:

    ```xml
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>
    ```

6.  Zapisz plik fragment ponownie.

7.  Aby przetestować skrót, otwórz projekt Visual Basic i otwieranie pliku kodu. Typ `hello` w pliku i naciśnij klawisz **kartę** dwa razy.

    Fragment kodu jest wstawiany.

### <a name="add-references-and-imports"></a>Dodaj referencje i Importy

1.  Możesz dodać odwołania do projektu przy użyciu **odwołania** element i Dodaj deklaracji importów przy użyciu **importów** elementu. (Ta dotyczy C# oraz.) Na przykład, jeśli zmienisz `Console.WriteLine` w przykładzie kodu do `MessageBox.Show`, może być konieczne dodanie *System.Windows.Forms.dll* zestawu do projektu.

2.  Otwórz wstawkę.

3.  Dodaj **odwołania** pod **fragment** elementu:

    ```xml
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>
    ```

4.  Dodaj **importów** pod **fragment** elementu:

    ```xml
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>
    ```

5.  Zmień **CDATA** sekcji do następującego:

    ```xml
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6.  Zapisz fragment kodu.

7.  Otwórz projekt Visual Basic i Dodaj fragment.

8.  Zobaczysz `Imports` instrukcji w górnej części pliku kodu:

    ```vb
    Imports System.Windows.Forms
    ```

9. Sprawdź właściwości projektu. **Odwołania** karta zawiera odwołanie do *System.Windows.Forms.dll*.

### <a name="add-replacements"></a>Dodaj elementy zastępcze

1.  Możesz części z fragmentów kodu mają zostać zastąpione przez użytkownika, na przykład dodać zmienną i użytkownik, który ma zastąpić zmiennej w bieżącym projekcie. Oferuje dwa rodzaje zamiany: literały oraz obiekty. Literały są ciągi pewien typ (Literały ciągu nazwy zmiennych i reprezentacji ciągu wartości liczbowe). Obiekty są wystąpienia typu innego niż ciąg. W tej procedurze zostanie zadeklarować zastępczy literału i zastąpienie obiektu i zmień kod, aby odwołać te elementy zastępcze.

2.  Otwórz wstawkę.

3.  W tym przykładzie użyto parametrów połączenia SQL, tak aby zmienić **importów** i **odwołania** elementy, aby dodać odpowiednie odwołania:

    ```xml
    <References>
        <Reference>
            <Assembly>System.Data.dll</Assembly>
        </Reference>
        <Reference>
            <Assembly>System.Xml.dll</Assembly>
        </Reference>
    </References>
    <Imports>
        <Import>
            <Namespace>System.Data</Namespace>
        </Import>
        <Import>
            <Namespace>System.Data.SqlClient</Namespace>
        </Import>
    </Imports>
    ```

4.  Aby zadeklarować zastępczy literału ciągu połączenia SQL, należy dodać **deklaracje** elementu w obszarze **fragment** elementu i jego Dodaj **literału** elementu z podelementy identyfikator, etykietki narzędzia i wartością domyślną dla zastąpienia:

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>
    ```

5.  Aby zadeklarować zastąpienie obiektu połączenia SQL, należy dodać **obiektu** element wewnątrz **deklaracje** element i Dodaj elementy podrzędne dla Identyfikatora typu obiektu, etykietki narzędzia i domyślne wartość. Powstałe w ten sposób **deklaracje** element powinien wyglądać następująco:

    ```xml
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
        <Object>
            <ID>SqlConnection</ID>
            <Type>System.Data.SqlClient.SqlConnection</Type>
            <ToolTip>Replace with a connection object in your application.</ToolTip>
            <Default>dcConnection</Default>
        </Object>
    </Declarations>
    ```

6.  W sekcji kodu można się odwołać zastępcze z otaczającego znaki $, na przykład `$replacement$`:

    ```xml
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7.  Zapisz fragment kodu.

8.  Otwórz projekt Visual Basic i Dodaj fragment.

9. Kod powinien wyglądać podobnie do następującego: gdzie zastępcze `SQL connection string` i `dcConnection` są wyróżniane w kolorze pomarańczowym prostych. Wybierz **kartę** można przejść z jednego do drugiego.

    ```vb
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection
    ```

## <a name="see-also"></a>Zobacz także

- [Odwołanie do schematu wstawki kodu](../ide/code-snippets-schema-reference.md)