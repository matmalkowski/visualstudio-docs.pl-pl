---
title: "Wskazówki: Tworzenie składnika Web Part dla SharePoint za pomocą projektanta | Dokumentacja firmy Microsoft"
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
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 28be854f01234783ff9873753eb88ca92bc192d6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer"></a>Wskazówki: tworzenie składnika Web part dla SharePoint za pomocą Projektanta
  Jeśli tworzysz części sieci web dla witryny programu SharePoint, użytkownicy bezpośrednio można zmodyfikować zawartość, wyglądu i zachowania stron w tej lokacji za pomocą przeglądarki. W tym przewodniku przedstawiono sposób wizualnie Tworzenie składnika web part za pomocą programu SharePoint **wizualnego składnika Web Part** szablonu projektu w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Składnik web part, które zostaną utworzone Wyświetla widok kalendarza miesięcznego i pola wyboru dla każdej listy kalendarza w witrynie. Użytkownicy mogą określić, który kalendarz wymieniono do uwzględnienia w widok kalendarza miesięcznego przez zaznaczenie pola wyboru.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie składnika web part za pomocą **wizualnego składnika Web Part** szablonu projektu.  
  
-   Projektowanie składnika web part za pomocą projektanta programu Visual Web Developer w programie Visual Studio.  
  
-   Dodawanie kodu do obsługi zdarzeń formantów w części sieci web.  
  
-   Testowanie części sieci web w programie SharePoint.  
  
    > [!NOTE]  
    >  W poniższych instrukcjach komputera mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika dla programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Windows i programu SharePoint. Zobacz [wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]lub nowszej wersji.  
  
## <a name="creating-a-web-part-project"></a>Tworzenie projektu części sieci web  
 Najpierw utwórz projekt części sieci web za pomocą **wizualnego składnika Web Part** szablonu projektu.  
  
#### <a name="to-create-a-visual-web-part-project"></a>Aby utworzyć projekt Visual składnika Web Part  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] za pomocą **Uruchom jako Administrator** opcji.  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
3.  W **nowy projekt** okno dialogowe, w obszarze albo **Visual C#** lub **Visual Basic**, rozwiń węzeł **Office i SharePoint**, a następnie wybierz pozycję  **Rozwiązania programu SharePoint** kategorii.  
  
4.  Na liście szablonów wybierz **SharePoint 2013 — wizualnego składnika Web Part** szablonu, a następnie wybierz pozycję **OK** przycisk.  
  
     **Kreator dostosowania programu SharePoint** pojawi się. Za pomocą tego kreatora, można określić lokacji, który ma być używany do debugowania projektu i poziom zaufania rozwiązania.  
  
5.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji.  
  
6.  Wybierz **Zakończ** przycisk, aby zaakceptować domyślne lokalnej witryny programu SharePoint.  
  
## <a name="designing-the-web-part"></a>Projektowanie składnika web part  
 Projektowanie części sieci web, dodając formantów z **przybornika** na powierzchnię projektanta Visual Web Developer.  
  
#### <a name="to-design-the-layout-of-the-web-part"></a>Aby zaprojektować układ części sieci web  
  
1.  W Projektancie Visual Web Developer, wybierz polecenie **projekt** tab, aby przełączyć do widoku projektu.  
  
2.  Na pasku menu wybierz **widoku**, **przybornika**.  
  
3.  W **standardowe** węzła **przybornika**, wybierz **CheckBoxList** kontroli, a następnie wykonaj jedną z następujących czynności:  
  
    -   Otwórz menu skrótów **CheckBoxList** sterowania, wybierz **kopiowania**, otwórz menu skrótów dla pierwszego wiersza w projektancie, a następnie wybierz pozycję **Wklej**.  
  
    -   Przeciągnij **CheckBoxList** kontrolować z **przybornika**i połącz formantu do pierwszego wiersza w projektancie.  
  
4.  Powtórz poprzedni krok, ale Przenoszenie przycisku do następnego wiersza projektanta.  
  
5.  W projektancie, wybierz **Button1** przycisku.  
  
6.  Na pasku menu wybierz **widoku**, **okna właściwości**.  
  
     **Właściwości** zostanie otwarte okno.  
  
7.  W **tekst** właściwości przycisku, wprowadź **aktualizacji**.  
  
## <a name="handling-the-events-of-controls-on-the-web-part"></a>Obsługa zdarzeń formantów w części sieci web  
 Dodaj kod, który umożliwia użytkownikowi dodanie kalendarzy widoku głównego kalendarza.  
  
#### <a name="to-handle-events-of-controls-on-the-web-part"></a>Do obsługi zdarzeń formantów w części sieci web  
  
1.  Wykonaj jeden z następujących zestawów czynności:  
  
    -   W projektancie, kliknij dwukrotnie **aktualizacji** przycisku.  
  
    -   W **właściwości** w oknie **aktualizacji** przycisku, wybierz **zdarzenia** przycisku. W **kliknij** właściwości, wprowadź **Button1_Click**, a następnie wybierz klawisz Enter.  
  
     Plik kodu formantu użytkownika zostanie otwarty w edytorze kodu i `Button1_Click` pojawi się program obsługi zdarzeń. Później zostanie dodany kod, aby ten program obsługi zdarzeń.  
  
