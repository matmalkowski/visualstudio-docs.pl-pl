---
title: 'Wskazówki: Tworzenie wstawek kodu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 10/27/2017
ms.technology:
- vs-ide-general
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
ms.openlocfilehash: 59aff5d84f81b1e9dea9cd3e4c08527b14dc7f34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-code-snippet"></a>Wskazówki: tworzenie wstawek kodu
Fragment kodu można utworzyć tylko kilka prostych kroków. To wszystko, co należy zrobić, tworzenie pliku XML, wypełnij odpowiednie elementy i Dodaj swój kod do niego. W kodzie, można dodać odniesienia i parametry zamiany. Fragment kodu można dodać do instalacji programu Visual Studio za pomocą przycisku importu w Menedżerze fragmentów kodu (**narzędzia**, **Menedżerze fragmentów kodu...** ).  
  
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
  
### <a name="to-create-a-code-snippet"></a>Aby utworzyć wstawek kodu  
  
1.  Utwórz nowy plik XML w Visual Studio i dodać szablon przedstawionych powyżej.  
  
2.  Wypełnij tytuł wstawki kodu, np. Tekst "hello World VB", w elemencie tytuł.  
  
3.  Wypełnij język fragmentu kodu w językach atrybut elementu kodu. Na przykład użyć "VB".  
  
4.  Na przykład dodać kod w sekcji CDATA wewnątrz elementu kodu:  
  
    ```xml  
    <Code Language="VB">  
        <![CDATA[Console.WriteLine("Hello, World!")]]>  
    </Code>
    ```  
  
5.  Zapisz fragment kodu jako VBCodeSnippet.snippet.  
  
### <a name="to-add-a-code-snippet-to-visual-studio"></a>Aby dodać fragment kodu dla programu Visual Studio  
  
1.  Można dodać własne wstawki na instalację programu Visual Studio za pomocą Menedżera wstawki kodu. Otwórz Menedżera fragmentów kodu (**narzędzia**, **... Menedżer wstawek kodu** ).  
  
2.  Kliknij przycisk **importu** przycisku.  
  
3.  Przejdź do lokalizacji, w której zapisano fragmentu kodu w poprzedniej procedurze, zaznacz go, a następnie kliknij przycisk **Otwórz**.  
  
4.  **Fragment kodu importu** zostanie otwarte okno dialogowe monitem o wybierz miejsce dodać fragment kodu z możliwości w okienku po prawej stronie. Jedną z opcji powinna być **Moje wstawki kodu**. Zaznacz go i kliknij **Zakończ**, następnie **OK**.  
  
5.  Fragment kodu jest kopiowany do następującej lokalizacji:  
  
     Wstawki kodu Basic\My Snippets\Visual 2017\Code %USERPROFILE%\Documents\Visual studio  
  
6.  Przetestuj wstawkę otwierania projektu Visual Basic i otwieranie pliku kodu. W pliku wybierz **wstawki**, **wstawić fragment** z menu kontekstowego, następnie **Moje wstawki kodu**. Powinny pojawić się fragment o nazwie **Moje wstawki kodu programu Visual Basic**. Kliknij go dwukrotnie.  
  
    `Console.WriteLine("Hello, World!")` dodaje się w pliku kodu.  
  
### <a name="adding-description-and-shortcut-fields"></a>Dodawanie pól skrótów i opis  
  
1.  Opis elementu pola podać więcej informacji na temat wstawki kodu programu wyświetlony w Menedżerze fragmentów kodu. Skrót jest tag, który użytkownicy mogą wprowadzić, aby można było wstawić wstawkę. Edytuj fragment, dodane przez otwarcie pliku %USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My kod Snippet\VBCodeSnippet.snippet.  
  
2.  Dodawanie elementów autora i opis dla elementu nagłówka i wypełnić je.  
  
