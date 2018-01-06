---
title: "Wskazówki: Tworzenie listy zewnętrznej w SharePoint za pomocą danych biznesowych | Dokumentacja firmy Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
ms.assetid: 046cf234-705a-4a6f-91f8-c5c569ae0dd0
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8ecc80a3c26b97b9754f998bd0903471d00cd1d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data"></a>Wskazówki: tworzenie listy zewnętrznej w SharePoint za pomocą danych biznesowych
  Usługa łączności danych biznesowych (BDC) umożliwia wyświetlanie danych biznesowych z wewnętrznego serwera aplikacji, usług sieci Web i baz danych programu SharePoint.  
  
 W tym przewodniku przedstawiono sposób tworzenia modelu usługi BDC, który zwraca informacje o kontaktach w przykładowej bazie danych. Spowoduje to utworzenie listy zewnętrznej w SharePoint za pomocą tego modelu.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie nowego projektu.  
  
-   Dodawanie jednostki do modelu.  
  
-   Dodawanie metody wyszukiwania.  
  
-   Dodawanie metody wyszukiwania.  
  
-   Testowanie projektu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Windows i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)], [!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)], lub [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)].  
  
-   Dostęp do przykładowej bazy danych AdventureWorks. Aby uzyskać więcej informacji o sposobie instalowania bazy danych AdventureWorks, zobacz [baz danych programu SQL Server próbki](http://go.microsoft.com/fwlink/?LinkID=117483).  
  
## <a name="creating-a-project-that-contains-a-bdc-model"></a>Tworzenie projektu, który zawiera model usługi BDC  
  
#### <a name="to-create-a-project-that-contains-a-bdc-model"></a>Aby utworzyć projekt, który zawiera model usługi BDC  
  
1.  Na pasku menu programu Visual Studio wybierz **pliku**, **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
2.  Pod **Visual C#** lub **Visual Basic**, rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** elementu.  
  
3.  W **szablony** okienku wybierz **projektu programu SharePoint 2010**, nazwij projekt **AdventureWorksTest**, a następnie wybierz pozycję **OK** przycisku .  
  
     **Kreator dostosowania programu SharePoint** pojawi się. W tym kreatorze można określić lokacji, który ma być używany do debugowania projektu i ustawić poziom zaufania rozwiązania.  
  
4.  Wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, aby ustawić poziom zaufania.  
  
5.  Wybierz **Zakończ** przycisk, aby zaakceptować domyślne lokalnej witryny programu SharePoint.  
  
6.  W **Eksploratora rozwiązań**, wybierz węzeł projektu programu SharePoint.  
  
7.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
8.  W **szablony** okienku wybierz **modelu łączności danych biznesowych (farmy rozwiązania tylko)**, nazwij projekt **AdventureWorksContacts**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
## <a name="adding-data-access-classes-to-the-project"></a>Dodawanie klas dostępu do danych do projektu  
  
#### <a name="to-add-data-access-classes-to-the-project"></a>Aby dodać klasy dostępu do danych do projektu  
  
1.  Na pasku menu wybierz **narzędzia**, **Połącz z bazą danych**.  
  
     **Dodawanie połączenia** zostanie otwarte okno dialogowe.  
  
2.  Dodaj połączenie do przykładowej bazy danych AdventureWorks serwera SQL.  
  
     Aby uzyskać więcej informacji, zobacz [Dodawanie i modyfikowanie połączenia (Microsoft SQL Server)](http://msdn.microsoft.com/en-us/fa400910-26c3-4df7-b9d1-115e688b4ea3).  
  
3.  W **Eksploratora rozwiązań**, wybierz węzeł projektu.  
  
4.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
5.  W **zainstalowane szablony** okienku wybierz **danych** węzła.  
  
6.  W **szablony** okienku wybierz **klasy LINQ do SQL**.  
  
7.  W **nazwa** określ **AdventureWorks**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Plik .dbml zostanie dodany do projektu, a następnie otwiera Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych).  
  
8.  Na pasku menu wybierz **widoku**, **Eksploratora serwera**.  
  
9. W **Eksploratora serwera**, rozwiń węzeł, który reprezentuje przykładową bazę danych AdventureWorks, a następnie rozwiń węzeł **tabel** węzła.  
  
10. Dodaj **kontaktu (osoba)** tabeli do Projektanta obiektów relacyjnych.  
  
     Klasa jednostki jest tworzony i wyświetlany na powierzchni projektu. Klasa jednostki ma właściwości, które mapują kolumny w tabeli Kontakt (osoba).  
  
## <a name="removing-the-default-entity-from-the-bdc-model"></a>Usuwanie jednostki domyślnej z modelu usługi BDC  
 **Modelu łączności danych biznesowych** projektu dodaje do jednostki domyślne o nazwie Entity1 do modelu. Usunięcie tej jednostki. Później należy dodać nową jednostkę. Począwszy od pusty model zmniejsza liczbę czynności wymagane do ukończenia przewodnika.  
  
#### <a name="to-remove-the-default-entity-from-the-model"></a>Aby usunąć jednostkę domyślną z modelu  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **BdcModel1** węzeł, a następnie otwórz plik BdcModel1.bdcm.  
  
2.  Otwiera plik modelu usługi łączności danych biznesowych w Projektancie usługi łączności danych biznesowych.  
  
3.  W projektancie, otwórz menu skrótów **Entity1**, a następnie wybierz pozycję **usunąć**.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów Entity1.vb (w języku Visual Basic) lub Entity1.cs (w języku C#), a następnie wybierz **usunąć**.  
  
5.  Otwórz menu skrótów Entity1Service.vb (w języku Visual Basic) lub Entity1Service.cs (w języku C#), a następnie wybierz pozycję **usunąć**.  
  
## <a name="adding-an-entity-to-the-model"></a>Dodawanie jednostki do modelu  
 Dodawanie jednostki do modelu. Można dodać jednostki z programu Visual Studio **przybornika** do projektanta usługi łączności danych biznesowych.  
  
#### <a name="to-add-an-entity-to-the-model"></a>Aby dodać obiekt do modelu  
  
1.  Na pasku menu wybierz **widoku**, **przybornika**.  
  
2.  Na **BusinessDataConnectivity** karcie **przybornika**, Dodaj **jednostki** do projektanta usługi łączności danych biznesowych.  
  
     Nowa jednostka będzie wyświetlany w projektancie. Visual Studio dodaje plik o nazwie EntityService.vb (w języku Visual Basic) lub EntityService.cs (w języku C#) do projektu.  
  
3.  Na pasku menu wybierz **widoku**, **właściwości**, **okna**.  
  
4.  W **właściwości** ustaw **nazwa** wartości właściwości do **skontaktuj się z**.  
  
5.  W projektancie, otwórz menu skrótów dla jednostki, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **identyfikator**.  
  
     Nowy identyfikator pojawia się na jednostce.  
  
6.  W **właściwości** okna, Zmień nazwę identyfikatora do **wartość ContactID**.  
  
7.  W **nazwy typu** wybierz **System.Int32**.  
  
## <a name="adding-a-specific-finder-method"></a>Dodawanie określonej metody wyszukiwania  
 Aby włączyć usługi BDC do wyświetlania określonego kontaktu, należy dodać metody wyszukiwania. Usługa BDC wywołuje metodę określonej metody wyszukiwania, gdy użytkownik wybierze element na liście, a następnie wybiera **elementu widoku** na Wstążce.  
  
 Dodaj metody wyszukiwania do jednostki kontaktu przy użyciu **szczegóły metody usługi łączności danych biznesowych** okna. Aby powrócić do określonej jednostki, należy dodać kod do metody.  
  
#### <a name="to-add-a-specific-finder-method"></a>Aby dodać określoną metodę wyszukiwania  
  
1.  W Projektancie BDC wybierz **skontaktuj się z** jednostki.  
  
2.  Na pasku menu wybierz **widoku**, **inne okna**, **szczegóły metody usługi łączności danych biznesowych**.  
  
     Zostanie otwarte okno Szczegóły metody usługi łączności danych biznesowych.  
  
3.  W **Dodaj metodę** wybierz **utworzyć określonej metody wyszukiwania**.  
  
     Visual Studio dodaje następujące elementy do modelu. Te elementy są wyświetlane w **szczegóły metody usługi łączności danych biznesowych** okna.  
  
    -   Metodę o nazwie ReadItem.  
  
    -   Parametr wejściowy dla metody.  
  
    -   Parametr zwrotnego dla metody.  
  
    -   Deskryptor typu dla każdego parametru.  
  
    -   Wystąpienia metody dla metody.  
  
4.  W **szczegóły metody usługi łączności danych biznesowych** okna, Otwórz listę, które pojawiają się **skontaktuj się z** deskryptor typu, a następnie wybierz pozycję **Edytuj**.  
  
     **Eksplorator modelu BDC** otwiera i udostępnia hierarchiczny widok modelu.  
  
5.  W **właściwości** oknie dalej, aby otworzyć listę **TypeName** właściwości, wybierz **bieżącego projektu** karcie, a następnie wybierz pozycję **skontaktuj się z**właściwości.  
  
6.  W **Eksplorator modelu BDC**, otwórz menu skrótów **skontaktuj się z**, a następnie wybierz pozycję **dodać deskryptor typu**.  
  
     Nowy deskryptor typu o nazwie **TypeDescriptor1** pojawia się w **Eksplorator modelu BDC**.  
  
7.  W **właściwości** ustaw **nazwa** wartości właściwości do **wartość ContactID**.  
  
8.  Dalej, aby otworzyć listę **TypeName** właściwości, a następnie wybierz pozycję **Int32**.  
  
9. Dalej, aby otworzyć listę **identyfikator** właściwości, a następnie wybierz pozycję **wartość ContactID**.  
  
10. Powtórz krok 6, aby utworzyć deskryptor typu dla każdego z poniższych pól.  
  
    |Nazwa|Nazwa typu|  
    |----------|---------------|  
    |Imię|System.String|  
    |Nazwisko|System.String|  
    |Telefon|System.String|  
    |EmailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. W Projektancie BDC na **skontaktuj się z** jednostki, otwórz **ReadItem** metody.  
  
     Skontaktuj się z pliku kodu usługi zostanie otwarty w edytorze kodu.  
  
12. W `ContactService` klasy, Zastąp `ReadItem` metodę z następującym kodem. Kod będzie wykonywał następujące zadania:  
  
    -   Pobiera rekord z tabeli skontaktuj się z bazy danych AdventureWorks.  
  
    -   Zwraca obiektu Kontakt z usługą BDC.  
  
    > [!NOTE]  
    >  Zastąp wartość `ServerName` nazwę serwera.  
  
     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]  
  
## <a name="adding-a-finder-method"></a>Dodawanie metody wyszukiwania  
 Aby włączyć usługę BDC do wyświetlenia na liście kontaktów, należy dodać metody wyszukiwania. Dodawanie metody wyszukiwania do obiektu kontakt przy użyciu **szczegóły metody usługi łączności danych biznesowych** okna. Aby przywrócić kolekcji jednostek usługi BDC, Dodaj kod do metody.  
  
#### <a name="to-add-a-finder-method"></a>Aby dodać metodę wyszukiwania  
  
1.  W Projektancie BDC wybierz **skontaktuj się z** jednostki.  
  
2.  W **szczegóły metody usługi łączności danych biznesowych** okna, należy Zwiń **ReadItem** węzła.  
  
3.  W **Dodaj metodę** w obszarze **ReadList** metody, wybierz **Utwórz metody wyszukiwania**.  
  
     Visual Studio dodaje metody, parametr zwrotnego i deskryptor typu.  
  
4.  W Projektancie BDC na **skontaktuj się z** jednostki, otwórz **ReadList** metody.  
  
     Pliku kodu usługi kontaktów zostanie otwarty w edytorze kodu.  
  
5.  W `ContactService` klasy, Zastąp `ReadList` metodę z następującym kodem. Kod będzie wykonywał następujące zadania:  
  
    -   Pobiera dane z bazy danych AdventureWorks tabeli kontaktów.  
  
    -   Zwraca listę jednostek skontaktuj się z usługą BDC.  
  
    > [!NOTE]  
    >  Zastąp wartość `ServerName` nazwę serwera.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="testing-the-project"></a>Testowanie projektu  
 Po uruchomieniu projektu otwiera witrynę programu SharePoint i Visual Studio dodaje modelu usługi łączności danych biznesowych. Tworzenie listy zewnętrznej w SharePoint, która odwołuje się do obiektu Kontakt. Dane dotyczące kontaktów w bazie danych AdventureWorks znajdują się na liście.  
  
> [!NOTE]  
>  Może być konieczne przed debugowaniem rozwiązania zmodyfikować ustawienia zabezpieczeń w programie SharePoint.  Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
#### <a name="to-test-the-project"></a>Aby przetestować projekt  
  
1.  Wybierz **F5** klucza.  
  
     Otwieranie witryny programu SharePoint.  
  
2.  Na **Akcje witryny** menu, wybierz **więcej opcji** polecenia.  
  
3.  Na **Utwórz** wybierz pozycję **listy zewnętrznej** szablonu, a następnie wybierz pozycję **Utwórz** przycisku.  
  
4.  Lista niestandardowych nazw **kontaktów**.  
  
5.  Kliknij przycisk Przeglądaj obok **typu zawartości zewnętrznej** pola.  
  
6.  W **zewnętrznych selektor typu zawartości** okno dialogowe Wybierz **AdventureWorksContacts.BdcModel1.Contact** elementu, a następnie wybierz pozycję **Utwórz** przycisku.  
  
     SharePoint tworzy listy zewnętrznej, która zawiera kontakty z przykładową bazę danych AdventureWorks.  
  
7.  Aby przetestować metody wyszukiwania, wybierz z listy kontakt.  
  
8.  Na Wstążce wybierz **elementów** karcie, a następnie wybierz pozycję **elementu widoku** polecenia.  
  
     Szczegóły kontaktu, która została wybrana opcja są wyświetlane w formularzu.  
  
## <a name="next-steps"></a>Następne kroki  
 Można poznać więcej informacji na temat sposobu projektowania modele usługi BDC w programie SharePoint z tych tematów:  
  
-   [Porady: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md).  
  
-   [Porady: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md).  
  
-   [Porady: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Integrowanie danych biznesowych z SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  