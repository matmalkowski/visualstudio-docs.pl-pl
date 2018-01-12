---
title: "Projektowanie modelu łączności danych biznesowych | Dokumentacja firmy Microsoft"
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
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe3de196219091478a30ff07d6c2f5916d423f15
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="designing-a-business-data-connectivity-model"></a>Projektowanie modelu łączności danych biznesowych
  Model usługi łączności danych biznesowych (BDC) można utworzyć przez dodanie jednostek i metody w pliku modelu. Jednostka opis kolekcji pól danych. Na przykład jednostka może reprezentować tabeli w bazie danych. Metoda wykonuje zadania, takie jak dodawanie, usuwanie i aktualizowanie danych reprezentowanego przez jednostek. Aby uzyskać więcej informacji, zobacz [integrowanie danych biznesowych do programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="adding-entities"></a>Dodawanie jednostek  
 Można dodać jednostki przez przeciąganie lub kopiowanie **jednostki** z programu Visual Studio **przybornika** do projektanta usługi łączności danych biznesowych. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Definiowanie pól jednostki w klasie. Na przykład dodać pole o nazwie `Address` do `Customer` klasy. Możesz dodać nową klasę w projekcie lub użyj istniejącej klasy utworzony przy użyciu innych narzędzi, takich jak Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych). Nazwa podmiotu i nazwę klasy, która reprezentuje jednostkę nie musi odpowiadać. Wiąże klasy się jednostki podczas definiowania metod w modelu.  
  
## <a name="adding-methods"></a>Dodawanie metody  
 Usługa BDC wywołuje metody w modelu, gdy użytkowników wyświetlać, dodawać, aktualizować lub usuwać informacje na liście lub części sieci Web, która jest oparta na modelu. Należy dodać metody do modelu dla każdego zadania, które użytkownik może wykonywać. Tworzenie metody, wybierając jedną z pięciu typów podstawowa metoda z **szczegóły metody usługi łączności danych biznesowych** okna. W poniższej tabeli opisano pięć podstawowych metod modelu usługi łączności danych biznesowych.  
  
