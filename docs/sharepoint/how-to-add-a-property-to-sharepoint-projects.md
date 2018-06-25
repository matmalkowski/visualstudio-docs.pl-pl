---
title: 'Porady: Dodawanie właściwości do projektów SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 015725197c2c269a7b6aed2e20f0159e2a9f2fe6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758562"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Porady: Dodawanie właściwości do projektów SharePoint
  Rozszerzenia projektu umożliwia dodawanie właściwości do żadnego projektu programu SharePoint. Pojawi się ona w **właściwości** okna, gdy projekt jest wybrany w **Eksploratora rozwiązań**.  
  
 W następujących krokach założono, że utworzono już rozszerzenia projektu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Aby dodać właściwość do projektu SharePoint  
  
1.  Definiowanie klasy, z właściwością publiczny odpowiadający właściwości, które dodajesz do projektów SharePoint. Jeśli chcesz dodać wiele właściwości, można zdefiniować wszystkie właściwości w tej samej lub różnych klas.  
  
2.  W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementacji, dojście <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> zdarzenie *projectService* parametru.  
  
3.  W obsłudze zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> zdarzeń, dodać wystąpienia klasy właściwości, aby <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> kolekcji parametr argumentów zdarzenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób dodawania dwóch właściwości do projektów SharePoint. Dane w pliku projektu użytkownika opcji będzie się powtarzać jedną właściwość ( *. csproj.user* pliku lub *. vbproj.user* pliku). Inne właściwości będzie się powtarzać, jego dane w pliku projektu (*.csproj* pliku lub *vbproj* pliku).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understand-the-code"></a>Kodu  
 Aby upewnić się, że to samo wystąpienie elementu `CustomProjectProperties` klasa jest używana zawsze <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> zdarzenie, przykładowy kod dodaje właściwości obiektu do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości czasu pierwszy projekt, to zdarzenie występuje. Kod pobiera tego obiektu, gdy to zdarzenie wystąpi ponownie. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość do skojarzenia danych z projektów, zobacz [rozszerzeń narzędzi kojarzenie danych niestandardowych z programem SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Aby zachować zmiany wartości właściwości **ustawić** metod dostępu właściwości przy użyciu następujących interfejsów API:  
  
-   `CustomUserFileProperty` używa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> właściwości można zapisać wartości w pliku opcji użytkownika projektu.  
  
-   `CustomProjectFileProperty` używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodę, aby zapisać jego wartości w pliku projektu.  
  
 Aby uzyskać więcej informacji na temat trwałych danych w tych plikach, zobacz [zapisywać danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Określ zachowanie właściwości niestandardowe  
 Można określić, jak właściwości niestandardowej pojawia się i zachowuje się tak **właściwości** okna przez zastosowanie atrybutów z <xref:System.ComponentModel> przestrzeni nazw do definicji property. Następujące atrybuty są przydatne w wielu scenariuszach:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Określa nazwę właściwości, która jest wyświetlana w **właściwości** okna.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Określa ciąg opisu, który pojawia się w dolnej części **właściwości** okna, jeśli właściwość jest zaznaczone.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Określa wartość domyślną właściwości.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Określa niestandardowy konwersji między ciąg, który jest wyświetlany w **właściwości** okno i wartość właściwości innych niż ciąg.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Określa niestandardowego edytora do zmodyfikowania właściwości.  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint
-    
-   Microsoft.VisualStudio.Shell
-     
-   Microsoft.VisualStudio.Shell.Interop
-     
-   Microsoft.VisualStudio.Shell.Interop.8.0
-     
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) dla zestawu i inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie projektów SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Porady: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Porady: Dodawanie pozycji menu skrótów do projektów SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
