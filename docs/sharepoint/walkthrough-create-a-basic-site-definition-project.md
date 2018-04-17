---
title: 'Wskazówki: Tworzenie podstawowego projektu definicji witryny | Dokumentacja firmy Microsoft'
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d54b3ea7c32230a683359ee466b03e8954fec2ab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Wskazówki: Tworzenie podstawowego projektu definicji witryny
  W tym przewodniku przedstawiono sposób tworzenia definicji lokacji podstawowej, która zawiera visual części sieci Web z niektórych formantów. Dla jasności wizualnego składnika Web part tworzenia zawiera tylko kilka formantów. Można jednak utworzyć bardziej złożone definicje witryn programu SharePoint, które zawierają więcej funkcji.  
  
 W tym przewodniku przedstawiono następujące zadania:  
  
-   Tworzenie definicji witryny przy użyciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] szablonu projektu.  
  
-   Tworzenie witryny programu SharePoint przy użyciu definicji lokacji w programie SharePoint.  
  
-   Dodawanie wizualnego składnika Web part do rozwiązania.  
  
-   Dostosowywanie strony default.aspx witryny, dodając do niego nowy składnik Web part programu visual.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint. Aby uzyskać więcej informacji zobacz wymagania dotyczące opracowywania rozwiązań programu SharePoint.  
  
-   Program Visual Studio.  
  
## <a name="creating-a-site-definition-solution"></a>Tworzenie rozwiązania definicji witryny  
 Najpierw utwórz projektu definicji witryny w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Aby utworzyć projekt definicji witryny  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**. Jeśli środowiskiem IDE ustawiono użyć ustawienia środowiska deweloperskiego Visual Basic, na pasku menu, wybierz **pliku**, **nowy projekt**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  Rozwiń węzeł **Visual C#** węzła lub **Visual Basic** węzła, rozwiń węzeł **SharePoint** węzła, a następnie wybierz pozycję **2010** węzła.  
  
3.  W **szablony** wybierz **projektu programu SharePoint 2010** szablonu.  
  
4.  W **nazwa** wprowadź **TestSiteDef**, a następnie wybierz pozycję **OK** przycisku.  
  
     **Kreator dostosowania programu SharePoint** pojawi się.  
  
5.  Na **określić poziom lokacji i zabezpieczeń dla debugowania** strony, wprowadź adres URL witryny programu SharePoint, na którym chcesz debugować definicji witryny lub użyj domyślnej lokalizacji (http://*Nazwa systemowa*/).  
  
6.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji.  
  
     Wszystkie projekty definicji witryny musi być wdrożony jako rozwiązania farmy. Aby uzyskać więcej informacji na temat rozwiązania piaskownicy w porównaniu z rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wybierz **Zakończ** przycisku.  
  
     Projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
8.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
9. Pod **Visual C#** lub **Visual Basic**, rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** węzła.  
  
10. W **szablony** okienku wybierz **definicji witryny** szablonu i pozostaw **nazwa** jako **SiteDefinition1**, a następnie wybierz pozycję  **Dodaj** przycisku.  
  
## <a name="create-a-visual-web-part"></a>Utwórz wizualny składnik Web Part  
 Następnie należy utworzyć visual składnik Web part na stronie głównej definicji witryny są wyświetlane.  
  
#### <a name="to-create-a-visual-web-part"></a>Aby utworzyć wizualny składnik Web part  
  
1.  W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** przycisku.  
  
2.  Wybierz **SiteDefinition1** węzła projektu, a następnie na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
3.  Rozwiń węzeł **Visual C#** węzła lub **Visual Basic** węzła, rozwiń węzeł **SharePoint** węzła, a następnie wybierz pozycję **2010** węzła.  
  
4.  Na liście szablonów wybierz **wizualnego składnika Web Part** szablonu, zachowaj domyślne nazwy VisualWebPart1, a następnie wybierz **Dodaj** przycisku.  
  
     Otwiera plik VisualWebPart1.ascx.  
  
5.  W dolnej części VisualWebPart1.ascx, Dodaj następujący kod do dodawania trzech formantów do formularza: pole tekstowe, przycisk i etykiety:  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  W obszarze VisualWebPart1.ascx, otwórz plik VisualWebPart1.ascx.cs (dla [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) lub VisualWebPart1.ascx.vb (dla [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), a następnie dodaj następujący kod:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Ten kod dodaje funkcje kliknij przycisk części sieci web.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Dodaj wizualny składnik Web Part do strony domyślnej ASPX  
 Następnie dodaj wizualnego składnika Web part do definicji witryny domyślnej strony ASPX.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Aby dodać wizualny składnik Web part do domyślnej strony ASPX  
  
1.  Otwórz stronę default.aspx, a następnie dodaj następujący wiersz w obszarze `WebPartPages` tagu:  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Ten wiersz kojarzy nazwę MyWebPartControls z części sieci Web i jej kodu. *Namespace* parametr przestrzeni nazw, który jest używany w pliku kodu VisualWebPart1.ascx jest zgodny.  
  
2.  Po `</asp:Content>` elementu, Zastąp całą `ContentPlaceHolderId="PlaceHolderMain"` sekcji i jego zawartość następującym kodem:  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Ten kod tworzy odwołanie do visual składnik Web part, który został utworzony wcześniej.  
  
3.  W **Eksploratora rozwiązań**, otwórz menu skrótów **SiteDefinition1** węzeł, a następnie wybierz pozycję **Ustaw jako element startowy**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Wdrażanie i uruchomienie rozwiązania definicji witryny  
 Następnie Wdróż projekt w programie SharePoint, a następnie uruchom projekt.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>Aby wdrożyć i uruchomić definicję witryny  
  
-   Na pasku menu wybierz **kompilacji**, **wdrażanie TestSiteDef**.  
  
-   Wybierz klawisz F5.  
  
     Visual Studio kompiluje kod, dodaje jej funkcje, umieszcza wszystkie pliki w pliku rozwiązania (WSP) programu SharePoint i wdraża pliku WSP do serwera programu SharePoint. SharePoint następnie instaluje pliki, a następnie aktywuje funkcji.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Utwórz witrynę na podstawie definicji witryny  
 Następnie utwórz witrynę za pomocą nowej definicji lokacji.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Aby utworzyć witrynę przy użyciu definicji witryny  
  
1.  W witrynie programu SharePoint zostanie wyświetlona strona nową witrynę programu SharePoint.  
  
2.  W **tytuł i opis** wprowadź **Moja nowa witryna** tytuł i opis witryny.  
  
3.  W **adres witryny sieci Web** wprowadź **MojaNowaWitryna** w **nazwa adresu URL** pole.  
  
4.  W **szablonu** wybierz **dostosowań SharePoint** kartę.  
  
5.  W **wybierz szablon** wybierz **SiteDefinition1**.  
  
6.  Pozostaw wartości domyślne inne ustawienia, a następnie wybierz **Utwórz** przycisku.  
  
     Pojawi się nowa lokacja.  
  
## <a name="test-the-new-site"></a>Testuj nową stronę  
 Następnie testować nowej lokacji, aby sprawdzić, czy działa poprawnie.  
  
#### <a name="to-test-the-new-site"></a>Aby przetestować nową stronę  
  
-   Na stronie ASPX domyślnej wprowadź tekst, a następnie wybierz pozycję **Zmień tekst etykiety** przycisk obok pola tekstowego.  
  
     Tekst jest wyświetlany w etykiecie po prawej stronie przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  