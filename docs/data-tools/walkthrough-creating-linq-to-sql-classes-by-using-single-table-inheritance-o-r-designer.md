---
title: "Wskazówki: Tworzenie klasy LINQ do SQL za pomocą pojedynczej tabeli dziedziczenia (Projektant O-R) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b6e255492f0859689b41723657338140ffee5931
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Wskazówki: Tworzenie klasy LINQ do SQL za pomocą pojedynczej tabeli dziedziczenia (Projektanta obiektów relacyjnych)
[Składnika LINQ to SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) obsługuje dziedziczenia pojedynczej tabeli, ponieważ jest on zwykle implementowany w systemach relacyjnych. W tym przewodniku rozszerza ogólne kroki podane w [porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) tematu i zapewnia niektórych danych rzeczywistych na przedstawiają sposób używania dziedziczenia w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 Podczas tego przewodnika wykonasz następujące zadania:  
  
-   Tworzenie tabeli bazy danych i Dodaj do niej danych.  
  
-   Tworzenie aplikacji formularzy systemu Windows.  
  
-   Dodaj [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] plik do projektu.  
  
-   Utwórz nowe klasy jednostki.  
  
-   Należy skonfigurować do używania dziedziczenia klas jednostek.  
  
-   Wyślij zapytanie do dziedziczonej klasie.  
  
-   Wyświetlanie danych w formularzu systemu Windows.  
  
## <a name="create-a-table-to-inherit-from"></a>Utwórz tabelę odziedziczone  
 Aby zobaczyć, jak działa dziedziczenie, zostanie tworzenie małej tabeli osoby, używać go jako klasę podstawową, a następnie utwórz obiekt pracownika, który dziedziczy on.  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Do utworzenia tabeli podstawowej, aby zademonstrować dziedziczenia  
  
1.  W **Eksploratora serwera**/**Eksploratora bazy danych**, kliknij prawym przyciskiem myszy **tabel** węzeł i kliknij przycisk **Dodaj nową tabelę**.  
  
    > [!NOTE]
    >  Korzystania z bazy danych Northwind lub inne bazy danych można dodać do tabeli.  
  
2.  Przy użyciu projektanta tabeli należy dodać następujące kolumny do tabeli:  
  
    |Nazwa kolumny|Typ danych|Dopuszcza wartości null|  
    |-----------------|---------------|-----------------|  
    |**IDENTYFIKATOR**|**int**|**Wartość false**|  
    |**Typ**|**int**|**Wartość true**|  
    |**Imię**|**nvarchar(200)**|**Wartość false**|  
    |**Nazwisko**|**nvarchar(200)**|**Wartość false**|  
    |**Menedżer**|**int**|**Wartość true**|  
  
3.  Wartość w kolumnie identyfikator jako klucz podstawowy.  
  
4.  Zapisywanie tabeli i nadaj mu nazwę **osoby**.  
  
## <a name="add-data-to-the-table"></a>Dodawanie danych do tabeli  
 Dzięki czemu można sprawdzić, czy dziedziczenia jest prawidłowo skonfigurowany, tabela musi niektóre dane dla każdej klasy w dziedziczeniu pojedynczej tabeli.  
  
#### <a name="to-add-data-to-the-table"></a>Aby dodać dane do tabeli  
  
1.  Otwórz tabelę w widoku danych. (Kliknij prawym przyciskiem myszy **osoby** tabeli w **Eksploratora serwera**/**Eksploratora bazy danych** i kliknij przycisk **Pokaż dane tabeli**.)  
  
2.  Skopiuj następujące dane do tabeli. (Można skopiuj go i wklej go do tabeli, wybierając cały wiersz w okienku wyników.)  
  
    ||||||  
    |-|-|-|-|-|  
    |**IDENTYFIKATOR**|**Typ**|**Imię**|**Nazwisko**|**Menedżer**|  
    |**1**|**1**|**Anna**|**Wallace**|**WARTOŚĆ NULL**|  
    |**2**|**1**|**Artur**|**Grilo**|**WARTOŚĆ NULL**|  
    |**3**|**1**|**Yael**|**Peled**|**WARTOŚĆ NULL**|  
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|  
    |**5**|**2**|**Andreasowi**|**Hauser**|**1**|  
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|  
    |**7**|**2**|**ALEXEY**|**Orekhov**|**2**|  
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|  
    |**9**|**2**|**Akończenie**|**Yee**|**2**|  
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|  
    |**11**|**2**|**Beata**|**Pole**|**3**|  
    |**12**|**2**|**Krzysztof**|**Kwok**|**3**|  
  