3.  Element nagłówka powinien wyglądać następująco:  
  
    ```xml  
    <Header>  
        <Title>Hello World VB</Title>  
        <Author>Myself</Author>  
        <Description>Says Hello to the world.</Description>  
    </Header>
    ```  
  
4.  Otwórz Menedżer wstawek kodu i wybierz wstawki kodu programu. W okienku po prawej stronie powinny być widoczne czy teraz zostaną wypełnione pola Opis i autora.  
  
5.  Aby dodać skrót, Dodaj element skrótów obok autora i opis elementu:  
  
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
  
### <a name="to-add-references-and-imports"></a>Aby dodać referencje i Importy  
  
1.  Dodaj odwołanie do projektu przy użyciu elementu odwołania i dodać deklaracji importów przy użyciu elementu importów. (Ta dotyczy C# oraz.) Na przykład, jeśli zmienisz `Console.WriteLine` w przykładzie kodu do `MessageBox.Show`, może być konieczne dodanie zestawu System.Windows.Forms.dll do projektu.  
  
2.  Otwórz wstawkę.  
  
3.  Dodaj element odwołania w elemencie fragment kodu:  
  
    ```xml  
    <References>  
        <Reference>  
            <Assembly>System.Windows.Forms.dll</Assembly>  
        </Reference>  
    </References>
    ```  
  
4.  Dodaj element Imports pod elementem fragment kodu:  
  
    ```xml  
    <Imports>  
        <Import>  
           <Namespace>System.Windows.Forms</Namespace>  
        </Import>  
    </Imports>
    ```  
  
5.  Zmień sekcji CDATA na następujący:  
  
    ```xml  
    <![CDATA[MessageBox.Show("Hello, World!")]]>  
    ```  
  
6.  Zapisz fragment kodu.  
  
7.  Otwórz projekt Visual Basic i Dodaj fragment.  
  
8.  Zostanie wyświetlony Importy — instrukcja w górnej części pliku kodu:  
  
    ```vb  
    Imports System.Windows.Forms
    ```  
  
9. Sprawdź właściwości projektu. Na karcie odwołania zawiera odwołanie do System.Windows.Forms.dll.  
  
### <a name="adding-replacements"></a>Dodawanie zamiany  
  
1.  Możesz części z fragmentów kodu mają zostać zastąpione przez użytkownika, na przykład dodać zmienną i użytkownik, który ma zastąpić zmiennej w bieżącym projekcie. Oferuje dwa rodzaje zamiany: literały oraz obiekty. Literały są ciągi pewien typ (Literały ciągu nazwy zmiennych i reprezentacji ciągu wartości liczbowe). Obiekty są wystąpienia typu innego niż ciąg. W tej procedurze zostanie zadeklarować zastępczy literału i zastąpienie obiektu i zmień kod, aby odwołać te elementy zastępcze.  
  
2.  Otwórz wstawkę.  
  
3.  W tym przykładzie użyto parametrów połączenia SQL, więc musisz zmienić importów i odwołania elementy, aby dodać odwołanie do odpowiedniego:  
  
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
  
4.  Aby zadeklarować zastępczy literału ciągu połączenia SQL, Dodaj element deklaracji w elemencie fragment, a w nim Dodaj element literał z podelementy identyfikator, etykietki narzędzia i wartością domyślną dla zastąpienia:  
  
    ```xml  
    <Declarations>  
        <Literal>  
            <ID>SqlConnString</ID>  
            <ToolTip>Replace with a SQL connection string.</ToolTip>  
            <Default>"SQL connection string"</Default>  
        </Literal>  
    </Declarations>
    ```  
  
5.  Aby zadeklarować zastąpienie obiektu połączenia SQL, Dodaj element Object wewnątrz elementu deklaracje i dodać elementy podrzędne dla Identyfikatora, typ obiektu, etykietki narzędzia i wartość domyślną. Wynikowy element deklaracje powinien wyglądać następująco:  
  
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
  
## <a name="see-also"></a>Zobacz też  
[Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)