|Metoda|Opis|  
|------------|-----------------|  
|Wyszukiwanie|Zwraca kolekcję wystąpień jednostek. Wywoływane, gdy użytkownik otwiera listy lub części sieci Web. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md).|  
|Specific Finder|Zwraca wystąpienie określonej jednostki. Wywoływane, gdy użytkownik wyświetla szczegóły określonych elementów listy. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|Kreator|Dodaje nowe dane do źródła danych jednostki. Wywołuje się, gdy użytkownicy wybiorą **nowy element** na Wstążce listę, która jest oparta na modelu. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md).|  
|Updater|Modyfikuje danych na liście. Wywoływane, gdy użytkownicy zaktualizuj informacje w postaci listy. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md).|  
|Deleter|Usuwa dane. Wywoływane, gdy użytkownicy usunąć element z listy. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## <a name="defining-method-parameters"></a>Definiowanie parametrów — metoda  
 Podczas tworzenia metody Visual Studio dodaje parametry wejściowe i wyjściowe, które są odpowiednie dla typu metody. Te parametry są tylko symbole zastępcze. W większości przypadków należy zmodyfikować parametrów, aby przekazać lub zwracać poprawny typ danych. Na przykład domyślnie metody wyszukiwania zwraca ciąg. W większości przypadków chcesz zmodyfikować parametru zwrotnego metody wyszukiwania, tak aby zwraca kolekcję jednostek. Które można wykonywać, modyfikując deskryptor typu parametru. Deskryptor typu jest Kolekcja atrybutów, która opisuje typ danych parametru. Aby uzyskać więcej informacji, zobacz [porady: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Program Visual Studio umożliwia kopiowanie deskryptory typu między parametrami w modelu. Na przykład można zdefiniować deskryptor typu o nazwie `CustomerTD` dla parametru zwrotnego z `GetCustomer` metody. Można skopiować `CustomerTD` deskryptor w typu **Eksplorator modelu BDC**, a następnie wklej tego parametr wejściowy deskryptor typu `CreateCustomer` metody. Zapobiega to konieczności więcej niż raz zdefiniować tego samego deskryptor typu.  
  
##  <a name="MethodInstances"></a>Wystąpienia — metoda  
 Podczas tworzenia metody Visual Studio dodaje wystąpienia metody domyślnej. Wystąpienie metody jest odwołaniem do metody, a także wartości domyślne dla parametrów. Pojedynczej metody mogą mieć wiele wystąpień metody. Każde wystąpienie jest kombinacją podpis metody i zestaw wartości domyślnych. Aby uzyskać więcej informacji, zobacz [porady: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Po uruchomieniu projektu metody wystąpienia są wyświetlane na liście rozwijanej powyżej listy programu SharePoint. Użytkownicy mogą wybierać wystąpień metody, aby wyświetlić dane.  
  
 Aby dodać wartości domyślne wystąpienie metody, należy bezpośrednio zmodyfikować XML modelu. Aby uzyskać więcej informacji, zobacz [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## <a name="adding-filter-descriptors"></a>Dodawanie deskryptory filtrów  
 Konsumenci modelu należy pobrać wystąpienia jednostki, które spełniają pewne kryteria. Aby włączyć tę funkcję, można dodać opisu filtru do metody. Deskryptory filtrów umożliwiają użytkownikom modelu do filtrowania zestawów wyników metody przez przekazanie wartości do metod przed ich. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie parametrów filtru do operacji dla wystąpień Limit z systemu zewnętrznego](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 Programu SharePoint zawiera kilka funkcji, które umożliwiają użytkownikom, podaj wartości filtru. Na przykład składników Web Part danych biznesowych Podaj polu tekstowym filtru. Użytkownicy, można ograniczyć danych na liście, wprowadzając wartość w polu tekstowym. Aby uzyskać więcej informacji o sposobie dodawanie opisu filtru do metody, zobacz [porady: dodawanie opisu filtru do metody wyszukiwania](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### <a name="filter-descriptor-properties"></a>Deskryptor właściwości filtru  
 Należy ustawić wartość **skojarzone deskryptor typu**, **nazwa**, i **typu** właściwości opisu filtru. Wszystkie inne właściwości są opcjonalne.  
  
 **Skojarzone deskryptor typu** właściwość dotyczy parametr wejściowy Deskryptor filtru. Gdy użytkownik poda wartość filtru, usługi BDC przekazuje tę wartość do metody za pomocą parametru wejściowego.  
  
 **Typu** właściwość opisuje filtrowania wzorzec, który ma być używany. W programie SharePoint wzorzec filtrowania, którą wybierzesz ma wpływ na tekst wyświetlany w interfejsie użytkownika (UI). Na przykład w przypadku wzorca filtrowania Komparatora tekst **jest równa** pojawia się jako kontroli nad składnika Web Part danych biznesowych. Aby uzyskać więcej informacji o każdym wzorzec filtrowania, zobacz [typy filtrów obsługiwany przez BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Aby uzyskać więcej informacji na temat właściwości opisu filtru, zobacz [filtru](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### <a name="providing-default-values"></a>Podając wartości domyślne  
 W niektórych przypadkach użytkownik nie może zawierać wartości filtru. Można podać wartość domyślną, dodając wartość domyślną do wystąpienia metody lub przez ustawienie wartości domyślnej w kodzie metodę. Aby uzyskać więcej informacji o sposobie dodawania wartości domyślnej na wystąpienie metody, zobacz [wystąpienia metody](http://go.microsoft.com/fwlink/?LinkID=169282). Na przykład jak ustawić wartość domyślna parametru wejściowego w kodzie metodę zobacz [porady: dodawanie opisu filtru do metody wyszukiwania](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## <a name="validating-the-model"></a>Sprawdzanie poprawności modelu  
 Weryfikacja z modelu, podczas tworzenia. Visual Studio identyfikuje problemy, które mogą uniemożliwić model działa zgodnie z oczekiwaniami. Te problemy występują w programie Visual Studio **listy błędów**.  
  
 Sprawdzanie poprawności modelu Otwieranie menu skrótów do projektanta usługi łączności danych biznesowych, a następnie wybierając **weryfikacji**. Jeśli model zawiera błędy, pojawią się one w **listy błędów**. Można szybko przenieść kursor do kodu, który zawiera błąd, klikając dwukrotnie błąd na liście. Alternatywnie można wybrać F8 lub Shift + F8 klucze wielokrotnie do kroku przed lub za pośrednictwem błędy na liście.  
  
 Błędy sprawdzania poprawności może wystąpić, gdy naruszenia reguły modelu w określony sposób. Na przykład jeśli **IsCollection** ma ustawioną właściwość deskryptor typu **true**, ale nie deskryptory typu podrzędnego istnieje, pojawi się błędu sprawdzania poprawności. Może być konieczne zapoznaj się z regułami modelu BDC do zrozumienia niektórych błędów, które są wyświetlane w programie Visual Studio **listy błędów**. Aby uzyskać więcej informacji o regułach modelu usługi łączności danych biznesowych, zobacz [schematu BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="debugging-the-solution-that-contains-the-model"></a>Debugowanie rozwiązania zawierającego modelu  
 Jak będzie debugowania kodu w programie Visual Studio można debugować kodu. Aby debugować kod, ustaw punkty przerwania w dowolnym miejscu w kodzie, a następnie uruchom debuger. Visual Studio otworzy w witrynie programu SharePoint. W programie SharePoint należy utworzyć listę lub składnik Web Part, który używa danych biznesowych. Następnie można przejrzeć kod. Aby uzyskać więcej informacji o debugowaniu projektów SharePoint, zobacz [Rozwiązywanie problemów z rozwiązań SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 Można również debugowania kodu w zestawów niestandardowych, które można dodać do projektu. Jednak do debugowania kodu w zestawie niestandardowym, należy dodać zestawu do pakietu rozwiązania. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie zestawów dodatkowych](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Aby uzyskać więcej informacji na temat dodawania niestandardowego zestawu do projektu, zobacz [porady: Dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### <a name="configuring-bdc-security"></a>Konfigurowanie zabezpieczeń BDC  
 Może być konieczne przed debugowaniem rozwiązania zmodyfikować ustawienia zabezpieczeń w programie SharePoint. Aby zmodyfikować te ustawienia, Otwórz aplikację usługi łączności danych biznesowych w SharePoint 2010 centralnej administracji witrynę sieci Web. W **Ustaw uprawnienia magazynu metadanych** okno dialogowe Dodawanie konta użytkownika, a następnie wybierz jedną z następujących opcji:  
  
|Zadanie|Opcja|  
|----------|------------|  
|Aby wdrożyć modele usługi BDC.|Edytowanie|  
|Do tworzenia list i składników Web Part za pomocą zewnętrznego (jednostki) typy zawartości do modelu.|Wybór spośród klientów|  
|Do tworzenia, odczytu, aktualizacji i usuwania danych jednostki.|Wykonanie|  
  
 Aby uzyskać więcej informacji o tych ustawieniach, zobacz [zarządzania usługi łączności danych biznesowych](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 Można również ustawić uprawnień zabezpieczeń dla poszczególnych modeli lub typów zawartości zewnętrznej. Aby uzyskać więcej informacji na temat ustawiania uprawnień zabezpieczeń dla modelu, zobacz [zarządzania modelu BDC](http://go.microsoft.com/fwlink/?LinkID=178884). Aby uzyskać więcej informacji na temat sposobu ustawiania uprawnień zabezpieczeń dla typu zawartości zewnętrznej, zobacz [typu zawartości zewnętrznej zarządzania](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Debugowanie rozwiązania lokalnego serwera programu SharePoint przy użyciu tych ustawień. Aby uzyskać więcej informacji o sposobie konfigurowania ustawień związanych z BDC zabezpieczeń na serwerze produkcyjnym programu SharePoint, zobacz [Omówienie zabezpieczeń usługi łączności danych biznesowych](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### <a name="retracting-models-that-become-corrupt"></a>Odwołaniem modeli, które uszkodzona  
 Podczas pierwszego uruchomienia debugera, program Visual Studio wdroży całego modelu w programie SharePoint. Za każdym razem po tej dacie Visual Studio aktualizuje wszystkie zmiany wprowadzone między wdrożeniami modelu w programie SharePoint.  
  
 Mogą wystąpić sytuacje wymagające Visual Studio, aby wycofać całkowicie modelu z programu SharePoint. Na przykład modelu może być uszkodzona.  Można wdrożyć ponownie modelu do programu SharePoint, należy ustawić **aktualizacji przyrostowej** właściwości modelu do **False**, a następnie uruchom debuger. **Aktualizacji przyrostowej** właściwość jest widoczna w **właściwości** okna po wybraniu węzła, który reprezentuje model w programie **Eksplorator modelu BDC**. Domyślnie nazwa modelu jest **BdcModel1**.  
  
### <a name="changing-identifier-names-of-entities-in-the-model"></a>Zmiana nazwy identyfikatorów jednostek w modelu.  
 Jeśli zmienisz nazwę identyfikatora po wdrożeniu modelu, zostanie zgłoszony błąd wdrażania. Nie można rozwiązać ten problem, ustawiając **aktualizacji przyrostowej** właściwości modelu do **False**. Ręcznie wycofać modelu, a następnie wykonaj ponowne wdrożenie rozwiązania. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z rozwiązań SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). Tego błędu można uniknąć, ustawiając **aktualizacji przyrostowej** właściwości **False** przed wdrożeniem początkowo modelu.  
  
## <a name="locating-documentation-for-bdc-model-elements"></a>Lokalizowanie dokumentacji dla elementów modelu BDC  
 Visual Studio dodaje XML element do modelu dla każdej jednostki, metody lub inny element, który można utworzyć. Atrybuty elementu są wyświetlane jako właściwości **właściwości** okna. Informacje dotyczące elementów i atrybutów, które generuje Visual Studio podczas projektowania modelu, zobacz [schematu BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)|Zawiera opis narzędzi, które służą do wizualnego projektowania modelu zapasowego kontrolera domeny.|  
|[Instrukcje: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)|Pokazuje, jak dodać typy zawartości zewnętrznej lub jednostki do modelu.|  
|[Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)|Pokazuje, jak dodać metodę, która umożliwia użytkownikom wyświetlanie listy jednostek na liście lub części sieci Web.|  
|[Instrukcje: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)|Pokazuje, jak dodać metodę, która umożliwia użytkownikom wyświetlić szczegóły określonej jednostki.|  
|[Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)|Pokazuje, jak dodać metodę, która umożliwia użytkownikom do dodawania rekordów do źródła danych bezpośrednio z listy lub części sieci Web.|  
|[Instrukcje: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)|Pokazuje, jak dodać metodę, która umożliwia użytkownikom usunąć dane ze źródła danych za pomocą opcji w interfejsie użytkownika (UI) listy lub części sieci Web.|  
|[Instrukcje: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)|Pokazuje, jak dodać metodę, która umożliwia użytkownikom zmianę rekordów danych w źródle danych bezpośrednio z listy lub części sieci Web.|  
|[Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Pokazuje, jak dodać parametry wejściowe i zwracany do metody za pomocą metody okno Szczegóły programu Visual Studio.|  
|[Instrukcje: Określanie deskryptora typu dla parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Pokazuje, jak zdefiniować typy danych parametru w modelu.|  
|[Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)|Przedstawia sposób tworzenia wystąpienia metody, która wykonuje BDC.|  
|[Instrukcje: Dodawanie deskryptora filtru do metody wyszukiwania](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Pokazuje, jak umożliwić użytkownikom ograniczyć liczbę wystąpień zwrócona przez metodę wyszukiwania.|  
|[Tworzenie skojarzenia między jednostkami](../sharepoint/creating-an-association-between-entities.md)|W tym artykule opisano, jak można zdefiniować relacji między jednostkami w modelu. Składniki Web Part danych biznesowych, list zewnętrznych i niestandardowe aplikacje można wyświetlić relacje tych danych w interfejsie użytkownika (UI).|  
|[Porady: Tworzenie skojarzenia między jednostkami](../sharepoint/how-to-create-an-association-between-entities.md)|Pokazuje, jak zdefiniować relacje między obiektami w modelu.|  
|[Przewodnik: Tworzenie listy zewnętrznej w SharePoint za pomocą danych biznesowych](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Zawiera instrukcje krok po kroku opisano sposób tworzenia i testowania modelu, który wyświetla kontakty w zewnętrznych listy programu SharePoint.|  
|[Integrowanie danych biznesowych z SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Omówienie tworzenia i projektowania modele usługi BDC.|  
  
  