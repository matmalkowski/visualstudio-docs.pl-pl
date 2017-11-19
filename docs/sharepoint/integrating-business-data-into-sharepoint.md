---
title: Integrowanie danych biznesowych programu SharePoint | Dokumentacja firmy Microsoft
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ece3128c2d6850a1d1dd22d0328a4ee2c46da2b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="integrating-business-data-into-sharepoint"></a>Integrowanie danych biznesowych z SharePoint
  Dane biznesowe można zintegrować programu SharePoint. Dane biznesowe mogą pochodzić z wewnętrznego serwera aplikacji, takich jak [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel i SAP, lub usługi sieci Web. Użytkowników można wyświetlić, dodawać, aktualizować lub usuwać dane biznesowe za pomocą list zewnętrznych lub składników Web Part danych biznesowych w programie SharePoint.  Użytkownicy mogą również dostęp do tych danych w trybie offline w aplikacji pakietu Microsoft Office, takich jak Microsoft Outlook. Aby uzyskać więcej informacji, zobacz [gdzie można można wyświetlić danych zewnętrznych](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Do integracji danych programu SharePoint, należy utworzyć model usługi łączności danych biznesowych (BDC). Usługa BDC jest aplikacja programu SharePoint, która przechowuje informacje dotyczące danych w aplikacjach biznesowych. Aby uzyskać więcej informacji, zobacz [usługi łączności danych biznesowych (BDC)](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Modele w programie Visual Studio  
 Modele w programie Visual Studio umożliwia pisanie kodu niestandardowego, pobierania i aktualizowania danych ze źródeł danych zaplecza. Można również agregacji danych z wielu źródeł danych. Na przykład można wyświetlić listę klientów, które zawiera dane z [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] bazy danych i usługi sieci Web.  
  
 Możesz również zaimportować modeli, które są już wdrożone w programie SharePoint. Po zaimportowaniu modelu, można dodać kod niestandardowy lub tylko pakiet, a następnie Wdróż model do wielu farm serwerów programu SharePoint za pomocą programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="designing-a-model-in-visual-studio"></a>Projektowanie modelu w programie Visual Studio  
 Model można zaprojektować przy użyciu projektanta i kilka okien narzędzi. Podczas projektowania modelu programu Visual Studio generuje plik XML modelu. Aby uzyskać więcej informacji, zobacz [omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Model zawiera jednostki i metod.  
  
### <a name="entities"></a>Jednostki  
 Jednostka opis kolekcji pól. Na przykład jednostka może reprezentować tabeli w bazie danych. Jednostka jest wyświetlany jako typu zawartości zewnętrznej w programie SharePoint. Aby uzyskać więcej informacji na temat typów zawartości zewnętrznej, zobacz [co to są typy zawartości zewnętrznej?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Metody  
 Metoda umożliwia konsumentów typu zawartości zewnętrznej do wykonania akcji w polach jednostki. Na przykład metody Updater może umożliwić użytkownikom zmienić adres i urodzenia Data klienta gdzie `Address` i `BirthDate` są pola `Customer` jednostki.  
  
 Program Visual Studio generuje plik kodu usługi dla każdej jednostki w modelu. Po dodaniu metody modelu programu Visual Studio generuje odpowiedniej metody w pliku kodu usługi. Dodaj kod do każdej metody do wykonywania odpowiednich zadań. Na przykład jeśli Dodawanie metody Creator do modelu, Visual Studio generuje metody Creator w pliku kodu usługi. Ta metoda jest wywoływana przez usługę BDC, gdy użytkownik kliknie **nowy element** przycisku na liście, który jest oparty na modelu. W związku z tym dodać kod do metody Creator, który dodaje nowe dane ze źródłem danych. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)|Pokazuje, jak utworzyć nowy model lub zaimportować do modelu, który można eksportować z programu SharePoint.|  
|[Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)|Wyjaśniono, jak zaprojektować elementy modelu przy użyciu narzędzi do projektowania programu Visual Studio.|  
|[Kiedy vs Użyj programu SharePoint Designer. Visual Studio w przypadku tworzenia rozwiązania z wykorzystaniem usług łączności Biznesowej](http://go.microsoft.com/fwlink/?LinkID=183448)|Pomoże Ci zdecydować, czy należy użyć programu Visual Studio lub użyj programu SharePoint Designer do tworzenia modeli dla usługi łączności danych biznesowych.|  
  
  