---
title: "Wskazówki: Tworzenie strony aplikacji SharePoint | Dokumentacja firmy Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e49e8d50905dc0bb0b3c104a7133fe7435e2e944
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-sharepoint-application-page"></a>Wskazówki: tworzenie strony aplikacji SharePoint
  Strony aplikacji jest specjalna forma strony platformy ASP.NET. Strony aplikacji mają zawartość, która jest scalany z strony wzorcowej programu SharePoint. Aby uzyskać więcej informacji, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 W tym przewodniku przedstawiono sposób tworzenia strony aplikacji i debugować go przy użyciu lokalnej witryny programu SharePoint. Ta strona zawiera wszystkie elementy, które każdy użytkownik ma utworzone lub zmodyfikowane we wszystkich lokacjach w farmie serwerów.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektu programu SharePoint.  
  
-   Dodawanie strony aplikacji do projektu programu SharePoint.  
  
-   Dodawanie formantów ASP.NET do strony aplikacji.  
  
-   Dodawanie kodzie formantów ASP.NET.  
  
-   Testowanie strony aplikacji.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Windows i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]lub w wersji programu Visual Studio Ultimate lub Visual Studio Premium.  
  
## <a name="creating-a-sharepoint-project"></a>Tworzenie projektu programu SharePoint  
 Najpierw utwórz **pusty projekt SharePoint**. Później, należy dodać **strony aplikacji** elementu do tego projektu.  
  
#### <a name="to-create-a-sharepoint-project"></a>Aby utworzyć projekt programu SharePoint  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Otwórz **nowy projekt** okna dialogowego rozwiń **Office i SharePoint** węźle język, który chcesz użyć, a następnie wybierz pozycję **rozwiązań SharePoint** węzła.  
  
3.  W **szablony Visual Studio zainstalowany** okienku wybierz **programu SharePoint 2010 — pusty projekt** szablonu. Nazwij projekt **MySharePointProject**, a następnie wybierz pozycję **OK** przycisku.  
  
     **Kreator dostosowania programu SharePoint** pojawi się. Ten kreator umożliwia wybór lokacji, który będzie używany do debugowania projektu i poziom zaufania rozwiązania.  
  
4.  Wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz pozycję **Zakończ** przycisk, aby zaakceptować domyślne lokalnej witryny programu SharePoint.  
  
## <a name="creating-an-application-page"></a>Tworzenie strony aplikacji  
 Aby utworzyć stronę aplikacji, należy dodać **strony aplikacji** elementu do projektu.  
  
#### <a name="to-create-an-application-page"></a>Aby utworzyć stronę aplikacji  
  
