---
title: Zapisywanie danych w rozszerzeniach systemu projektu SharePoint | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3605558fd1fd9263c5dad7ec7bc295b7f095a185
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="saving-data-in-extensions-of-the-sharepoint-project-system"></a>Zapisywanie danych w rozszerzeniach systemu projektu SharePoint
  Podczas rozszerzania systemu projektu SharePoint można zapisać danych ciąg będzie nadal występować po zamknięciu projektu programu SharePoint. Dane są zwykle skojarzone z elementem określonego projektu lub z samym projekcie.  
  
 Jeśli masz dane, które nie jest konieczne będą się powtarzać, można dodać danych do każdego obiektu w modelu obiektów programu SharePoint narzędzia, która implementuje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfejsu. Aby uzyskać więcej informacji, zobacz [kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="saving-data-that-is-associated-with-a-project-item"></a>Zapisywanie danych, który jest skojarzony z elementem projektu  
 Jeśli masz dane skojarzone z określonego elementu projektu SharePoint, takiego jak wartość właściwości, które można dodać do elementu projektu można zapisać danych do pliku .spdata — dla elementu projektu. Aby to zrobić, użyj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu. Danymi dodawanymi do tej właściwości jest zapisywany w **extensiondata —** elementu w pliku .spdata — dla elementu projektu. Aby uzyskać więcej informacji, zobacz [extensiondata — Element](../sharepoint/extensiondata-element.md).  
  
 Poniższy przykład kodu pokazuje sposób użycia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości można zapisać wartości właściwości ciągu, który jest zdefiniowany w niestandardowego typu elementu projektu SharePoint. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [porady: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="saving-data-that-is-associated-with-a-project"></a>Zapisywanie danych, który jest skojarzony z projektem  
 Jeśli masz dane na poziomie projektu, takie jak wartości właściwości, które dodajesz do projektów SharePoint można zapisać danych do pliku projektu (pliku .csproj lub .vbproj pliku) lub pliku opcji użytkownika projektu (. plik csproj.user lub. vbproj.user pliku). Plik, który chcesz zapisać dane w zależy od sposobu danych do użycia:  
  
-   Jeśli dane mają być dostępne dla wszystkich deweloperów, którzy Otwórz projekt programu SharePoint, należy zapisać danych do pliku projektu. Ten plik jest zawsze ewidencjonowane bazy danych kontroli źródła, więc dane w tym pliku są dostępne dla innych deweloperów, którzy wyewidencjonować projektu.  
  
-   Jeśli dane mają być dostępne tylko dla bieżącego projektanta, który ma projekt SharePoint jest otwarty w programie Visual Studio, należy zapisać danych do pliku opcji użytkownika projektu. Ten plik nie jest zazwyczaj sprawdzana do bazy danych kontroli źródła, więc dane w tym pliku nie jest dostępne dla innych deweloperów, którzy wyewidencjonować projektu.  
  
### <a name="saving-data-to-the-project-file"></a>Zapisywanie danych w pliku projektu  
 Można zapisać danych w pliku projektu, należy przekonwertować <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> do obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> obiekt, a następnie użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metody. Poniższy przykład kodu pokazuje, jak użyć tej metody można zapisać wartości właściwości projektu w pliku projektu. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [porady: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Aby uzyskać więcej informacji na temat konwertowania <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektów do innych typów w modelu obiektu automatyzacji programu Visual Studio lub model obiektów integracji, zobacz [konwertowanie między SharePoint typami systemu projektu i inne typy projektów Visual Studio ](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="saving-data-to-the-project-user-option-file"></a>Zapisywanie danych w pliku opcji użytkownika projektu  
 Aby zapisać danych do pliku projektu użytkownika opcji, należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektu. Poniższy przykład kodu pokazuje, jak użyć tej właściwości można zapisać wartości właściwości projektu w pliku opcji użytkownika projektu. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [porady: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  