2.  Dodaj następujące instrukcje na początku pliku kodu kontrolki użytkownika.  
  
     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
3.  Dodaj następujący wiersz kodu w celu `VisualWebPart1` klasy. Ten kod deklaruje formantu view kalendarza miesięcznego.  
  
     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]  
  
4.  Zastąp `Page_Load` metody `VisualWebPart1` klasy następującym kodem. Kod będzie wykonywał następujące zadania:  
  
    -   Dodaje widok kalendarza miesięcznego do kontrolki użytkownika.  
  
    -   Dodaje pole wyboru dla każdej listy kalendarza w witrynie.  
  
    -   Określa szablon dla każdego typu elementu, który jest wyświetlany w widoku Kalendarz.  
  
     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]  
  
5.  Zastąp `Button1_Click` metody `VisualWebPart1` klasy następującym kodem. Ten kod dodaje elementy z każdego wybranego kalendarza do widoku głównego kalendarza.  
  
     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]  
  
## <a name="testing-the-web-part"></a>Testowanie składnika web part  
 Po uruchomieniu projektu otwiera witrynę programu SharePoint. Składnik web part jest automatycznie dodawany do galerii składników Web Part w programie SharePoint. Aby przetestować ten projekt, będziesz wykonywać następujące zadania:  
  
-   Dodawanie zdarzenia do każdego z dwóch oddzielnych kalendarza list.  
  
-   Dodaj składnik web part do strony sieci web.  
  
-   Określ listy, aby uwzględnić w widoku kalendarza miesięcznego.  
  
#### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Aby dodać zdarzenia do listy kalendarza w lokacji  
  
1.  W programie Visual Studio wybierz klawisz F5.  
  
     Otwieranie witryny programu SharePoint oraz [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] pasek Szybkie uruchamianie jest wyświetlany na stronie.  
  
2.  Na pasku Szybkie uruchamianie w obszarze **wymieniono**, wybierz **kalendarza** łącza.  
  
     **Kalendarza** zostanie wyświetlona strona.  
  
     Jeśli użytkownik nie łącz kalendarza zostanie wyświetlony na pasek Szybkie uruchamianie, wybrać **zawartość witryny** łącza. Jeśli nie wyświetla stronę zawartość witryny **kalendarza** element, utwórz je.  
  
3.  Na stronie kalendarza wybierz dzień, a następnie wybierz **Dodaj** łącze wybranego dnia, aby dodać zdarzenie.  
  
4.  W **tytuł** wprowadź **zdarzeń w kalendarzu domyślne**, a następnie wybierz pozycję **zapisać** przycisku.  
  
5.  Wybierz **zawartość witryny** łącza, a następnie wybierz pozycję **Dodaj aplikację** kafelka.  
  
6.  Na **Utwórz** wybierz pozycję **kalendarza** typ, nazwa kalendarza, a następnie wybierz **Utwórz** przycisku.  
  
7.  Dodawanie zdarzeń do kalendarza nowe, Nazwa zdarzenia **zdarzenia w niestandardowego kalendarza**, a następnie wybierz **zapisać** przycisku.  
  
#### <a name="to-add-the-web-part-to-a-web-part-page"></a>Aby dodać składnik web part do strony sieci web  
  
1.  Na **zawartość witryny** Otwórz **stron w witrynie** folderu.  
  
2.  Na Wstążce, wybierz **pliki** kartę, otwórz **nowy dokument** menu, a następnie wybierz pozycję **strony składników Web Part** polecenia.  
  
3.  Na **Nowa strona części sieci Web** strony, nazwy strony **SampleWebPartPage.aspx**, a następnie wybierz pozycję **Utwórz** przycisku.  
  
     Zostanie wyświetlona strona części sieci web.  
  
4.  W strefie górnej części strony sieci web, wybierz **Wstaw** karcie, a następnie wybierz pozycję **składnika Web Part** przycisku.  
  
5.  Wybierz **niestandardowy** folderu, wybierz **VisualWebPart1** składnik web part, a następnie wybierz pozycję **Dodaj** przycisku.  
  
     Składnik web part jest wyświetlany na stronie. W części sieci web są wyświetlane następujące sterowniki:  
  
    -   Widok kalendarza miesięcznego.  
  
    -   **Aktualizacji** przycisku.  
  
    -   A **kalendarza** pole wyboru.  
  
    -   A **niestandardowego kalendarza** pole wyboru.  
  
#### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Aby określić listę do uwzględnienia w widok kalendarza miesięcznego  
  
1.  W części sieci web, określ kalendarzy, które chcesz uwzględnić w widoku miesięczny kalendarz, a następnie wybierz **aktualizacji** przycisku.  
  
     Zdarzenia ze wszystkich kalendarzy, określone przez użytkownika są wyświetlane w widoku kalendarza miesięcznego.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie składników Web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Porady: tworzenie SharePoint Web Part](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Porady: tworzenie SharePoint Web Part za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Przewodnik: Tworzenie części sieciowej dla SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  