1.  W **Eksploratora rozwiązań**, wybierz **MySharePointProject** projektu.  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** oknie dialogowym wybierz **strony aplikacji (tylko rozwiązanie farmy** szablonu.  
  
4.  Nazwa strony **SearchItems**, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Projektant Visual Web Developer, zostanie wyświetlona strona aplikacji w **źródła** umożliwia wyświetlenie elementów HTML strony widoku. Projektant wyświetla kod znaczników dla wielu <xref:System.Web.UI.WebControls.Content> kontrolki. Mapuje każdego formantu <xref:System.Web.UI.WebControls.ContentPlaceHolder> formant, który jest zdefiniowany w domyślnej strony głównej aplikacji.  
  
## <a name="designing-the-layout-of-the-application-page"></a>Projektowanie układu strony aplikacji  
 Element strony aplikacji umożliwia przy użyciu projektanta Dodaj formanty ASP.NET do strony aplikacji. Ten Projektant jest tej samej projektanta używane w programie Visual Web Developer. Dodaj etykietę, listy przycisków radiowych i tabela, która ma **źródła** wyświetlić projektanta, a następnie ustaw właściwości w taki sam sposób jak podczas projektowania wszystkie standardowe strony ASP.NET.  
  
#### <a name="to-design-the-layout-of-the-application-page"></a>Aby zaprojektować układ strony aplikacji  
  
1.  Na pasku menu wybierz **widoku**, **przybornika**.  
  
2.  W węźle standardowe **przybornika**, wykonaj jedną z następujących czynności:  
  
    -   Otwórz menu skrótów **etykiety** element, wybierz **kopiowania**, otwórz menu skrótów wiersza w obszarze **PlaceHolderMain** zawartości formantu w projektancie, a następnie Wybierz **Wklej**.  
  
    -   Przeciągnij **etykiety** elementu z **przybornika** na treść **PlaceHolderMain** zawartości formantu.  
  
3.  Powtórz poprzedni krok, aby dodać **DropDownList** elementu i **tabeli** elementu do **PlaceHolderMain** zawartości formantu.  
  
4.  W projektancie, zmień wartość `Text` atrybut formantu etykiety **Pokaż wszystkie elementy**.  
  
5.  W projektancie, Zastąp `<asp:DropDownList>` elementu za pomocą następujących XML.  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## <a name="handling-the-events-of-controls-on-the-page"></a>Obsługa zdarzeń formantów na stronie  
 Obsługa formantów strony aplikacji, tak samo jak dowolnej strony ASP.NET. W ramach tej procedury będzie obsługiwać `SelectedIndexChanged` zdarzenia z listy rozwijanej.  
  
#### <a name="to-handle-the-events-of-controls-on-the-page"></a>Do obsługi zdarzeń formantów na stronie  
  
1.  Na **widoku** menu, wybierz **kod**.  
  
     Plik kodu strony aplikacji zostanie otwarty w edytorze kodu.  
  
2.  Dodaj następującą metodę do `SearchItems` klasy. Ten kod obsługi <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> zdarzenia <xref:System.Web.UI.WebControls.DropDownList> , wywołując metodę, która zostanie utworzona w dalszej części tego przewodnika.  
  
     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]  
  
3.  Dodaj następujące instrukcje na początku pliku kodu strony aplikacji.  
  
     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]  
  
4.  Dodaj następującą metodę do `SearchItems` klasy. Ta metoda wykonuje iterację wszystkich lokacji w farmie serwerów i wyszukuje elementy utworzone lub zmodyfikowane przez bieżącego użytkownika.  
  
     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]  
  
5.  Dodaj następującą metodę do `SearchItems` klasy. Ta metoda Wyświetla elementy utworzone lub zmodyfikowane przez bieżącego użytkownika w tabeli.  
  
     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]  
  
## <a name="testing-the-application-page"></a>Testowanie strony aplikacji  
 Po uruchomieniu projektu otwiera witrynę programu SharePoint i wyświetleniu strony aplikacji.  
  
#### <a name="to-test-the-application-page"></a>Aby przetestować stronę aplikacji  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla strony aplikacji, a następnie wybierz **Ustaw jako element startowy**.  
  
2.  Wybierz klawisz F5.  
  
     Otwieranie witryny programu SharePoint.  
  
3.  Na stronie aplikacji wybierz **zmodyfikowane przeze mnie** opcji.  
  
     Strona aplikacji odświeża i wyświetla wszystkie elementy, które zostały zmodyfikowane we wszystkich lokacjach w farmie serwerów.  
  
4.  Na stronie aplikacji wybierz **utworzone przeze mnie** na liście.  
  
     Strona aplikacji odświeża i wyświetla wszystkie elementy, które zostały utworzone we wszystkich lokacjach w farmie serwerów.  
  
## <a name="next-steps"></a>Następne kroki  
 Aby uzyskać więcej informacji na temat stron aplikacji programu SharePoint, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Możesz można dowiedzieć się więcej na temat projektowania zawartości strony programu SharePoint przy użyciu projektanta wizualnego sieci Web z tych tematów:  
  
-   [Tworzenie składników Web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md)   
 [Wpisz _layouts aplikacji](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  