## <a name="create-a-new-project"></a>Utwórz nowy projekt  
 Teraz, po utworzeniu tabeli, należy utworzyć nowy projekt, aby zademonstrować Konfigurowanie dziedziczenia.  
  
#### <a name="to-create-the-new-windows-forms-application"></a>Aby utworzyć nową aplikację formularzy systemu Windows  
  
1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .  
  
2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.  

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.  

4. Nazwij projekt **InheritanceWalkthrough**, a następnie wybierz pozycję **OK**. 
  
     **InheritanceWalkthrough** projektu jest tworzony i dodane do **Eksploratora rozwiązań**.  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Dodaj składnika LINQ to SQL klasy plik do projektu  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Aby dodać LINQ do SQL pliku do projektu  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  Kliknij przycisk **klasy LINQ do SQL** szablonu, a następnie kliknij przycisk **Dodaj**.  
  
     Plik .dbml zostanie dodany do projektu i [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] otwiera.  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>Tworzenie dziedziczenia za pomocą Projektanta obiektów relacyjnych  
 Konfigurowanie dziedziczenia przeciągając **dziedziczenia** obiekt z **przybornika** na powierzchnię projektu.  
  
#### <a name="to-create-the-inheritance"></a>Aby utworzyć dziedziczenia  
  
1.  W **Eksploratora serwera**/**Eksploratora bazy danych**, przejdź do **osoby** tabeli, który został utworzony wcześniej.  
  
2.  Przeciągnij **osoby** tabeli na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] powierzchnię projektu.  
  
3.  Przeciągnij drugi **osoby** tabeli na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] i zmień jego nazwę, aby **pracownika**.  
  
4.  Usuń **Menedżera** właściwość z **osoby** obiektu.  
  
5.  Usuń **typu**, **identyfikator**, **imię**, i **nazwisko** właściwości z **pracownika** obiektu. (Innymi słowy, Usuń wszystkie właściwości, z wyjątkiem **Menedżera**.)  
  
6.  Z **Projektant obiektów relacyjnych** karcie **przybornika**, Utwórz **dziedziczenia** między **osoby** i  **Pracownik** obiektów. Aby to zrobić, kliknij przycisk **dziedziczenia** elementu **przybornika** i zwolnij przycisk myszy. Następnie kliknij przycisk **pracownika** obiektu, a następnie **osoby** obiektu w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Wskaż strzałkę na linii dziedziczenia **osoby** obiektu.  
  
7.  Kliknij przycisk **dziedziczenia** linia na powierzchni projektu.  
  
8.  Ustaw **właściwość rozróżniacza** właściwości **typu**.  
  
9. Ustaw **wartość dyskryminatora klasy pochodnej** właściwości **2**.  
  
10. Ustaw **wartość dyskryminatora klasy podstawowej** właściwości **1**.  
  
11. Ustaw **domyślnej dziedziczenia** właściwości **osoby**.  
  
12. Skompiluj projekt.  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Zapytanie dziedziczonej klasie i wyświetlić dane w formularzu  
 Teraz należy dodać kodu do formularza, który wysyła zapytanie do określonej klasy w modelu obiektów.  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Tworzenie zapytań LINQ i wyświetlić wyniki w formularzu  
  
1.  Przeciągnij **ListBox** na Form1.  
  
2.  Kliknij dwukrotnie formularz, aby utworzyć `Form1_Load` obsługi zdarzeń.  
  
3.  Dodaj następujący kod do `Form1_Load` obsługi zdarzeń:  
  
    ```vb  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```csharp  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Uruchom aplikację i sprawdź, czy rekordy wyświetlane w polu listy wszystkich pracowników (rekordy, które mają wartość 2 w ich kolumny typu).  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Naciśnij F5.  
  
2.  Sprawdź, czy są wyświetlane tylko te rekordy, które mają wartość 2 w ich kolumny typu.  
  
3.  Zamknij formularz. (Na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.)  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Wskazówki: Tworzenie klasy LINQ do SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Instrukcje: Generowanie modelu obiektu w języku Visual Basic lub C#](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)