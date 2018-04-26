---
title: Łączenie z danymi w bazie danych programu Access (formularze systemu Windows)
ms.date: 09/15/2017
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d15cf1d8e2d7a7178b6ffc423319fcadd8e00cad
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Łączenie z danymi w bazie danych programu Access (formularze systemu Windows)
Bazy danych programu Access (pliku MDF lub pliku .accdb) można nawiązać za pomocą programu Visual Studio. Po zdefiniowaniu połączenia, dane są wyświetlane w **źródeł danych** okna. Stamtąd można przeciągnąć tabele lub widoki na formularze.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby korzystać z tych procedur, potrzebny jest projektem aplikacji formularzy systemu Windows i bazy danych programu Access (plik .accdb) lub bazy danych programu Access 2000-2003 (plik mdb). Wykonaj procedurę, która odnosi się do typu Twojego pliku.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Tworzenie zestawu danych dla pliku .accdb
 Można połączyć z baz danych utworzonych za pomocą dostępu 2013, Office 365, Access 2010 lub Access 2007 przy użyciu poniższej procedury.

#### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych

1.  Otwórz aplikacji formularzy systemu Windows, z którym chcesz się połączyć danych.

2.  Na **widoku** menu, wybierz opcję **inne okna** > **źródeł danych**.

     ![Wyświetlać innych źródeł danych systemu Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

     **Kreator konfiguracji źródła danych** otwiera.

4.  Wybierz **bazy danych** na **wybierz typ źródła danych** , a następnie wybierz **dalej**.

5.  Wybierz **Dataset** na **wybierz Model bazy danych** , a następnie wybierz **dalej**.

6.  Na **wybierz połączenie danych** wybierz pozycję **nowe połączenie** można skonfigurować nowe połączenia danych.

     **Dodawanie połączenia** zostanie otwarte okno dialogowe.

7.  Wybierz **zmiany** znajdujący się obok **źródła danych** pola tekstowego.

     **Źródło danych zmiany** zostanie otwarte okno dialogowe.

8.  Na liście źródeł danych, wybierz  **\<innych\>**. W **dostawcy danych** listy rozwijanej, wybierz pozycję **.NET Framework Data Provider for OLE DB**, a następnie wybierz **OK**.

9. W **Dodawanie połączenia** okno dialogowe, wybierz opcję **Microsoft Office 12.0 dostępu do bazy danych aparatu OLE DB Provider** z **dostawcy OLE DB** listy rozwijanej.

     ![OLE DB dostawcy programu Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

     > [!NOTE]
     >  Jeśli nie widzisz **Microsoft Office 12.0 dostępu do bazy danych aparatu OLE DB Provider** w dostawcy OLE DB listy rozwijanej, należy zainstalować [sterownik systemu Office 2007: składniki łączności danych](https://www.microsoft.com/download/confirmation.aspx?id=23734).

9. W **nazwę serwera lub pliku** polu tekstowym określ ścieżkę i plików, nazwa pliku .accdb chcesz nawiązać połączenie, a następnie wybierz **OK**. (Jeśli plik bazy danych ma nazwę użytkownika i hasło, określ je przed wybraniem **OK**.)

10. Wybierz **dalej** na **wybierz połączenie danych** strony.

     Mogą być wyświetlane okno dialogowe z informacją o plik danych nie ma w bieżącym projekcie. Wybierz **tak** lub **nr**.

11. Wybierz **dalej** na **zapisać parametry połączenia w pliku konfiguracji aplikacji** strony.

12. Rozwiń węzeł **tabel** węzła na **wybierz obiekty bazy danych** strony.

13. Wybierz niezależnie od tabel lub widoków w zestawie danych, a następnie wybierz **Zakończ**.

     Zestaw danych zostanie dodany do projektu i tabele i widoki są wyświetlane w **źródeł danych** okna.

## <a name="creating-the-dataset-for-an-mdb-file"></a>Tworzenie zestawu danych dla plikowych
 Utwórz zestaw danych, uruchamiając **Kreator konfiguracji źródła danych**.

#### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych

1.  Otwórz aplikacji formularzy systemu Windows, z którym chcesz się połączyć danych.

2.  Na **widoku** menu, wybierz opcję **inne okna** > **źródeł danych**.

     ![Wyświetlać innych źródeł danych systemu Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

     **Kreator konfiguracji źródła danych** otwiera.

4.  Wybierz **bazy danych** na **wybierz typ źródła danych** , a następnie wybierz **dalej**.

5.  Wybierz **Dataset** na **wybierz Model bazy danych** , a następnie wybierz **dalej**.

6.  Na **wybierz połączenie danych** wybierz pozycję **nowe połączenie** można skonfigurować nowe połączenia danych.

7.  Jeśli źródło danych nie jest **pliku bazy danych programu Microsoft Access (OLE DB)**, wybierz pozycję **zmiany** otworzyć **źródło danych zmiany** okno dialogowe i wybierz **firmy Microsoft Dostęp do pliku bazy danych**, a następnie wybierz **OK**.

8.  W **nazwa pliku bazy danych**, określ ścieżkę i nazwę pliku MDB chcesz nawiązać połączenie, a następnie wybierz **OK**.

     ![Dodaj plik bazy danych programu Access połączenia](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")

9. Wybierz **dalej** na **wybierz połączenie danych** strony.

10. Wybierz **dalej** na **zapisać parametry połączenia w pliku konfiguracji aplikacji** strony.

11. Rozwiń węzeł **tabel** węzła na **wybierz obiekty bazy danych** strony.

12. Wybierz niezależnie od tabel lub widoków w zestawie danych, a następnie wybierz **Zakończ**.

     Zestaw danych zostanie dodany do projektu i tabele i widoki są wyświetlane w **źródeł danych** okna.

## <a name="security"></a>Zabezpieczenia
 Przechowywanie poufnych informacji (takich jak hasło) może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="next-steps"></a>Następne kroki
 Nowo utworzony zestaw danych jest teraz dostępna w **źródeł danych** okna. Można teraz wykonywać dowolne z następujących zadań:

-   Wybierz elementy w **źródeł danych** okna i przeciągnij je na formularzu (zobacz [formanty formularzy systemu Windows powiązać z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

-   Otworzyć źródła danych w **Projektant obiektów Dataset** umożliwiają dodawanie lub edytowanie obiektów, które tworzą zestaw danych.

-   Dodaj logikę sprawdzania poprawności do <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> zdarzeń tabel danych w zestawie danych (zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Zobacz także

- [Dodawanie połączeń](../data-tools/add-new-connections.md)