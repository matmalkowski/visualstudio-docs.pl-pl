---
title: 'Porady: Tworzenie polecenia SharePoint | Dokumentacja firmy Microsoft'
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
helpviewer_keywords: SharePoint commands [SharePoint development in Visual Studio], creating
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 42aa28637bc513865f96c0b88d2ca7c4dd726c5c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-sharepoint-command"></a>Porady: tworzenie polecenia SharePoint
  Jeśli chcesz użyć modelu obiektów serwera w rozszerzeniu narzędzia programu SharePoint, należy utworzyć niestandardowego *polecenia SharePoint* do wywołania interfejsu API. Polecenie programu SharePoint do definiowania zestawu, który można wywołać bezpośrednio do modelu obiektów serwera.  
  
 Aby uzyskać więcej informacji dotyczących przeznaczenia polecenia SharePoint, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-create-a-sharepoint-command"></a>Aby utworzyć polecenie programu SharePoint  
  
1.  Tworzenie projektu biblioteki klas, które ma następującą konfigurację:  
  
    -   Dotyczy programu .NET Framework 3.5. Aby uzyskać więcej informacji o wybieraniu platformę docelową, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
    -   Celem AnyCPU lub x64 platformy. Domyślnie platforma docelowa dla projektów biblioteki klas to AnyCPU. Aby uzyskać więcej informacji o wybieraniu platformy docelowej, zobacz [porady: Konfigurowanie projektów do platform docelowych](../ide/how-to-configure-projects-to-target-platforms.md).  
  
    > [!NOTE]  
    >  Polecenie programu SharePoint nie może implementować w tym samym projekcie, który definiuje to rozszerzenie narzędzia programu SharePoint, ponieważ polecenia SharePoint celem docelowy rozszerzeń narzędzi .NET Framework 3.5 i SharePoint [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Należy zdefiniować żadnych poleceń programu SharePoint, które są używane przez rozszerzenia w oddzielny projekt. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  W klasie w projekcie Tworzenie metody, która definiuje polecenie programu SharePoint. Metoda musi być zgodna z następującymi zasadami:  
  
    -   Może mieć jeden lub dwa parametry.  
  
         Pierwszy parametr musi być <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> obiektu. Ten obiekt zawiera Microsoft.SharePoint.SPSite lub Microsoft.SharePoint.SPWeb, w którym wykonywane jest polecenie. Zapewnia także <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> obiektu, który może służyć do zapisywania wiadomości **dane wyjściowe** okna lub **listy błędów** okna w programie Visual Studio.  
  
         Drugi parametr może być typem wybranych przez użytkownika, ale ten parametr jest opcjonalny. Jeśli potrzebujesz do przekazywania danych z rozszerzenia narzędzia programu SharePoint do polecenia, można dodać tego parametru polecenia programu SharePoint.  
  
    -   Może mieć wartości zwracanej, ale ten krok jest opcjonalny.  
  
    -   Druga wartość parametru i przywracać musi być typu, który może być serializowany przez Windows Communication Foundation (WCF). Aby uzyskać więcej informacji, zobacz [typy obsługiwane przez serializator kontraktu danych](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) i [przy użyciu klasy XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).  
  
    -   Metoda może mieć żadnych widoczności (**publicznego**, **wewnętrzny**, lub **prywatnej**), i może być statyczne lub statyczna.  
  
4.  Zastosuj <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> do metody. Ten atrybut określa unikatowy identyfikator dla polecenia; Ten identyfikator nie ma być zgodna z nazwą metody.  
  
     Należy określić ten sam Unikatowy identyfikator podczas wywoływania polecenia z rozszerzenia narzędzia programu SharePoint. Aby uzyskać więcej informacji, zobacz [porady: wykonywanie polecenia SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje polecenie programu SharePoint, która ma identyfikator `Contoso.Commands.UpgradeSolution`. To polecenie używa interfejsów API w modelu obiektów serwera do uaktualnienia do wdrożonej rozwiązania.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 Oprócz pierwszego niejawne <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametru, to polecenie ma także parametr niestandardowy ciąg, który zawiera pełną ścieżkę pliku wsp, który jest uaktualniany do witryny programu SharePoint. Aby wyświetlić ten kod w kontekście większego przykładu, zobacz [wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## <a name="deploying-the-command"></a>Wdrażanie polecenia  
 Aby wdrożyć polecenia, należy uwzględnić zestaw polecenia w tej samej [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) z zestawu rozszerzenia, która używa polecenia. Należy również dodać wpis dla zestawu poleceń w pliku extension.vsixmanifest. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Porady: wykonywanie polecenia SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  