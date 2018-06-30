---
title: 'Porady: dostosowywanie funkcji SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9be9ba70bb94e743a788db11b55c188275bcad64
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120300"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Porady: dostosowywanie funkcji SharePoint
  Można tworzyć i dostosowywać funkcji programu SharePoint przy użyciu narzędzia Projektant funkcji w programie Visual Studio. Na przykład można ustawić zakresu funkcji i dodać inne funkcje jako zależności. Domyślnie projektancie funkcji jest otwarty podczas dodawania nowych funkcji w Eksploratorze rozwiązań lub w Eksploratorze pakietu programu SharePoint.  
  
## <a name="opening-the-feature-designer"></a>Otworzyć projektanta funkcji  
 Można dodawać i usuwać SharePoint — elementy projektu do funkcji przy użyciu narzędzia Projektant funkcji.  
  
#### <a name="to-open-the-feature-designer"></a>Aby otworzyć projektanta funkcji
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **funkcji**.  
  
2.  Kliknij dwukrotnie *Feature1* elementu, lub Otwórz menu skrótów *Feature1* elementu, a następnie wybierz pozycję **Widok projektanta**.  
  
## <a name="view-the-packaged-manifest-file"></a>Widok spakowanych pliku manifestu  
 Projektant funkcji można użyć do modyfikacji i generowanie pliku manifestu spakowanych funkcji (*feature.xml*). Następnie można wyświetlić kod XML dla tego pliku w programie Visual Studio.  
  
#### <a name="to-view-the-packaged-manifest-file"></a>Aby wyświetlić spakowanych pliku manifestu  
  
1.  W **projektanta funkcji**, wybierz **manifestu** kartę.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Aby wyświetlić spakowanych pliku manifestu za pomocą Eksploratora rozwiązań  
  
1.  W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** ikony.  
  
2.  Rozwiń węzeł funkcje rozwiń FeatureName, rozwiń FeatureName.feature, a następnie otwórz  *\<Nazwa_funkcji >. Template.XML* pliku.  
  
    > [!NOTE]  
    >  Po otwarciu szablonu pliku manifestu funkcji XML, pliki zostaną automatycznie sprawdzone i można zignorować ostrzeżenia, które są wyświetlane w oknie Lista błędów.  
  
## <a name="change-the-manifest-template"></a>Zmień manifestu szablonu  
 Kod XML w edytorze XML programu Visual Studio lub w okienku manifestu szablonu pliku manifestu funkcji, można zmienić. Wszelkie zmiany w kodzie XML jest scalany spakowanych pliku manifestu dla funkcji. Na przykład można zmienić manifestu szablonu, aby dostosować właściwości funkcji.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Aby zmienić manifestu szablonu za pomocą edytora XML  
  
1.  W **projektanta funkcji**, wybierz **manifestu** karcie, rozwiń **edytować opcje** węzła, a następnie wybierz **otwarty w edytorze XML** łącza.  
  
     Zmiany w pliku XML są scalane w spakowanych pliku manifestu.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Aby zmienić manifestu szablonu przy użyciu okienka manifestu szablonu  
  
1.  W **projektanta funkcji**, wybierz **manifestu** karcie, rozwiń **edytować opcje** węzeł, a następnie zmień plik XML, który zostanie wyświetlony w okienku manifestu szablonu.  
  
     Zmiany w pliku XML są wyświetlane w **podglądu z spakowane manifestu** okienka.  
  
## <a name="overwrite-the-packaged-manifest-file"></a>Zastąp spakowanych pliku manifestu  
 Można wyłączyć funkcji projektanta i utworzyć *feature.xml* plik ręcznie. Aby wykonać tę procedurę, po raz pierwszy bieżące ustawienia w Projektancie funkcji są zapisywane do pliku XML szablonu funkcji. Następnie można zmodyfikować lub zastąpić kod XML.  
  
> [!NOTE]  
>  Jeśli możesz dodać lub usunąć SharePoint — elementy projektu w pliku XML, gdy funkcja Projektant jest wyłączony, nie są dostarczane te elementy projektu.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Aby zastąpić spakowanych plik manifestu wyłączając projektanta  
  
1.  W **projektanta funkcji**, wybierz **manifestu** kartę.  
  
2.  Rozwiń węzeł **edytować opcje** węzła, wybierz **Zastąp wygenerowanego kodu XML i edytowania manifestu w edytorze XML** łącza, a następnie wybierz pozycję **tak** przycisku.  
  
     Szablon został zaktualizowany o spakowanych bieżącego pliku manifestu.  
  
## <a name="enable-the-feature-designer"></a>Włącz projektanta funkcji  
 Można ponownie włączyć projektanta funkcji, aby dostosować *feature.xml* pliku.  
  
#### <a name="to-re-enable-the-designer"></a>Aby ponownie włączyć projektanta  
  
1.  W **projektanta funkcji**, wybierz **odrzucenia manifestu zmiany i ponownie włącz projektanta** łącza, a następnie wybierz pozycję **tak** przycisku.  
  
2.  Szablon jest odświeżany z oryginalny tekst, a zmiany wprowadzone w pliku XML zostaną utracone.  
  
## <a name="see-also"></a>Zobacz także
 [Pakiet i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
