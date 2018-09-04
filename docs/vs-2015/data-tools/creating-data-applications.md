---
title: Tworzenie aplikacji do danych | Dokumentacja firmy Microsoft
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
- data access [Visual Studio], creating applications
- applications [Visual Studio], data
- data [Visual Studio]
- data [Visual Studio], creating applications
ms.assetid: ab334d5f-4f49-4346-bce0-3325d6130b3e
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 9e662eedef9053a460ffbb5012a079f05239a9a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682897"
---
# <a name="creating-data-applications"></a>Tworzenie aplikacji danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio udostępnia wiele narzędzi projektowania, aby pomóc w tworzeniu aplikacji uzyskujących dostęp do danych. To wprowadzenie przedstawia omówienie podstawowych procesów związanych z tworzeniem aplikacji, które działają z danymi. W tym miejscu informacje celowo wiele szczegółów i został zaprojektowany jako źródło informacji ogólnych i punkt wyjścia do wielu innych stron pomocy związanych z tworzeniem aplikacji danych.  
  
 Podczas tworzenia aplikacji uzyskujących dostęp do danych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], będzie miała inne wymagania. W niektórych przypadkach można po prostu wyświetlanie danych w formularzu. W innych przypadkach może być konieczne opracowanie sposobu udostępniania informacji z innymi aplikacjami lub procesami.  
  
 Niezależnie od tego, co możesz zrobić z danymi istnieją pewne podstawowe pojęcia, które należy zrozumieć. Nigdy nie potrzebować znać niektórych szczegółów przetwarzania danych — na przykład może nigdy nie należy programowo utworzyć bazy danych — ale to bardzo przydatne do zrozumienia pojęcia podstawowe dane, a także narzędzia data tools (kreatory i projektanci) dostępne w <c1/>.  
  
 Aplikacja typowych danych wykorzystuje większość procesów przedstawionych na poniższym diagramie:  
  
 ![Grafika przedstawiająca cykl danych](../data-tools/media/datacyclegraphicinfo.gif "datacyclegraphicinfo")  
