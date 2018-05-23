---
title: 'Porady: Lokalizowanie znacznika ASPX | Dokumentacja firmy Microsoft'
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
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b43a8833ea84c4f6d191200bcf3af80815deb03a
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="how-to-localize-aspx-markup"></a>Porady: lokalizowanie znacznika ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony (aspx) używają zwykle ustalony ciągami. Do zlokalizowania te ciągi, należy je zastąpić przy użyciu wyrażeń, które odwołują się zlokalizowanych zasobów.  
  
## <a name="localizing-aspx-markup"></a>Lokalizowanie znacznika ASPX  
  
#### <a name="to-localize-aspx-markup"></a>Aby lokalizowanie znacznika ASPX  
  
1.  Dodaj pliki zasobów oddzielne: jeden język domyślny i jeden dla każdego zlokalizowanego języka.  
  
     Jeśli są lokalizowanie tylko znaczników i kodu nie, Dodaj element projektu globalnego pliku zasobów. Jeśli są lokalizowanie kodu i znaczników, Dodaj element projektu pliku zasobów.  
  
    1.  Aby dodać plik zasobów globalnych w **Eksploratora rozwiązań**, otwórz menu skrótów dla elementu projektu SharePoint, a następnie wybierz **Dodaj**, **nowy element**. W obszarze programu SharePoint **2010** węzła, wybierz **globalnego pliku zasobów** szablonu.  
  
    2.  Aby dodać plik zasobów w **Eksploratora rozwiązań**, otwórz menu skrótów dla elementu projektu SharePoint, a następnie wybierz **Dodaj**, **nowy element**. W obszarze albo **Visual Basic** lub **Visual C#** węzła, wybierz **pliku zasobów** szablonu.  
  
    > [!NOTE]  
    >  Pamiętaj dodać pliki zasobów do elementu projektu SharePoint, aby włączyć właściwość typu wdrożenia. Ta właściwość jest wymagana w dalszej części tej procedury. Jeśli rozwiązania nie ma elementu projektu SharePoint, można dodawać pusty projekt programu SharePoint i usuń jego domyślny plik Elements.xml.  
  
2.  Nadaj nazwę wybraną dołączany z rozszerzeniem resx, takich jak MyAppResources.resx pliku zasobów języka domyślnego. Użyj takiej samej nazwie podstawowej dla każdego pliku zlokalizowanych zasobów, ale Dodaj kultura [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Na przykład nazwę niemieckim zlokalizowany zasób MyAppResources.de DE.resx.  
  
3.  Zmień wartość **typu wdrożenia** właściwości każdego pliku zasobu do **AppGlobalResource** powodując wdrażanie w folderze App_GlobalResources serwera.  
  
4.  Jeśli używasz zasobów do zlokalizowania kodu oprócz znacznika ASPX, pozostaw wartość **Akcja kompilacji** właściwość jako **osadzonego zasobu**. Jeśli używane są pliki zasobów tylko do zlokalizowania znaczników, opcjonalnie można zmienić wartości właściwości plików do **zawartości**. Aby uzyskać więcej informacji, zobacz [lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Otwórz każdy plik zasobu i Dodaj zlokalizowanych ciągów, za pomocą tych samych parametrach identyfikatorów w każdym pliku.  
  
6.  W [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] kod znaczników dla strony ASPX i kontrolki, Zamień ciągi stałe wartości, które należy użyć następującego formatu:  
  
    ```aspx-csharp  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Na przykład do zlokalizowania tekst formantu etykiety na stronie aplikacji, można zmienić:  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     na  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Wybierz klawisz F5, aby skompilować i uruchomić aplikację.  
  
8.  W programie SharePoint zmień język wyświetlania domyślnego.  
  
     Zlokalizowanych ciągów są wyświetlane w aplikacji. Aby wyświetlić zlokalizowanych zasobów, serwer programu SharePoint musi mieć zainstalowany pakiet językowy zgodny plik zasobu kultury.  
  
## <a name="see-also"></a>Zobacz też  
 [Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Porady: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md)   
 [Porady: Dodawanie pliku zasobów](../sharepoint/how-to-add-a-resource-file.md)   
 [Instrukcje: Lokalizowanie kodu](../sharepoint/how-to-localize-code.md)  
  
  