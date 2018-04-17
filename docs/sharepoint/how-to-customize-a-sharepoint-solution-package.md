---
title: 'Porady: Dostosowywanie pakietu rozwiązania SharePoint | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9ffe532653abf58e4af6297e69c1049a916144cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Porady: dostosowywanie pakietu rozwiązania SharePoint
  Projektanta pakietów służy do tworzenia i dostosowywania pakietów (wsp). Na przykład można dodać projektu SharePoint — elementy i funkcje, określić, czy serwer sieci Web jest zresetować po wdrożeniu rozwiązania i ustawić typ serwera wdrażania.  
  
## <a name="opening-the-package-designer"></a>Otwieranie projektanta pakietów  
  
#### <a name="to-open-the-package-designer"></a>Aby otworzyć projektanta pakietów  
  
-   W **Eksploratora rozwiązań**, kliknij dwukrotnie **pakietu**, lub wybierz **Widok projektanta** menu skrótów dla **pakietu**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Wyświetlanie spakowanych pliku manifestu  
 Projektanta pakietów służy do modyfikowania i generowanie spakowanych pliku manifestu. Następnie można wyświetlić kod XML dla tego pliku w programie Visual Studio.  
  
#### <a name="to-view-the-xml-source-file"></a>Aby wyświetlić plik XML źródła  
  
1.  W **projektanta pakietów**, wybierz **manifestu**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Aby wyświetlić spakowanych pliku manifestu za pomocą Eksploratora rozwiązań  
  
1.  W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki**.  
  
2.  Rozwiń węzeł pakietu, rozwiń Package.package, a następnie otwórz plik Package.Template.xml.  
  
    > [!NOTE]  
    >  Podczas otwierania pliku manifestu XML dla szablonu pakietu pliki są automatycznie zweryfikowane i możesz zignorować ostrzeżenia, które są wyświetlane w oknie Lista błędów.  
  
## <a name="changing-the-manifest-template"></a>Zmiana manifestu szablonu  
 Można zmienić kod XML spakowanych pliku manifestu w edytorze XML programu Visual Studio lub w okienku manifestu szablonu. Wszelkie zmiany w kodzie XML są scalane w spakowanych pliku manifestu pakietu.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Aby zmienić manifestu szablonu za pomocą edytora XML  
  
1.  W **projektanta pakietów**, wybierz **manifestu** karcie, rozwiń węzeł **edytować opcje** węzła, a następnie wybierz pozycję **otwarty w edytorze XML** łącza.  
  
     Zmiany w pliku XML są scalane w spakowanych pliku manifestu.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Aby zmienić manifestu szablonu przy użyciu okienka manifestu szablonu  
  
1.  W **projektanta pakietów**, wybierz **manifestu** karcie, rozwiń **edytować opcje** węzeł, a następnie zmień plik XML, który zostanie wyświetlony w okienku manifestu szablonu.  
  
     Zmiany w pliku XML są wyświetlane w **podglądu z spakowane manifestu** okienka.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Zastępowanie spakowanych pliku manifestu  
 Można wyłączyć projektanta pakietów i utworzenia pliku manifest.xml ręcznie. Aby wykonać tę procedurę, po raz pierwszy bieżące ustawienia w Projektancie pakietu są zapisywane do pliku XML pakietu szablonu. Następnie można zmodyfikować lub zastąpić kod XML.  
  
> [!NOTE]  
>  Jeśli dodawanie lub usuwanie SharePoint — elementy projektu i funkcji w pliku XML podczas projektanta pakietów jest wyłączone, te elementy projektu i funkcje nie są umieszczone.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Aby zastąpić spakowanych plik manifestu wyłączając projektanta  
  
1.  W **projektanta pakietów**, wybierz **manifestu** kartę.  
  
2.  .  
  
3.  Rozwiń węzeł **edytować opcje** węzła, wybierz **Zastąp wygenerowanego kodu XML i edytowania manifestu w edytorze XML** łącza, a następnie wybierz pozycję **tak** przycisku.  
  
     Szablon został zaktualizowany o spakowanych bieżącego pliku manifestu.  
  
## <a name="enabling-the-package-designer"></a>Włączanie projektanta pakietów  
 Można ponownie włączyć projektanta pakietów do pliku manifest.xml dostosowywania.  
  
#### <a name="to-re-enable-the-designer"></a>Aby ponownie włączyć projektanta  
  
1.  W **projektanta pakietów**, wybierz **odrzucenia manifestu zmiany i ponownie włącz projektanta** łącza, a następnie wybierz pozycję **tak** przycisku.  
  
     Szablon jest odświeżany z oryginalny tekst, a zmiany wprowadzone w pliku XML zostaną utracone.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania pakowania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  