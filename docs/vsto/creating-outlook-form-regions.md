---
title: Tworzenie regionów formularzy programu Outlook | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 550514444e7931b188951bbf05f8d371bc361aca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="creating-outlook-form-regions"></a>Tworzenie regionów formularzy w programie Outlook
  Regiony formularzy służy do dostosowywania formularzy programu Microsoft Office Outlook. Program Visual Studio udostępnia zaawansowane narzędzia, które ułatwiają projektowanie, tworzenie i debugowania regionów formularzy.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Ten temat zawiera następujące informacje:  
  
-   [Korzyści wynikające z używania regionów formularzy](#Enhance)  
  
-   [Dodawanie do projektu regionów formularzy programu Outlook](#Adding)  
  
-   [Przy użyciu projektanta regionów formularza](#UsingFormRegionDesigner)  
  
-   [Za pomocą regionów formularzy zaprojektowanych w programie Outlook](#UsingFormRegionDesignedOutlook)  
  
-   [Dodawanie niestandardowego kodu do regionu formularza](#AddingCustomCode)  
  
-   [Tworzenie projektu](#Building)  
  
-   [Debugowanie regionów formularzy](#Debugging)  
  
-   [Wdrażanie regionów formularzy](#Deploying)  
  
##  <a name="Enhance"></a> Korzyści wynikające z używania regionów formularzy  
 Regiony formularzy oferują wiele udoskonaleń za pośrednictwem tradycyjnych tworzeniu formularzy programu Outlook:  
  
-   Dostosowywanie domyślnej strony wszystkie standardowe formularza.  
  
-   Dodaj do 12 dodatkowych stron do żadnych standardowych formularza.  
  
-   Zastąp lub rozszerzają wszystkie standardowe formularza.  
  
-   Wyświetlanie interfejsu użytkownika, w okienku odczytu i inspektorzy.  
  
 Aby uzyskać więcej informacji, zobacz [Dostosowywanie strony formularza i regionów formularzy](http://msdn.microsoft.com/library/office/ff869060.aspx).  
  
##  <a name="Adding"></a> Dodawanie do projektu regionów formularzy programu Outlook  
 Można użyć **nowych regionów formularzy programu Outlook** kreatora w celu projektowania nowego regionu formularza lub importowanie regionów formularzy, który został zaprojektowany w programie Outlook. Ponadto jeśli masz regionu formularza, który został użyty w innym projekcie dodatku narzędzi VSTO programu Outlook, można ponownie użyć istniejącego regionu formularza.  
  
###  <a name="CreatingFormRegion"></a> Tworzenie nowego regionu formularza za pomocą Kreatora  
 Aby utworzyć regionu formularza, dodać **regionów formularzy programu Outlook** element do projektów dodatku VSTO dla programu Outlook. Spowoduje to uruchomienie **nowych regionów formularzy programu Outlook** kreatora.  
  
 Użyj kreatora, aby wskazać, czy mają być projektowania nowego regionu formularza lub importowanie regionów formularzy, który został zaprojektowany w programie Outlook. Aby uzyskać więcej informacji na temat opracowywania nowego regionu formularza, zobacz [przy użyciu projektanta regionów formularza](#UsingFormRegionDesigner). Aby uzyskać więcej informacji o używaniu regionów formularzy zaprojektowanych w programie Outlook, zobacz [importowanie regionu formularza w programie Outlook zaprojektowane](#UsingFormRegionDesignedOutlook).  
  
 Użyj kreatora, aby określić typ regionu formularza, który chcesz utworzyć. W poniższej tabeli opisano każdy typ regionu formularza.  
  
|Typ regionu|Opis|  
|-----------------|-----------------|  
|Oddzielne|Dodaje regionu formularza jako nową stronę w formularzu programu Outlook.|  
|Sąsiadujące|Dołącza regionu formularza do dolnej części strony domyślnego formularza programu Outlook.|  
|Zastąpienie|Dodaje regionu formularza jako nowa strona, która zastępuje domyślną stronę formularz programu Outlook.|  
|Zamień wszystkie|Zamienia cały formularz Outlook regionu formularza.|  
  
 Można także użyć kreatora w celu określenia warunków wyświetlania i wybrać typ formularza do rozszerzenia. Aby uzyskać więcej informacji, zobacz [porady: dodawanie regionu formularza do projektu dodaj programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Wybrane w Kreatorze wpływa na opcje, które są dostępne w innych stron kreatora. Na przykład w przypadku wybrania **Adjoining** lub **oddzielnych** w **tworzenie nowych regionów formularzy programu Outlook** strony, a następnie **tytuł** i **Opis** pola są niedostępne w przypadku **Podaj opis, a następnie wybierz preferencje wyświetlania** strony. Jest to spowodowane Outlook nie używa tych pól wyświetlanych sąsiadujących lub osobnych regionu formularza.  
  
#### <a name="form-region-files"></a>Pliki regionów formularzy  
 Po zakończeniu **nowych regionów formularzy programu Outlook** kreatora, Visual Studio automatycznie dodaje następujące pliki do projektu:  
  
-   Plik kodu regionu formularza. Ten plik ma nazwę, którą określisz dla **regionów formularzy programu Outlook** elementu **Dodaj nowy element** okno dialogowe. Dodaj kod obsługi zdarzenia regionu formularza do tego pliku.  
  
-   Plik projektanta kodu regionu formularza. Ten plik zawiera kod wygenerowany przez projektanta regionów formularza i nie należy bezpośrednio edytować.  
  
-   Plik magazynu formularzy programu Outlook (.ofs).  
  
    > [!NOTE]  
    >  Ten plik jest tylko dodany do projektu po zaimportowaniu regionu formularza, który został zaprojektowany w programie Outlook.  
  
#### <a name="form-region-factory-class"></a>Klasa fabryki regionu formularza  
 Plik kodu regionu formularza zawiera częściowej klasy, która implementuje <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> interfejsu. Jest to klasa fabryki regionu formularza. Klasa fabryki region formularza jest odpowiedzialny za tworzenie nowych wystąpień regionu formularza.  
  
 Ta klasa można znaleźć, rozwijając **fabryki regionu formularza** regionu.  
  
 **Nowych regionów formularzy programu Outlook** Kreator dodaje atrybuty do tej klasy, która określ nazwy wewnętrznej regionu formularza i klasy wiadomości, które wyświetlania regionu formularza. Należy ręcznie zmodyfikować te atrybuty po dodaniu pliku do projektu.  
  
 Większość klasę fabryki region formularza jest zaimplementowana w pliku projektanta regionu formularza. Jednak `FormRegionInitializing` program obsługi zdarzeń jest widoczna w pliku kodu regionu formularza. Ten program obsługi zdarzeń służy do określania, czy program Outlook powinien wyświetlać regionu formularza. Aby uzyskać więcej informacji, zobacz [obsługi zdarzeń regionu formularza](#HandlingFormRegionEvents).  
  
###  <a name="AddingExistingFormRegion"></a> Dodawanie istniejącego regionu formularza do projektu  
 Jeśli masz regionów formularzy programu Outlook, który został użyty w innym projekcie programu Outlook, może używać go w bieżącym projekcie dodatku narzędzi VSTO programu Outlook przy użyciu **Dodaj istniejący element** okno dialogowe.  
  
 Istniejące regionu formularza musi zawierać plik kodu (.vb lub .cs); Nie można dodać magazyn formularzy programu Outlook (.ofs) pliki za pomocą **Dodaj istniejący element** okno dialogowe. Jednak można utworzyć nowego regionu formularza przez zaimportowanie pliku magazynu formularzy programu Outlook. Aby uzyskać więcej informacji, zobacz [porady: dodawanie regionu formularza do projektu dodaj programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
##  <a name="UsingFormRegionDesigner"></a> Przy użyciu projektanta regionów formularza  
 Projektanta regionów formularza ułatwia projektowanie układu i wyglądu regionu formularza. Przeciągnij formanty zarządzane na powierzchnię projektanta, kliknij dwukrotnie kontroli w celu otwarcia procedury obsługi zdarzeń i ustawiać właściwości **właściwości** okna.  
  
> [!NOTE]  
>  Można znaleźć właściwości, które mają wpływ na sposób region formularza zostanie wyświetlony w programie Outlook poniżej **manifestu** w węźle **właściwości** okna.  
  
 Projektanta regionów formularza jest dostępna, tylko jeśli wybierzesz **projektowania nowego regionu formularza** w **wybierz jak chcesz utworzyć regionu formularza** strony **nowych regionów formularzy programu Outlook** Kreator.  
  
 Istnieją trzy sposoby Otwórz projektanta regionów formularza:  
  
-   W **Eksploratora rozwiązań**, kliknij dwukrotnie plik kodu regionu formularza.  
  
-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik kodu regionu formularza, a następnie kliknij przycisk **Widok projektanta**.  
  
-   W **Eksploratora rozwiązań**, wybierz plik kodu regionu formularza, a następnie na **widoku** menu, kliknij przycisk **projektanta**.  
  
 Obsługuje projektanta regionów formularza tylko zarządzane formanty. Nie można dodać kontrolki natywne programu Outlook.  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> Importowanie regionów formularzy zaprojektowanych w programie Outlook  
 Podczas projektowania w programie Outlook można dodać kontrolki natywne Outlook do regionu formularza. Kontrolki natywne programu Outlook umożliwia powiązanie z danymi programu Outlook w czasie projektowania. Jednak nie można następnie użyć projektanta regionów formularza dodaj formanty zarządzane lub zmienić projekt regionu formularza.  
  
 Regiony formularzy można importować do projektów dodatku VSTO dla programu Outlook przy użyciu **nowych regionów formularzy programu Outlook** kreatora. Na **wybierz jak chcesz utworzyć regionu formularza** wybierz **Importowanie pliku magazynu formularzy programu Outlook (.ofs)**. Możesz następnie przejść do lokalizacji magazynu formularzy programu Outlook (.ofs) pliku. (Outlook zapisuje regionów formularzy jako pliki .ofs).  
  
 **Nowych regionów formularzy programu Outlook** Kreator skopiuje plik .ofs do katalogu projektu i dodaje kontroli odwołania do pliku projektanta regionów formularza. Następnie można obsługiwać zdarzenia formantów w pliku kodu regionu formularza.  
  
 Do obsługi zdarzeń w projektach Visual Basic, wybierz zdarzenie z listy Nazwa metody u góry edytora kodu.  
  
 Do obsługi zdarzeń w projekcie C#, subskrybowanie zdarzeń kontrolowania w <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> metody. Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń &#40;C&#35; przewodnik programowania w języku&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).  
  
 Można zmienić właściwości regionu formularza w `InitializeManifest` metody klasy fabryki regionu formularza.  
  
> [!NOTE]  
>  Aby zaimportować regionu formularza, jest możliwe w projekcie którego element docelowy tę samą wersję programu Outlook, który jest zainstalowany na komputerze dewelopera. Na przykład, jeśli masz zainstalowany program Outlook 2010, importowanie formularza region będzie działać tylko w projekcie został utworzony przy użyciu **Outlook 2010 Add-in** szablonu projektu.  
  
### <a name="updating-an-imported-form-regions-design"></a>Aktualizowanie projektu regionu formularza zaimportowany  
 Można dodać, usunąć ani zmienić kontrole regionu formularza. Zanim to zrobisz, Utwórz kopię zapasową dowolny kod, który został dodany do pliku kodu regionu formularza. Następnie otwórz plik .ofs w programie Outlook, zmodyfikuj regionu formularza, a następnie zapisz zmiany. Użyj **nowych regionów formularzy programu Outlook** kreatora w celu zaimportowania pliku .ofs zmodyfikowane. Następnie można wkleić kod do nowego pliku kodu regionu formularza.  
  
##  <a name="AddingCustomCode"></a> Dodawanie niestandardowego kodu do regionu formularza  
 <xref:Microsoft.Office.Tools.Outlook> Przestrzeni nazw umożliwia dostęp do klasy reprezentujące region formularza, elementu programu Outlook, który wyświetla regionu formularza i inne przydatne elementy. **Regionów formularzy programu Outlook** elementu automatycznie dodaje odwołania do tego zestawu w projekcie i wstawia odpowiednie **przy użyciu** lub **importów** instrukcji w górnej części plik kodu regionu formularza.  
  
 Klas, metod i właściwości można użyć w przestrzeni nazw Microsoft.Office.Interop.Outlook do wykonywania większości zadań programowania programu Outlook. Aby uzyskać więcej informacji o modelu obiektów programu Outlook, zobacz [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md). Przykłady typowych zadań, które należy użyć modelu obiektów programu Outlook, zobacz [rozwiązania programu Outlook](../vsto/outlook-solutions.md).  
  
###  <a name="HandlingFormRegionEvents"></a> Obsługa zdarzeń regionu formularza  
 **Regionów formularzy programu Outlook** elementu automatycznie dodaje obsługi następujących trzech zdarzeń do pliku kodu regionu formularza.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|FormRegionInitializing|Występuje, zanim region formularza zostanie zainicjowany. Możesz sprawdzić warunków w tej obsłudze zdarzeń, aby określić, czy program Outlook powinien wyświetlać regionu formularza. Aby uzyskać więcej informacji, zobacz [porady: zapobieganie Outlook przy wyświetlaniu regionu formularza](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|  
|FormRegionShowing|Występuje po utworzeniu wystąpienia obszaru formularza, ale przed pojawieniem się obszaru formularza.|  
|FormRegionClosed|Występuje przed zamknięciem obszaru formularza.|  
  
##  <a name="Building"></a> Tworzenie projektu  
 Podczas tworzenia projektów dodatku VSTO dla programu Outlook zawierający regionów formularzy programu Visual Studio dodaje następujące informacje w rejestrze:  
  
-   Klucz dla każdej klasy wiadomości, który jest skojarzony z co najmniej jeden regionów formularzy.  
  
-   Wpis dla każdego regionu formularza i skojarzona wartość, która reprezentuje nazwę dodatku VSTO dla programu Outlook.  
  
 Outlook używa tych informacji do załadowania regionów formularzy.  
  
##  <a name="Debugging"></a> Debugowanie regionów formularzy  
 Można debugować dodatku VSTO dla programu Outlook zawierający regionu formularza, tak jak będzie debugowania innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów. Po rozpoczęciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugera programu Visual Studio automatycznie uruchamia program Outlook.  
  
 Aby wyświetlić regionów formularzy, należy otworzyć odpowiedniego elementu programu Outlook. Na przykład jeśli sąsiadujących region formularza jest dołączany na końcu elementu poczty, otwórz element poczty.  
  
##  <a name="Deploying"></a> Wdrażanie regionów formularzy  
 Regiony formularzy są wdrażane automatycznie z skojarzone dodatku VSTO dla programu Outlook. W związku z tym nie trzeba wykonywać żadnych specjalnych zadania w celu wdrożenia regionu formularza. Aby uzyskać więcej informacji na temat wdrażania dodatków VSTO zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wytyczne dotyczące tworzenia regionów formularzy w programie Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Zawiera informacje, które mogą pomóc w optymalizacji sieci regionów formularzy i uniknąć ewentualnych problemów.|  
|[Instrukcje: Dodawanie regionu formularza do projektu dodatków w programie Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Pokazuje, jak utworzyć regionu formularza, aby rozszerzyć za pomocą standardowych lub niestandardowych formularzy programu Microsoft Office Outlook **nowych regionów formularzy programu Outlook** kreatora.|  
|[Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Wyjaśniono, jak określić elementy, które program Microsoft Office Outlook wyświetlania regionu formularza przez kojarzenie regionu formularza z klasą wiadomości poszczególnych elementów.|  
|[Przewodnik: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)|Pokazuje, jak projektowanie regionów formularzy niestandardowych wyświetlany jako nową stronę w oknie inspektora w elemencie kontaktu.|  
|[Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Pokazuje, jak projektowanie regionów formularzy w programie Microsoft Office Outlook, a następnie zaimportuj regionów formularzy w projekcie dodatku narzędzi VSTO programu Outlook przy użyciu **nowych regionów formularzy programu Outlook** kreatora.|  
|[Uzyskiwanie dostępu do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)|Opisuje, jak napisać kod, aby wyświetlić, Ukryj lub modyfikowanie formantów na region formularza i włączyć użytkownikom na uruchamianie kodu z innych obszarów w projekcie przy użyciu `Globals` klasy.|  
|[Instrukcje: Ochrona programu Outlook przed wyświetlaniem regionów formularzy](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Pokazuje, jak zapobiec wyświetlaniu regionu formularza dla danego elementu programu Microsoft Office Outlook.|  
|Pokazuje, jak można uzyskać dostępu do elementu programu Outlook, w której znajduje się regionu formularza.|  
|[Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|Opisuje sposób użytkownicy mogli odpowiedzieć elementu programu Outlook.|  
  
  