Cykl danych  
  
 Jak utworzyć aplikację, można traktować zadanie, które mają być osiągnięte. Użyj poniższych sekcji, aby ułatwić znalezienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi i obiektów, które są dostępne dla Ciebie.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapewnia kreatory upraszczające niektóre procesy ukazane na poprzednim rysunku. Aby na przykład uruchomić **Kreatora konfiguracji źródła danych** zapewni aplikacji wystarczająco informacji, aby połączyć się z danymi, utworzyć typizowany zestaw danych do odbierania danych i przenieść dane do aplikacji.  
  
 Aby szybko wyświetlić jak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pomaga w opracowywaniu danych aplikacji, zobacz [wskazówki: Tworzenie prostej aplikacji danych](http://msdn.microsoft.com/library/c5d0968c-d86f-4ae9-a2e1-871f208a3bb3).  
  
## <a name="connecting-to-data"></a>Łączenie z danymi  
 Przenoszenie danych do aplikacji (i wysłać zmiany z powrotem do źródła danych), pewnego rodzaju komunikacja dwukierunkowa musi zostać ustanowione. Ta dwukierunkowa komunikacja jest zazwyczaj obsługiwana przez obiekty w modelu danych.  
  
 Na przykład `TableAdapter` łączy aplikacje, które używają zestawów danych w bazie danych, a <xref:System.Data.Objects.ObjectContext> łączy jednostki w programie Entity Framework z bazą danych. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] udostępnia kilka narzędzi, które pomagają w tworzeniu połączeń, które mogą być używane przez aplikację. Aby uzyskać więcej informacji na temat łączenia aplikacji z danymi, zobacz [o łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md).  
  
 Aby dowiedzieć się, jak używać zestawów danych, aby połączyć aplikację z danymi w bazie danych, zobacz [wskazówki: łączenie z danymi w bazie danych (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c).  
  
## <a name="preparing-your-application-to-receive-data"></a>Przygotowywanie aplikacji na otrzymywanie danych  
 Jeśli aplikacja używa modelu danych odłączonych, trzeba tymczasowo przechowywać dane w aplikacji, podczas pracy z nim. Program Visual Studio zapewnia narzędzia pomagające tworzyć obiekty, których aplikacja używa do tymczasowego przechowywania danych: zestawy danych, podmioty, i [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] obiektów.  
  
> [!NOTE]
>  Aplikację, która używa modelu danych odłączonych będą zwykle połączenie z bazą danych, uruchamiać zapytanie dotyczące wprowadzania danych do aplikacji, odłącz od bazy danych i następnie manipulować danymi w trybie offline przed ponownym podłączeniem i zaktualizowaniem bazy danych.  
  
 Aby uzyskać więcej informacji na temat tworzenia typizowanych zestawów danych w aplikacji, zobacz [przygotowywanie aplikacji do odbierania danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad). Aby uzyskać dodatkowe informacje na temat używania zestawów danych w aplikacjach n warstwowych, zobacz [oddzielanie zestawów danych i TableAdapters do różnych projektów](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md).  
  
 Aby dowiedzieć się, jak utworzyć zestaw danych, wykonaj procedury opisane w [wskazówki: Tworzenie zestawu danych w Projektancie obiektów Dataset](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
 Aby dowiedzieć się, jak utworzyć [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] obiektów, wykonaj procedury w [wskazówki: Tworzenie klasy programu LINQ to SQL (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="fetching-data-into-your-application"></a>Pobieranie danych do aplikacji  
 Czy Twoja aplikacja używa modelu danych odłączonych, czy nie, musisz być w stanie pobierać dane do aplikacji. Wprowadzasz dane do aplikacji przez wykonanie zapytań lub procedur składowanych w bazie danych. Za pomocą aplikacji, które przechowują dane w zestawach danych, wykonują kwerendy i procedury składowane `TableAdapter`s, natomiast aplikacje, które przechowują dane w jednostkach, wykonują kwerendy za pomocą [składnik LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d) lub łącząc podmioty bezpośrednio do procedur składowanych. Aby uzyskać więcej informacji na temat tworzenia i edytowania zapytań, które używają adapterów tabel, zobacz [porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md) i [jak: Edit TableAdapter Queries](../data-tools/how-to-edit-tableadapter-queries.md).  
  
 Aby uzyskać więcej informacji na temat ładowania danych do zestawów danych i wykonywania zapytań i procedur składowanych, zobacz [pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md).  
  
 Aby dowiedzieć się, jak załadować dane do zestawu danych, wykonaj procedury opisane w [wskazówki: wyświetlanie danych w formularzu Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md) i sprawdź kod w obsłudze zdarzeń formularz ładowanie.  
  
 Aby dowiedzieć się, jak załadować dane do [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] obiektów, wykonaj procedury w [wskazówki: Tworzenie klasy programu LINQ to SQL (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
 Aby dowiedzieć się, jak tworzyć i wykonywać zapytania SQL, zobacz [porady: tworzenie i wykonywanie instrukcji SQL, że zwraca wiersze](http://msdn.microsoft.com/library/14637fc5-d42a-4cca-97ac-54c181ec3eed).  
  
 Aby dowiedzieć się, jak wykonać procedurę przechowywaną, zobacz [porady: wykonywanie procedury składowane tego zwraca wiersze](http://msdn.microsoft.com/library/db3d7021-d3ef-4db8-b12a-b6146570355d).  
  
## <a name="displaying-data-on-forms"></a>Wyświetlanie danych w formularzach  
 Po wprowadzeniu danych do aplikacji, możesz będą one zazwyczaj wyświetlane w formularzu dla użytkowników wyświetlić lub zmodyfikować. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] udostępnia [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992), gdzie elementy można przeciągać do formularzy w celu automatycznego tworzenia formantów powiązanych z danymi, wyświetlających dane. Aby uzyskać więcej informacji o wiązaniu danych i wyświetlaniu danych użytkownikom, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Aby dowiedzieć się, jak prezentować użytkownikom dane, wykonaj procedury opisane w poniższych instruktażach (zwracając szczególną uwagę na proces przeciągania elementów z **źródeł danych** okna):  
  
-   [Wskazówki: Wyświetlanie danych w formularzu Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
-   [Powiązywanie kontrolek WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)  
  
-   [Wskazówki: Powiązywanie kontrolek Silverlight z usługi danych WCF](http://msdn.microsoft.com/library/f3f08661-7d91-4185-8ed6-912d524d4c6b)  
  
## <a name="editing-data-in-your-application"></a>Edytowanie danych w aplikacji  
 Gdy użytkownikom zostaną przedstawione dane, prawdopodobnie zmodyfikują je przez dodawanie nowych rekordów oraz edytowanie i usunięcie rekordów przed wysłaniem danych z powrotem do bazy danych.  
  
 Aby uzyskać więcej informacji na temat pracy z danymi po ich załadowaniu do zestawu danych, zobacz [edycji danych w aplikacji](../data-tools/editing-data-in-your-application.md).  
  
## <a name="validating-data"></a>Sprawdzanie poprawności danych  
 Podczas wprowadzania zmian w danych, będzie zazwyczaj chcesz zweryfikować zmiany przed zezwoleniem na wartości, które mają być przyjęte do zestawu danych lub zapisywane w bazie danych. *Sprawdzanie poprawności* jest nazwą procesu w celu sprawdzenia, czy te nowe wartości są akceptowalne dla wymagań aplikacji. Możesz dodać logikę do sprawdzenia wartości w aplikacji w miarę jak ulegają zmianom. Visual Studio zapewnia narzędzia, które pomagają w dodawaniu kodu, który sprawdza poprawność danych podczas zmiany wierszy i kolumn. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e).  
  
 Aby dowiedzieć się, jak dodać sprawdzanie poprawności danych do aplikacji, zobacz [wskazówki: Dodawanie sprawdzania poprawności do zestawu danych](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
 Aby dowiedzieć się, jak dodać sprawdzanie poprawności do zestawu danych, który jest podzielony aplikacji n-warstwowej, zobacz [Dodawanie walidacji do warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## <a name="saving-data"></a>Zapisywanie danych  
 Po wprowadzeniu zmian w aplikacji (i sprawdzeniu poprawności tych zmian), zazwyczaj chcesz wysłać zmiany z powrotem do bazy danych. Aplikacje, które zazwyczaj przechowują dane w zestawach danych za pomocą TableAdapterManager, aby zapisać dane. Aby uzyskać więcej informacji, zobacz [TableAdapterManager — Przegląd](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650). Aplikacje Entity Framework używają <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metodę, aby zapisać dane.  
  
 Aby uzyskać więcej informacji dotyczących wysyłania zaktualizowanych danych z powrotem do bazy danych, zobacz [zapisywanie danych](../data-tools/saving-data.md).  
  
 Aby dowiedzieć się, jak wysyłać zaktualizowane dane z zestawu danych do bazy danych, wykonaj procedury opisane w [wskazówki: zapisywanie danych z powiązanych tabel danych (hierarchiczna aktualizacja)](http://msdn.microsoft.com/library/50601bd7-a488-480c-9910-3c6570fa3a1b).  
  
## <a name="related-topics"></a>Tematy pokrewne  
 [Przegląd aplikacji w programie Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)  
 Zawiera łącza do tematów opisujących sposób tworzenia aplikacji, które działają z danymi.  
  
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)  
 Zawiera łącza do tematów dotyczących sposobu używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do łączenia aplikacji z danymi i tworzenia źródeł danych dla aplikacji.  
  
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 Zawiera łącza do tematów, które opisują sposób pracy z modelami danych w aplikacji, w tym zestawy danych i modeli danych jednostek.  
  
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)  
 Zawiera łącza do tematów opisujących sposób ładowania danych do aplikacji.  
  
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 Zawiera łącza do tematów, które wyjaśniają, jak do powiązania Windows kontrolek formularzy, kontrolek WPF i formanty programu Silverlight ze źródłami danych.  
  
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)  
 Zawiera łącza do tematów opisujących sposób zmiany danych w aplikacji.  
  
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 Zawiera łącza do tematów opisujących sposób dodawania sprawdzania poprawności do zmian danych.  
  
 [Zapisywanie danych](../data-tools/saving-data.md)  
 Zawiera łącza do tematów, które wyjaśniają, jak wysyłać zaktualizowane dane z aplikacji z bazą danych lub jak zapisać je do innych formatów, takich jak XML.  
  
 [Narzędzia do pracy ze źródłami danych w programie Visual Studio](http://msdn.microsoft.com/library/1e584c75-900a-49a0-a82a-d19172ef2eb3)  
 Zawiera łącza do tematów o narzędziach, których można użyć do pracy ze źródłami danych w programie Visual Studio, takich jak **źródeł danych** okna i Projektant modelu danych jednostki ADO.NET.