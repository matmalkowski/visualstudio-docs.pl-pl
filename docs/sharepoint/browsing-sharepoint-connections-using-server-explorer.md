---
title: Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ca6e7ff8d046ae94d6016c01b346bce592b2fcf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="browsing-sharepoint-connections-using-server-explorer"></a>Przeglądanie połączeń SharePoint za pomocą eksploratora serwera
  Możesz teraz przeglądać lokalnych połączeń SharePoint w **Eksploratora serwera**. Przy użyciu tej metody, można przejść za pośrednictwem składników witryny programu SharePoint w systemie. Składniki witryny programu SharePoint, takie jak definicje list i typów zawartości, są wyświetlane w węźle, o nazwie **połączeń SharePoint** w widoku drzewa **Eksploratora serwera**. Aby wyświetlić **Eksploratora serwera**, na pasku menu wybierz **widoku**, **Eksploratora serwera**. Oprócz wyświetlania składników witryny programu SharePoint, można usunąć elementy, przeglądania właściwości lub Odśwież widok drzewa za pomocą poleceń menu skrótów.  
  
> [!IMPORTANT]  
>  Aby przeglądać witryny programu SharePoint, musisz być administratorem zbioru witryn programu SharePoint, a działanie programu Visual Studio z uprawnieniami administratora komputera lokalnego. W przeciwnym razie jest wyświetlana w **Eksploratora serwera**, ale nie można rozwinąć jego węzła. Aby sprawdzić, czy jesteś administratorem zbioru witryn, otwórz witrynę w przeglądarce sieci web, otwórz **Akcje witryny** menu, wybierz **uprawnienia witryny**, a następnie na **uprawnienia: Team Witryna** wybierz pozycję **Administratorzy** polecenie **Zarządzaj** na Wstążce. Twoja nazwa będzie widoczna w polu tekstowym, jeśli jesteś administratorem zbioru witryn. Jeśli **Administratorzy** polecenia nie pojawia się w grupie zarządzania, na Wstążce, użytkownik nie jest administratorem zbioru witryn i odpowiednie uprawnienia, które należy uzyskać od administratora witryny.  
  
## <a name="server-explorer-nodes"></a>Węzły w Eksploratorze serwera  
 Każdy składnik witryny programu SharePoint jest reprezentowany przez węzeł w **Eksploratora serwera** widok w obszarze drzewa **połączeń SharePoint**. Domyślne witryny programu SharePoint zawierają na przykład typ zawartości o nazwie Dyskusja, który reprezentuje typ dyskusji, którym jest wyświetlany w **dyskusji** strony w witrynie programu SharePoint. Typ zawartości dyskusji zawiera kilka pól. Aby wyświetlić te pola **Eksploratora serwera**, rozwiń węzeł **typów zawartości** węzeł, a następnie **dyskusji** węzła. W obszarze czy kilka węzłów pola, takie jak treści, temat dyskusji i tytuł.  
  
## <a name="node-shortcut-menu-commands"></a>Polecenia Menu skrótów węzła  
 Każdy węzeł ma menu skrótów, do którego dostęp przez kliknięcie prawym przyciskiem myszy węzeł lub wybierając go, a następnie wybierając klawiszy Shift + F10. Węzeł poleceń mogą obejmować:  
  
|Nazwa polecenia|Opis|  
|------------------|-----------------|  
|Odśwież|Aktualizuje widok drzewa, aby odzwierciedlić zmiany, które mogły wystąpić od czasu ostatniego wyświetlania węzła.|  
|Usuwanie|Usuwa wybrany węzeł w widoku drzewa. **Uwaga:** to polecenie jest włączone tylko na liście połączeń SharePoint **połączeń SharePoint** węzła.|  
|Właściwości|Wyświetla dostępne właściwości dla wybranego węzła w **właściwości** okna. Właściwości są wszystkie tylko do odczytu i nie każdy węzeł ma właściwości skojarzone z nim.|  
|Dodaj połączenie|Umożliwia określenie witryny programu SharePoint, które chcesz przeglądać. Dostępne na **połączeń SharePoint** węzła i węzłów podrzędnych lokacji.|  
|Wyświetl w przeglądarce|Wyświetla wybraną listę w przeglądarce sieci Web. To polecenie jest dostępna w niektórych list w obszarze **wymieniono** węzła, który jest zawarty w **list i bibliotek**.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Dodawanie lub usuwanie połączeń SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Opisuje czynności, które są wymagane do dodawania nowej witryny programu SharePoint do **połączeń SharePoint** w węźle **Eksploratora serwera**.|  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  