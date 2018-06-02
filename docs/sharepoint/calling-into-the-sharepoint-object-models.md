---
title: Wywoływanie modeli obiektów SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 795fd4a146aaedbfb4035cfc028bd37e0b0282fd
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691716"
---
# <a name="calling-into-the-sharepoint-object-models"></a>Wywoływanie modeli obiektów SharePoint
  Po utworzeniu rozszerzeń dla narzędzi SharePoint w Visual Studio może być konieczne wywoływania interfejsów API programu SharePoint do wykonywania określonych zadań. Na przykład w przypadku utworzenia niestandardowego kroku wdrożenia dla projektów programu SharePoint, trzeba będzie wywoływać interfejsy API programu SharePoint do wykonania niektórych zadań w celu wdrożenia rozwiązania.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zapewniają dwa modele inny obiekt, których można używać w rozszerzeń narzędzi SharePoint: modelu obiektów serwera i modelu obiektów klienta. Każdy model obiektów ma zalety i wady w kontekście rozszerzeń narzędzi SharePoint.  
  
 Omówienie modeli obiektów SharePoint, zobacz [omówienie programowania modelu z rozszerzeniami narzędzi SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="using-the-client-object-model-in-extension-projects"></a>Przy użyciu client object model w projektach rozszerzenia
 Podczas opracowywania rozszerzeń dla narzędzi SharePoint można użyć modelu obiektów klienta w projekcie podobnie jak dowolnego innego zestawu zarządzanych interfejsów API. Można dodać odwołania do zestawów w modelu obiektów klienta do projektu i mogą wywoływać interfejsy API w modelu obiektów klienta bezpośrednio w kodzie.  
  
 Jednak client object model ma dwie wady w kontekście rozszerzeń narzędzi SharePoint:  
  
-   Model obiektu klienta zawiera tylko podzestawu modelu obiektów serwera. Należy korzystać z funkcji programu SharePoint, która nie jest widoczna w modelu obiektów klienta, należy użyć modelu obiektów serwera.  
  
-   Mimo że w rozszerzeń narzędzi SharePoint przy użyciu client object model powinny działać w większości przypadków, mogą wystąpić sytuacje, w którym wywołań client object model nie działają zgodnie z oczekiwaniami. Client object model jest przeznaczony do użycia w aplikacjach klienckich do wywołania do witryny programu SharePoint na serwerze zdalnym lub farmy. Narzędzia programu SharePoint w Visual Studio działa tylko z lokalną instalacją programu SharePoint na komputerze dewelopera. W związku z tym gdy używasz client object model w rozszerzeniu narzędzia programu SharePoint, należy wywołać w witrynie programu SharePoint na komputerze lokalnym, który jest nie jak client object model został zaprojektowany do użycia.  
  
 Aby uzyskać wskazówki, które pokazuje, jak użyć modelu obiektów klienta w rozszerzeniu narzędzi SharePoint w Visual Studio, zobacz [wskazówki: wywoływanie Model obiektu klienta programu SharePoint w rozszerzeniu Eksploratora serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="using-the-server-object-model-in-extension-projects"></a>Za pomocą modelu obiektów serwera w projektach rozszerzenia
 W modelu obiektów serwera jest nadzbiorem client object model. Korzystając z modelu obiektów serwera, można użyć wszystkich funkcji który [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ujawnia programowo.  

 Rozszerzeń narzędzi SharePoint można używać interfejsów API w modelu obiektów serwera, ale ich nie można bezpośrednio wywołać interfejsów API. W modelu obiektów serwera można wywołać tylko z procesu 64-bitowego którego element docelowy .NET Framework 3.5. Jednak wymaga rozszerzeń narzędzi SharePoint [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i są uruchamiane w procesie 32-bitowego programu Visual Studio. Zapobiega to bezpośrednio odwołania do zestawów w modelu obiektów programu SharePoint server rozszerzeń narzędzi SharePoint.  
  
 Jeśli chcesz użyć modelu obiektów serwera w rozszerzeniu narzędzia programu SharePoint, należy utworzyć niestandardowego *polecenia SharePoint* do wywołania interfejsu API. Polecenie programu SharePoint należy zdefiniować w dodatkowej zestawu, który można wywołać bezpośrednio do modelu obiektów serwera. W projekcie rozszerzenia, należy wywołać polecenie programu SharePoint pośrednio za pomocą metody parametr ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> obiektu.  
  
 Aby uzyskać więcej informacji na temat tworzenia i używania poleceń programu SharePoint, zobacz [porady: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) i [porady: wykonywanie polecenia SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Aby uzyskać informacje o sposobie wdrażania SharePoint — polecenia, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Aby uzyskać wskazówki, które przedstawiają sposób tworzenia i używania poleceń programu SharePoint, zobacz [wskazówki: Tworzenie niestandardowego kroku wdrożenia dla projektów SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) i [wskazówki: rozszerzanie Eksploratora serwera do wyświetlania w sieci Web Części](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### <a name="understand-how-sharepoint-commands-are-executed"></a>Zrozumienie, jak są wykonywane polecenia SharePoint
 Zestawy, które definiują polecenia SharePoint są ładowane w ramach procesu 64-bitowego hosta o nazwie vssphost4.exe. Po wywołaniu polecenia SharePoint w rozszerzeniu narzędzia programu SharePoint, polecenie zostanie wykonane przez vssphost4.exe zamiast procesu 32-bitowego programu Visual Studio (devenv.exe). Można kontrolować niektóre aspekty jak polecenia SharePoint są wykonywane przez ustawienie wartości w rejestrze. Aby uzyskać więcej informacji, zobacz [Debugowanie rozszerzeń dla narzędzi SharePoint w Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Porady: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Porady: wykonywanie polecenia SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Omówienie modelu programowania rozszerzeń narzędzi SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
