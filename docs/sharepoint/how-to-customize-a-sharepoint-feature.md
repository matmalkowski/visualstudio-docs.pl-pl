---
title: 'Porady: dostosowywanie funkcji SharePoint | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: adb4283a56715da704df8991543ea89c6cbc79a4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Porady: dostosowywanie funkcji SharePoint
  Można tworzyć i dostosowywać funkcji programu SharePoint przy użyciu narzędzia Projektant funkcji w programie Visual Studio. Na przykład można ustawić zakresu funkcji i dodać inne funkcje jako zależności. Domyślnie projektancie funkcji jest otwarty podczas dodawania nowych funkcji w Eksploratorze rozwiązań lub w Eksploratorze pakietu programu SharePoint.  
  
## <a name="opening-the-feature-designer"></a>Otworzyć projektanta funkcji  
 Można dodawać i usuwać SharePoint — elementy projektu do funkcji przy użyciu narzędzia Projektant funkcji.  
  
#### <a name="to-open-the-feature-designer"></a>Aby otworzyć projektanta funkcji  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **funkcji**.  
  
2.  Kliknij dwukrotnie *Feature1* elementu, lub Otwórz menu skrótów *Feature1* elementu, a następnie wybierz pozycję **Widok projektanta**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Wyświetlanie spakowanych pliku manifestu  
 Projektant funkcja służy do modyfikowania i generowanie pliku manifestu spakowanych funkcji (feature.xml). Następnie można wyświetlić kod XML dla tego pliku w programie Visual Studio.  
  
#### <a name="to-view-the-packaged-manifest-file"></a>Aby wyświetlić spakowanych pliku manifestu  
  
1.  W **projektanta funkcji**, wybierz **manifestu** kartę.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Aby wyświetlić spakowanych pliku manifestu za pomocą Eksploratora rozwiązań  
  
1.  W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** ikony.  
  
2.  Rozwiń węzeł funkcje rozwiń FeatureName, rozwiń FeatureName.feature, a następnie otwórz *FeatureName*. Plik template.XML.  
  
    > [!NOTE]  
    >  Po otwarciu szablonu pliku manifestu funkcji XML, pliki zostaną automatycznie sprawdzone i można zignorować ostrzeżenia, które są wyświetlane w oknie Lista błędów.  
  
## <a name="changing-the-manifest-template"></a>Zmiana manifestu szablonu  
 Kod XML w edytorze XML programu Visual Studio lub w okienku manifestu szablonu pliku manifestu funkcji, można zmienić. Wszelkie zmiany w kodzie XML jest scalany spakowanych pliku manifestu dla funkcji. Na przykład można zmienić manifestu szablonu, aby dostosować właściwości funkcji.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Aby zmienić manifestu szablonu za pomocą edytora XML  
  
1.  W **projektanta funkcji**, wybierz **manifestu** karcie, rozwiń **edytować opcje** węzła, a następnie wybierz **otwarty w edytorze XML** łącza.  
  
     Zmiany w pliku XML są scalane w spakowanych pliku manifestu.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Aby zmienić manifestu szablonu przy użyciu okienka manifestu szablonu  
  
1.  W **projektanta funkcji**, wybierz **manifestu** karcie, rozwiń **edytować opcje** węzeł, a następnie zmień plik XML, który zostanie wyświetlony w okienku manifestu szablonu.  
  
     Zmiany w pliku XML są wyświetlane w **podglądu z spakowane manifestu** okienka.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Zastępowanie spakowanych pliku manifestu  
 Można wyłączyć funkcji projektanta i ręcznie utworzyć plik feature.xml. Aby wykonać tę procedurę, po raz pierwszy bieżące ustawienia w Projektancie funkcji są zapisywane do pliku XML szablonu funkcji. Następnie można zmodyfikować lub zastąpić kod XML.  
  
> [!NOTE]  
>  Jeśli możesz dodać lub usunąć SharePoint — elementy projektu w pliku XML, gdy funkcja Projektant jest wyłączony, nie są dostarczane te elementy projektu.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Aby zastąpić spakowanych plik manifestu wyłączając projektanta  
  
1.  W **projektanta funkcji**, wybierz **manifestu** kartę.  
  
2.  Rozwiń węzeł **edytować opcje** węzła, wybierz **Zastąp wygenerowanego kodu XML i edytowania manifestu w edytorze XML** łącza, a następnie wybierz pozycję **tak** przycisku.  
  
     Szablon został zaktualizowany o spakowanych bieżącego pliku manifestu.  
  
## <a name="enabling-the-feature-designer"></a>Włączanie funkcji projektanta  
 Można ponownie włączyć projektanta funkcji, aby dostosować plik feature.xml.  
  
#### <a name="to-re-enable-the-designer"></a>Aby ponownie włączyć projektanta  
  
1.  W **projektanta funkcji**, wybierz **odrzucenia manifestu zmiany i ponownie włącz projektanta** łącza, a następnie wybierz pozycję **tak** przycisku.  
  
2.  Szablon jest odświeżany z oryginalny tekst, a zmiany wprowadzone w pliku XML zostaną utracone.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania pakowania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  