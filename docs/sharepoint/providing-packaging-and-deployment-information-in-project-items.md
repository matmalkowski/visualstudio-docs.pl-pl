---
title: "Opakowanie i informacje o wdrożeniu w elementach projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
ms.assetid: 209ff3b9-d701-4d27-9d24-005fcc811cbe
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 84379f4847bb708bf8089ac32e261b459e87e1a1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="providing-packaging-and-deployment-information-in-project-items"></a>Zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu
  Wszystkie SharePoint — elementy projektu w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mają właściwości, które można udostępniać dodatkowe dane, gdy projekt jest wdrażany w programie SharePoint. Właściwości są następujące:  
  
-   Właściwości funkcji  
  
-   Funkcja odbiorcy  
  
-   Preferencje danych wyjściowych projektu  
  
-   Wpisy kontroli bezpieczne  
  
 Te właściwości są wyświetlane w **właściwości** okna.  
  
## <a name="feature-properties"></a>Właściwości funkcji  
 Użyj **właściwości funkcji** właściwości w celu określenia danych przy użyciu funkcji. Funkcja właściwości danych jest to zbiór wartości (przechowywane jako pary klucz/wartość), która jest zawarta w funkcji podczas wdrażania w programie SharePoint. Po wdrożeniu funkcji można uzyskać dostępu do wartości właściwości, w kodzie.  
  
 Po dodaniu funkcji wartości właściwości do elementu projektu, wartość jest dodawana jako elementu w manifeście funkcji elementu. W projekcie modelu łączności danych biznesowych (BDC) na przykład właściwość ModelFileName funkcja wygląda następująco:  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Po ustawieniu wartości właściwości funkcji jest dodawana jako FeatureProperty — element w pliku .spdata — projektu. Aby dowiedzieć się, jak uzyskiwanie dostępu do właściwości w programie SharePoint, zobacz [SPFeaturePropertyCollection klasy](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Funkcja identyczne wartości właściwości z wszystkich elementów projektu są scalane w manifeście funkcji. Jednak jeśli dwóch elementów inny projekt określić ten sam klucz właściwości funkcji z wartościami niezgodny, występuje błąd sprawdzania poprawności.  
  
 Aby dodać właściwości funkcji bezpośrednio do pliku funkcji (* .feature), wywołaj [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] metody modelu obiektu programu SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>. Jeśli używasz tej metody, należy pamiętać, że tę samą zasadę o dodanie wartości właściwości funkcji identyczne we właściwościach funkcji dotyczą również właściwości dodane bezpośrednio do pliku funkcji.  
  
## <a name="feature-receiver"></a>Odbiorca funkcji  
 Funkcja odbiorcy są kod wykonywany po wystąpieniu określonego zdarzenia na element projektu zawierającego funkcji. Na przykład można zdefiniować odbiorcy funkcji, które są wykonywane podczas instalowania, aktywowany lub uaktualnić tę funkcję. Aby dodać Odbiorca funkcji jest dodanie go bezpośrednio do funkcji, zgodnie z opisem w [wskazówki: Dodawanie przyszłych obsługiwanych odbiorników](../sharepoint/walkthrough-add-feature-event-receivers.md). Innym sposobem jest odwoływać się do nazwy klasy odbiorcy funkcji i zestawu w **Odbiorca funkcji** właściwości.  
  
### <a name="direct-method"></a>Metoda bezpośrednia  
 Po dodaniu Odbiorca funkcji do funkcji bezpośrednio, pliku kodu jest objęte **funkcji** węzła w Eksploratorze rozwiązań. Podczas tworzenia rozwiązania programu SharePoint, kod kompiluje do zestawu i wdraża do programu SharePoint. Domyślnie funkcja właściwości **zestawu odbiorcy** i **klasy odbiorcy** odwoływać się do nazwy klasy i zestawu.  
  
### <a name="reference-method"></a>Reference — metoda  
 Inny sposób, aby dodać Odbiorca funkcji polega na użyciu **Odbiorca funkcji** właściwości elementu projektu do odwołania zestawu odbiorcy funkcji. Odbiorca funkcji wartość właściwości ma dwie właściwości podrzędne: **zestawu** i **Nazwa klasy**. Zestaw musi użyć jej pełną, "silnego" i nazwę klasy musi być pełna nazwa typu. Aby uzyskać więcej informacji, zobacz [zestawy Strong-Named](http://go.microsoft.com/fwlink/?LinkID=169573). Po wdrożeniu rozwiązania do programu SharePoint, funkcja używa Odbiorca funkcji do którego istnieje odwołanie do obsługi zdarzeń funkcji.  
  
 W trakcie kompilacji rozwiązania wartości właściwości odbiorcy funkcji w funkcji i jego projekty razem scalania można ustawić atrybutów ReceiverAssembly i ReceiverClass elementu funkcji w manifeście funkcji programu SharePoint pliku rozwiązania (wsp). W związku z tym jeśli zestawu i nazwa klasy wartości właściwości elementu projektu i funkcja oba określone, wartości właściwości elementu, a funkcja projektu muszą być zgodne. Jeśli wartości nie są zgodne, zostanie wyświetlony błąd sprawdzania poprawności. Jeśli chcesz, aby element projektu odwołać się do zestawu odbiornika funkcji, innego niż ten, korzysta z jego funkcji, przenieś go do innej funkcji.  
  
 Odwołanie zestawu odbiorcy funkcji, która nie jest jeszcze na serwerze, należy również dołączyć w samym pliku zestawu w pakiecie; [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie dodaje go dla Ciebie. Podczas wdrażania funkcji plik zestawu jest kopiowany do tego systemu [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] lub folder Bin w katalogu fizycznym programu SharePoint. Aby uzyskać więcej informacji, zobacz porady: [porady: Dodawanie i usuwanie zestawów dodatkowych](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Aby uzyskać więcej informacji o funkcji odbiorcy, temacie [odbiorcy zdarzeń funkcji](http://go.microsoft.com/fwlink/?LinkID=169574) i [funkcja zdarzenia](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## <a name="project-output-references"></a>Preferencje danych wyjściowych projektu  
 Właściwość preferencje danych wyjściowych projektu określa zależność, takich jak zestawu, który tego elementu projektu musi być uruchamiane. Na przykład załóżmy, że rozwiązania jest BDC projektu i projektu klasy. Jeśli projekt BDC ma zależności w zestawie, który jest wynikiem projektu klasy, można odwoływać się do zestawu we właściwości odwołania do projektu danych wyjściowych projektu usługi łączności danych biznesowych. Po spakowaniu projektu BDC zestaw zależny jest uwzględniony w pakiecie.  
  
 Preferencje danych wyjściowych projektu są zwykle zestawów, ale w niektórych przypadkach (takich jak projekty Silverlight) może być innych typów plików.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dodawanie odwołania wyjścia projektu](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## <a name="safe-control-entries"></a>Wpisy kontroli bezpieczne  
 SharePoint zapewnia mechanizm zabezpieczeń o nazwie wpisy kontroli bezpieczne, aby ograniczyć dostęp niezaufanym użytkownikom na niektórych formantów. Zgodnie z projektem SharePoint pozwala niezaufanym użytkownikom na przekazywanie i tworzyć strony ASPX na serwerze programu SharePoint. Aby uniemożliwić dodawanie niebezpieczny kod do strony ASPX tych użytkowników, SharePoint ogranicza ich dostęp do *bezpieczne kontrolki*. Bezpieczne kontrolki ASPX formanty i składniki Web Part wyznaczony jako bezpieczne i które mogą być używane przez dowolnego użytkownika w witrynie. Aby uzyskać więcej informacji, zobacz [krok 4: Dodaj do listy bezpiecznych kontrolek składnika Web Part](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Każdy element projektu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ma właściwość o nazwie **bezpieczne wpisy kontroli** ma dwie właściwości Boolean: **bezpieczne** i **bezpieczne skryptu przed**. Bezpieczne właściwość określa, czy niezaufanym użytkownikom dostęp do formantu. Właściwość bezpieczne względem skryptu określa, czy niezaufanym użytkownikom można wyświetlać i zmieniać właściwości formantu.  
  
 Na podstawie zestawu odwołuje się wpisy kontroli bezpieczne. Dodaj wpisy kontroli bezpiecznych do projektu zestawu, wprowadzając je w elemencie projektu **bezpieczne wpisy kontroli** właściwości. Jednak również można dodać wpisów kontroli bezpiecznych do projektu zestawu za pomocą **zaawansowane** karcie **projektanta pakietów** po dodaniu dodatkowych zestawów do pakietu. Aby uzyskać więcej informacji, zobacz [porady: Oznacz kontrolek pojęciem bezpiecznych kontrolek](../sharepoint/how-to-mark-controls-as-safe-controls.md) lub [rejestrowanie w zestawie części sieci Web jako formant bezpieczny](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### <a name="xml-entries-for-safe-controls"></a>Wpisy XML dla bezpiecznych formantów  
 Po dodaniu wpisu bezpieczne kontrolki do elementu projektu lub do projektu zestawu, odwołanie jest zapisywany plik manifestu pakietu w następującym formacie:  
  
```xml  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Przy użyciu modułów podczas dołączania plików rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  