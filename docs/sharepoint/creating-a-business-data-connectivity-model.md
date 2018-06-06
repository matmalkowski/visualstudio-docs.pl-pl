---
title: Tworzenie modelu łączności danych biznesowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c80d6f3e76d20e4b5a15af162ea4581b03999e61
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765193"
---
# <a name="create-a-business-data-connectivity-model"></a>Tworzenie modelu łączności danych biznesowych
  Można utworzyć modelu łączności danych biznesowych (BDC) lub dostosowanie istniejącego modelu BDC przy użyciu programu Visual Studio. Każdy projekt programu SharePoint może zawierać tylko jeden model. Aby uzyskać więcej informacji, zobacz [integrowanie danych biznesowych do programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="create-a-new-model"></a>Utwórz nowy model
 Aby utworzyć nowy model, utworzyć **modelu łączności danych biznesowych** lub Dodaj **modelu łączności danych biznesowych** elementu do **pusty projekt SharePoint**.  
  
> [!NOTE]  
>  Musi mieć [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zainstalowany na tym komputerze.  
  
 Visual Studio dodaje folder do projektu. Ten folder ma nazwę, którą określisz dla **modelu łączności danych biznesowych** elementu **Dodaj nowy element** okno dialogowe. Jeśli tworzysz nową **modelu łączności danych biznesowych** projektu programu Visual Studio nazwy folderu **BdcModel1**.  
  
 Visual Studio dodaje następujące pliki do nowego folderu:  
  
|Plik|Opis|  
|----------|-----------------|  
|Plik definicji modelu|Zawiera kod XML, który definiuje jednostek, metod obiektów systemowych Linia biznesowych (LOB) i innych metadanych, które opisują modelu.<br /><br /> Modyfikowanie metadanych w tym pliku przy użyciu narzędzia Projektant BDC **Eksplorator modelu BDC**, **szczegóły metody usługi łączności danych biznesowych** okno i **właściwości** okna.|  
|Plik kodu usługi jednostki|Zawiera metody stanowiące pobrać, aktualizowanie i usuwanie wystąpienia jednostki domyślnej.|  
  
 Aby zdefiniować właściwości jednostki, Edytuj plik kodu jednostki. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Aby pobrać, aktualizowanie i usuwanie wystąpienia jednostki, należy dodać kod do pliku kodu usługi jednostki. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Podczas kompilowania projektu programu Visual Studio tworzy zestawu. Upewnij się, czy nie dodawaj innych elementów do projektu, który Dodawanie kodu do zestawów projektu (na przykład: **sekwencyjnego przepływu pracy** elementu lub **składnika Web Part** elementu). Nie można uruchomić kod dla tego elementu, podczas wdrażania rozwiązania, ponieważ pakiet rozwiązania nie kopiuje zestawu w pamięci podręcznej GAC.  Pakiet rozwiązania wdraża zestaw BDC tylko na bazę danych w programie SharePoint.  
  
> [!NOTE]  
>  Podczas debugowania projektu programu Visual Studio kopiuje do zestawu do zarówno w lokalizacji na komputerze lokalnym.  
  
## <a name="add-an-existing-model"></a>Dodawanie istniejącego modelu
 Możesz zaimportować modelu, który został utworzony przy użyciu innych narzędzi, takich jak SharePoint Designer. Można także zaimportować istniejący model do projektu w następujących sytuacjach:  
  
-   Aby dostosować modelu, który jest już wdrożony do farmy programu SharePoint.  
  
-   Do pakietu i wdrażanie istniejącego modelu dla wielu farm serwerów programu SharePoint.  
  
 W obu przypadkach systemów LOB zdefiniowanego w modelu, który można zaimportować nie dotyczy i będą nadal działać zgodnie z oczekiwaniami. Aby dodać istniejącego modelu do projektu SharePoint, należy użyć programu Visual Studio **Dodaj istniejący element** okno dialogowe. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie istniejącego modelu BDC do projektu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
 System LOB zestawu .NET Framework typu można dodać do importowanego modelu, zaznaczając odpowiednią opcję w **zestawu .NET dodać LOB**. Umożliwia pisanie kodu niestandardowego i zdefiniuj metadanych dla importowanego modelu przy użyciu projektanta.  
  
## <a name="related-topics"></a>Tematy pokrewne
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md)|Pokazuje, jak utworzyć nowy model usługi łączności danych biznesowych.|  
|[Instrukcje: Dodawanie istniejącego modelu BDC do projektu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Pokazuje, jak zaimportować istniejący model do projektu programu SharePoint.|  
|[Instrukcje: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Opisuje sposób udostępnić ciągów, które są łączone w metadanych modelu, jeśli model jest używany przez składnik Web Part lub strony sieci Web.|  
|[Instrukcje: Dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Pokazuje, jak Dołączanie niestandardowego zestawu w funkcji.|  
  
 