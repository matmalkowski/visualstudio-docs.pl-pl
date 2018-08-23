---
title: 'Porady: łączenie z danymi w bazie danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases, connecting to
- data sources, databases
- data [Visual Studio], connecting to databases
- data sources, creating
- database connections
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 72b278305995e2edb86e612e0c5c3789c8ce756a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42670821"
---
# <a name="how-to-connect-to-data-in-a-database"></a>Porady: łączenie z danymi w bazie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć programu Visual Studio, aby połączyć aplikację z bazą danych. Po utworzeniu połączenia danych, program Visual Studio generuje model danych używanych przez aplikację do interakcji z danymi w bazie danych. Obiekty w modelu danych są wyświetlane w [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Następnie możesz utworzyć formanty powiązane z danymi przez przeciąganie elementów z **okna źródeł danych** do powierzchni projektowej. Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Ten temat zawiera instrukcje dotyczące nawiązywania połączenia z bazą danych i tworzenia następujących rodzajów modeli danych:  
  
-   Zestaw danych  
  
-   Entity Data Model (EDM)  
  
> [!NOTE]
>  Visual Studio umożliwia również tworzenie LINQ do klas SQL z bazy danych. Jednak klasy LINQ do SQL nie są wyświetlane w **źródeł danych** okna i nie mogą być przeciągane bezpośrednio do projektanta w celu tworzenia formantów powiązanych z danymi. Aby uzyskać więcej informacji na temat tworzenia LINQ do klas SQL z bazy danych, zobacz [porady: Tworzenie klasy programu LINQ to SQL zamapowanych na tabele i widoki (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
##  <a name="dataset"></a> Łączenie z bazą danych i tworzenie zestawu danych  
 Podczas tworzenia zestawu danych, który jest oparty na bazie danych programu Visual Studio tworzy zestaw klas, które reprezentują programowalny widok danych. Główna klasa ma nazwę *typizowany zestaw danych*. Wpisany zestaw danych zawiera obiekty tabeli danych, które reprezentują tabele w bazie danych. Aby uzyskać więcej informacji na temat zestawów, zobacz [narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Po utworzeniu zestawu danych, można utworzyć kontrolki WPF i formularze Windows powiązane z danymi przez przeciąganie obiektów dataset z okna źródeł danych do WPF lub Windows Forms designer.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-a-dataset"></a>Aby połączyć aplikację z bazą danych i tworzenie zestawu danych  
  
1.  Otwórz istniejący projekt w programie Visual Studio, lub Utwórz nowy projekt.  
  
2.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.  
  
     **Kreatora konfiguracji źródła danych** zostanie otwarty.  
  
3.  Na **wybierz typ źródła danych** wybierz opcję **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz Model bazy danych** wybierz opcję **Dataset**, a następnie kliknij przycisk **dalej**.  
  
5.  Na **wybierz połączenie danych** stronie, wybierz połączenie danych z listy dostępnych połączeń, a następnie kliknij przycisk **dalej**.  
  
     Jeśli żądane połączenie danych nie jest dostępna, należy utworzyć nowe połączenie, wykonując kroki opisane w [Tworzenie nowego połączenia z bazą danych](#CreatingDataConnection).  
  
6.  Na **Zapisz parametry połączenia do pliku konfiguracyjnym aplikacji** strony Opcjonalnie wyczyść **tak, Zapisz połączenie jako** pole wyboru, jeśli chcesz zapisać parametry połączenia bezpośrednio w skompilowanej aplikacja. Domyślnie połączenie jest zapisywany w pliku konfiguracyjnym aplikacji. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie i Edycja parametrów połączeń](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
7.  Na **wybierz obiekty bazy danych** wybierz obiekty bazy danych, które będą używane w aplikacji. Istnieje również możliwość zastąpienia domyślnej **Nazwa zestawu danych**.  
  
8.  Kliknij przycisk **Zakończ**. Właśnie utworzony zestaw danych jest teraz dostępna w **źródeł danych** okna.  
  
    > [!NOTE]
    >  Jeśli **źródeł danych** okno nie jest otwarty, kliknij przycisk **Pokaż źródła danych** na **danych** menu, aby otworzyć okno.  
  
9. Teraz można przeciągać elementy z **źródeł danych** okna Projektanta WPF, projektanta Windows Forms lub [projektanta składników](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282) do tworzenia formantów powiązanych z danymi. Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Łączenie z bazą danych i tworzenie modelu danych jednostki  
 Podczas tworzenia modelu Entity Data Model oparty na bazie danych programu Visual Studio tworzy zestaw klas, które reprezentują programowalny widok danych. Aby uzyskać więcej informacji dotyczących modeli danych jednostek i ADO.NET Entity Framework, zobacz [Omówienie programu Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
 Po utworzeniu modelu Entity Data Model, można utworzyć kontrolek WPF powiązane z danymi przez przeciąganie obiektów DataSet z okna źródeł danych do WPF lub projektanta.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-an-entity-data-model"></a>Aby połączyć aplikację z bazą danych i utworzyć model Entity Data Model  
  
1.  Otwórz istniejący projekt w programie Visual Studio, lub Utwórz nowy projekt.  
  
2.  Postępuj zgodnie z instrukcjami w **Kreator modelu Entity Data Model** połączenie z bazą danych i określić zawartość modelu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego edmx pliku](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Po ukończeniu **Kreator modelu Entity Data Model**, utworzony modelu danych jednostki zostanie otwarty w Projektancie Entity Data Model i obiekty danych są teraz dostępne w **źródeł danych** okna.  
  
    > [!NOTE]
    >  Jeśli **źródeł danych** okno nie jest otwarty, kliknij przycisk **Pokaż źródła danych** na **danych** menu, aby otworzyć okno.  
  
4.  Jeśli projektant WPF jest otwarty, można przeciągać elementy z **źródeł danych** okna Projektanta w celu tworzenia formantów, które są powiązane z modelu Entity Data Model. Aby uzyskać więcej informacji, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Jeśli projektant Windows Forms jest otwarty, nie można przeciągać elementy z **źródeł danych** do projektanta. Aby utworzyć formanty powiązane z modelem danych jednostki, należy skompilować projekt, Dodaj nowe źródło danych obiektu, który jest oparty na modelu Entity Data Model i następnie przeciągnąć te obiekty do projektanta.  
  
##  <a name="CreatingDataConnection"></a> Tworzenie nowego połączenia bazy danych  
 Kiedy używasz **Kreatora konfiguracji źródła danych**lub **Kreator modelu Entity Data Model**, należy określić połączenie z bazą danych, którego chcesz użyć. Jeśli nie masz już połączenie z bazą danych, wykonaj następujące kroki, aby utworzyć połączenie.  
  
 W poniższych instrukcjach przyjęto, zostało już rozpoczęte **Kreatora konfiguracji źródła danych** lub **Kreator modelu Entity Data Model** zgodnie z opisem w [łączenia z bazą danych i tworzenie zestawu danych ](#dataset) i [łączenia z bazą danych i tworzenie modelu danych jednostki](#edm).  
  
#### <a name="to-create-a-new-database-connection"></a>Aby utworzyć nowe połączenie bazy danych  
  
1.  Na **wybierz połączenie danych** strony **Kreatora konfiguracji źródła danych** lub **Kreator modelu Entity Data Model**, kliknij przycisk **nowe połączenie**.  
  
     Wystąpić jeden z następujących czynności:  
  
    -   Jeśli utworzono już połączenie danych w programie Visual Studio, **Dodaj połączenie** zostanie otwarte okno dialogowe.  
  
    -   Jeśli jest to pierwsze połączenie danych utworzone w programie Visual Studio **wybierz źródło danych** Wyświetla okno dialogowe. Wybierz typ bazy danych, aby nawiązać połączenie, a następnie kliknij przycisk **OK** do wyświetlenia **Dodaj połączenie** okno dialogowe.  
  
2.  W **Dodaj połączenie** okna dialogowego wprowadź żądane informacje. **Dodaj połączenie** okno dialogowe różni się dla każdego typu dostawcy danych.  
  
    > [!NOTE]
    >  Jeśli wybrane **źródła danych** w **Dodaj połączenie** okno dialogowe nie jest źródło danych, aby nawiązać połączenie, kliknij przycisk **zmiany** otworzyć **zmian danych Źródło** okna dialogowego pole, a następnie wybierz inne źródło danych.  
  
3.  W **Dodaj połączenie** okno dialogowe, kliknij przycisk **OK**.  
  
     Wróć do **wybierz połączenie danych** strony **Kreatora konfiguracji źródła danych** lub **Kreator modelu Entity Data Model**.  
  
4.  Na **wybierz połączenie danych** strony, upewnij się, że nowe połączenie danych jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
5.  Wykonaj pozostałe kroki w **Kreatora konfiguracji źródła danych** lub **Kreator modelu Entity Data Model**.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Przechowywanie poufnych informacji (takich jak hasło) może wpłynąć na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)   
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Nawiązywanie połączenia ze źródłem danych](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)