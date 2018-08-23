---
title: Łączenie z danymi w Windows Forms aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- System.Data.SqlClient.SqlConnection
- System.Data.Odbc.OdbcConnection
- System.Data.OleDb.OleDbConnection
- System.Data.OracleClient.OracleConnection
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connection objects, tools for working with
- OleDbConnection class, ADO.NET connection objects
- databases [Visual Studio], connecting to
- data adapters, connections
- connection pooling, ADO.NET connections
- connection strings [Visual Studio], ADO.NET
- connection objects, types of
- dynamic properties, ADO.NET connections
- connections, about connections
- data [Visual Studio], connecting
- design-time connections
- connections, design-time
- TableAdapters, connections
- connection objects
- SqlConnection class, ADO.NET connection objects
- connecting to databases, ADO.NET connections
- transactions, ADO.NET
- database connections [Visual Studio], ADO.NET
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d1132ee07e892886e49fbaa4670b309afc448da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690837"
---
# <a name="connecting-to-data-in-windows-forms-applications"></a>Łączenie z danymi w aplikacjach Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] udostępnia narzędzia, aby połączyć aplikację z danymi z wielu różnych źródeł, takich jak bazy danych, usług sieci web i obiektami. Jeśli używasz narzędzia do projektowania danych w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], często nie trzeba jawnie Utwórz obiekt połączenia danych formularza lub składnika. Obiekt połączenia jest zwykle tworzony wyniku przeczytanie jednego z kreatorów danych lub przeciągając obiekty danych na formularzu. Aby połączyć aplikację z danymi w bazie danych, usługi sieci web lub obiektu, należy uruchomić [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) , wybierając **Dodaj nowe źródło danych** z [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Na poniższym diagramie przedstawiono przepływ standardowych operacji, podczas nawiązywania połączenia z danymi, wykonując zapytanie TableAdapter w celu pobrania danych i wyświetlić je na formularzu w aplikacji Windows.  
  
 ![Przepływ danych w aplikacji klienckiej](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 W niektórych sytuacjach jest wygodne utworzyć obiekt połączenia bez pomocy dowolnego narzędzia do projektowania danych. Informacje na temat tworzenia połączeń programowo, zobacz [nawiązania połączenia ze źródłem danych](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e).  
  
> [!NOTE]
>  Aby uzyskać informacje na temat łączenia aplikacji sieci web z danymi, zobacz [Mapa zawartości dostępu do danych ASP.NET](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## <a name="walkthroughs-for-connecting-windows-forms-applications-to-data"></a>Wskazówki dotyczące łączenia usługi Windows Forms aplikacji do danych  
 Poniższe przewodniki zawierają procedury związane z o łączeniu z danymi w aplikacjach Windows Forms:  
  
-   [Wskazówki: Łączenie z danymi w bazie danych (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)  
  
-   [Wskazówki: Łączenie z danymi w pliku lokalnej bazy danych (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [Wskazówki: Łączenie z danymi w usłudze sieci Web (Windows Forms)](http://msdn.microsoft.com/library/079fb9b0-c733-40c1-acd1-d0d68834354d)  
  
-   [Wskazówki: Łączenie z danymi w obiektach (formularze Windows)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)  
  
-   [Łączenie z danymi w bazie danych programu Access (formularze Windows)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## <a name="creating-connections"></a>Tworzenie połączeń  
 W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], połączenia są skonfigurowane przy użyciu **Dodawanie/modyfikowanie połączenia** okno dialogowe. **Dodaj połączenie** podczas edytowania lub tworzenia połączeń w ramach jednego z kreatorów danych pojawi się okno dialogowe lub [Server Explorer/Eksploratorze bazy danych](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) lub podczas edytowania właściwości połączenia w **właściwości** okna.  
  
 Połączenia danych są konfigurowane automatycznie, kiedy wykonujesz jedno z następujących czynności.  
  
|Akcja|Opis|  
|------------|-----------------|  
|Uruchom [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).|Połączenia są skonfigurowane, po wybraniu ścieżki bazy danych w **Kreatora konfiguracji źródła danych**. Aby uzyskać więcej informacji, zobacz [porady: łączenie z danymi w bazie danych](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Uruchom [Kreator konfiguracji TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8).|Połączenia są tworzone w ramach **Kreator konfiguracji TableAdapter**. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md).|  
|Uruchom [Edycja TableAdapters](../data-tools/editing-tableadapters.md).|Połączenia są tworzone w ramach **Kreatora konfiguracji zapytania TableAdapter**. Aby uzyskać więcej informacji, zobacz [porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).|  
|Przeciągnij elementy z [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) w formularzu lub [projektanta składników](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282).|Obiekty połączenia są tworzone podczas przeciągania elementów z **źródeł danych** okna na **Windows Forms Designer** lub **projektanta składników**. Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Dodawanie nowego połączenia danych z [Server Explorer/Eksploratorze bazy danych](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d).|Połączenia danych w **Server Explorer/Eksploratorze bazy danych** pojawiają się na liście dostępnych połączeń w ramach tych kreatorów danych|  
  
## <a name="connection-strings"></a>Parametry połączenia  
 Parametry połączenia mogą być przechowywane w ramach aplikacji skompilowanych lub w pliku konfiguracyjnym aplikacji. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie i Edycja parametrów połączeń](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
## <a name="connection-information-and-security"></a>Informacje o połączeniu i zabezpieczenia  
 Ponieważ otwarcie połączenia obejmuje uzyska dostęp do ważnych zasobów — bazy danych — często są zaangażowane w konfigurowaniu i stosowaniu połączenia problemy z zabezpieczeniami.  
  
 Jak zabezpieczyć aplikację i jego dostęp do źródła danych zależy od architektury systemu. W aplikacji sieci web na przykład użytkownicy zazwyczaj Pobierz anonimowego dostępu do programu Internet Information Services (IIS) i w związku z tym nie są oferowane poświadczenia zabezpieczeń. W takim przypadku aplikacja przechowuje informacje logowania i używa go, a nie wszystkie informacje określonego użytkownika, aby otworzyć połączenie i dostęp do bazy danych.  
  
> [!IMPORTANT]
>  Przechowywanie parametrów połączenia szczegóły, takie jak hasła mogą wpływać na bezpieczeństwo aplikacji. Korzysta ze zintegrowanych zabezpieczeń Windows jest Bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
 W sieci intranet lub wielowarstwowych aplikacji możesz korzystać z zalet opcję Zintegrowane zabezpieczenia udostępniane przez Windows, usługi IIS i SQL Server. W tym modelu poświadczeń uwierzytelniania użytkownika dla sieci lokalnej są również używane do dostępu do zasobów bazy danych, a nie nazwa użytkownika lub hasło jest używany w parametrach połączenia. Zazwyczaj uprawnienia są określane na komputerze serwera bazy danych za pomocą grup, dzięki czemu nie trzeba ustanowić indywidualne uprawnienia dla wszystkich użytkowników, którzy mogą uzyskiwać dostęp do bazy danych. W tym modelu nie należy przechowywać na wszystkich informacji logowania dla połączenia, a żadnych dodatkowych czynności wymaganych do ochrony informacji o parametrach połączenia.  
  
 Aby uzyskać więcej informacji na temat zabezpieczeń zobacz następujące tematy:  
  
-   [Zabezpieczanie aplikacji ADO.NET](http://msdn.microsoft.com/library/005a1d43-6ee5-471e-ad98-1d30a44d49d5)  
  
-   [Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms](http://msdn.microsoft.com/library/3cd3e55b-2f5e-40dd-835d-f50f7ce08967)  
  
## <a name="design-time-connections-in-server-explorerdatabase-explorer"></a>Połączenia czasu projektowania w Server Explorer/Eksploratorze bazy danych  
 **Server Explorer/Eksploratorze bazy danych** umożliwia tworzenie projektowania połączeń ze źródłami danych. Pozwala na przeglądanie dostępnych źródeł danych; Wyświetlanie informacji o tabele, kolumny i inne elementy, które zawierają; edytowanie i tworzenie elementów bazy danych.  
  
 Aplikacja nie bezpośrednio przy użyciu połączeń dostępnych w **Server Explorer/Eksploratorze bazy danych**. Te połączenia są używane przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do pracy z bazą danych w czasie projektowania. Aby uzyskać więcej informacji, zobacz [narzędzia graficzne bazy danych](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Na przykład w czasie projektowania może użyć **Server Explorer/Eksploratorze bazy danych** do utworzenia połączenia z bazą danych. Później, podczas projektowania formularza, użytkownik może przeglądać bazę danych, wybierz kolumny z tabeli i przeciągnij je na [Projektanta obiektów Dataset](../data-tools/creating-and-editing-typed-datasets.md). Spowoduje to utworzenie [TableAdapter](../data-tools/tableadapter-overview.md) w zestawie danych. Tworzy nowy obiekt połączenia, który jest częścią nowo utworzony obiekt TableAdapter.  
  
 Informacje dotyczące połączenia czasu projektowania są przechowywane na komputerze lokalnym, niezależnie od określonego projektu lub rozwiązania. Dlatego po ustanowieniu połączenia czasu projektowania podczas pracy w aplikacji, pojawi się on **Server Explorer/Eksploratorze bazy danych** zawsze, gdy użytkownik pracuje w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], tak długo, jak serwera, z którym połączenie nie jest dostępny punkt. Aby uzyskać więcej informacji, zobacz [porady: połączenie z bazą danych za pomocą Eksploratora serwera](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../includes/sqlobjectexplorer-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Porady: łączenie z danymi w bazie danych](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Wskazówki: Łączenie z danymi w bazie danych (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Mapa zawartości dostępu do danych w programie ASP.NET](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)