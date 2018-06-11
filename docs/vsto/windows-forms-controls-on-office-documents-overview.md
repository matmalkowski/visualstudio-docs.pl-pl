---
title: Formanty formularzy systemu Windows na przegląd dokumentów pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a8ac517153555b6e18726d7343b510c68533117a
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258713"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Formanty formularzy systemu Windows na przegląd dokumentów pakietu Office
  Formanty formularzy systemu Windows są obiektami, które użytkownicy mogą wykorzystywać do wprowadzania lub manipulować danymi. W projektach na poziomie dokumentu dla programu Microsoft Office Excel i Microsoft Office Word można dodać formanty formularzy systemu Windows do dokumentu lub skoroszytu w projekcie w czasie projektowania lub tych kontrolek można dodać programistycznie w czasie wykonywania. Tych kontrolek można programowo dodać otwartego dokumentu lub arkusza w czasie wykonywania w dodatku VSTO dla programu Excel lub Word.  
  
 Aby uzyskać więcej informacji, zobacz [porady: formanty formularzy systemu Windows dodawanie do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="use-windows-forms-controls"></a>Formanty formularzy systemu Windows  
 Formanty formularzy systemu Windows można dodać do dokumentów oraz do elementów interfejsu użytkownika można dostosowywać, łącznie z okienka akcji niestandardowych okienek zadań i formularzy systemu Windows. Formanty formularzy systemu Windows mają zwykle takie samo zachowanie w dokumentach jako na inne elementy interfejsu użytkownika, ale istnieją pewne różnice. Aby uzyskać informacje, zobacz [formanty ograniczenia formularzy systemu Windows w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 Decyzja, czy dodać formanty formularzy systemu Windows do innego elementu interfejsu użytkownika lub dokumentu zależy od wielu czynników. Podczas projektowania rozwiązania do interfejsu użytkownika, należy wziąć pod uwagę zastosowań formanty formularzy systemu Windows zgodnie z opisem w poniższej tabeli.  
  
 W dokumencie.  
 -   Jeśli chcesz wyświetlić formanty 100% czasu.  
  
-   Gdy ma użytkownikom na wprowadzanie danych bezpośrednio w dokumencie, na przykład w dokumentach oparte na formularzach, gdzie jest zablokowany do edycji powierzchni.  
  
-   Kiedy zechcesz, służy do wyświetlania zgodnie z danymi w dokumencie. Na przykład jeśli dodajesz przyciski do każdego wiersza obiekt listy, czy chcesz je zgodnie z każdego elementu listy.  
  
 W okienku Akcje lub niestandardowego okienka zadań.  
 -   Gdy chcesz udostępnić informacje kontekstowe użytkownikowi.  
  
-   Po tylko wyniki mają być wyświetlane w dokumencie i nie formanty zapytania i danych.  
  
-   Jeśli chcesz upewnić się, że formanty nie są drukowane na dokument.  
  
-   Jeśli chcesz upewnij się, że kontrolki nie przeszkadzają mając dokumentu.  
  
 W formularzu systemu Windows.  
 -   Jeśli chcesz kontrolować rozmiar interfejsu użytkownika.  
  
-   Jeśli chcesz uniemożliwić użytkownikom ukrywanie lub usuwanie kontrolek.  
  
-   Jeśli chcesz uzyskać dane wejściowe użytkownika i uniemożliwia użytkownikowi wykonanie w dokumencie do momentu otrzymania danych wejściowych.  
  
## <a name="add-windows-forms-controls-programmatically"></a>Programowo Dodaj formanty formularzy systemu Windows  
 Formanty formularzy systemu Windows można dodać do dokumentów programu Word i Excel arkuszy w czasie wykonywania. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Udostępnia metody pomocnicze do dodawania najbardziej typowych formantów formularzy systemu Windows. Te metody pomocnicze umożliwiają szybkie dodawanie formantów do dokumentów pakietu Office i dostępu łączy funkcje formantu formularzy systemu Windows i Office związane z funkcjonalności tych kontrolek.  
  
 Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="use-windows-forms-controls-in-document-level-projects"></a>Formanty formularzy systemu Windows w projektach na poziomie dokumentu  
 Niektóre aspekty za pomocą formantów formularzy systemu Windows w dokumentach są unikatowe dla projektów na poziomie dokumentu, który umożliwia projektowanie interfejsu użytkownika dokumentu przy użyciu narzędzia Projektant Visual Studio.  
  
### <a name="create-custom-user-controls"></a>Utwórz użytkownika niestandardowego formantów  
 Można dodać kontrolkę użytkownika do projektu, a następnie dodaj go do **przybornika**. Można następnie przeciągnij formant użytkownika bezpośrednio do dokumentu w taki sam sposób, należy dodać kontrolki formularza systemu Windows do dokumentu. Istnieje kilka kwestii, które należy wziąć pod uwagę podczas tworzenia kontrolki użytkownika:  
  
-   Nie twórz **zapieczętowanego** kontrolki użytkownika. Podczas przeciągania formantu do dokumentu programu Visual Studio generuje klasy otoki pochodzącej od formant użytkownika, aby go tak rozszerzyć i obsługuje jego użycia w dokumencie. W przypadku formantu użytkownika **zapieczętowanego**, Visual Studio nie może wygenerować klasy otoki.  
  
-   Formanty użytkownika musi mieć <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawić atrybutu **true**. Formanty użytkownika utworzonego w projekcie biura zawierać ten atrybut ustawioną **true** przez domyślny, ale użytkownik formantów, które są częścią poza projektów może nie mieć ten atrybut na wartość **true**.  
  
-   Po dodaniu kontrolkę użytkownika do dokumentu, zmieniaj nazwy ani usunąć <xref:System.Windows.Forms.UserControl> klasy z projektu. Jeśli musisz zmienić nazwę formantu użytkownika musi najpierw ją usunąć z dokumentu, a następnie dodać ją ponownie po zmianie nazwy.  
  
### <a name="arrange-controls-at-design-time"></a>Rozmieszczanie formantów w czasie projektowania  
 Jeśli dodasz kilka formantów do dokumentów programu Word i Excel w czasie projektowania, można szybko ustawić wyrównanie wszystkich zaznaczonych formantów przy użyciu **Microsoft Office Word** i **Microsoft Office Excel**paski narzędzi w programie Visual Studio. Te paski narzędzi są dostępne tylko wtedy, gdy dokument lub arkusz jest otwarty w projektancie.  
  
 Po wybraniu wielu formantów w Projektancie umożliwia następujące przyciski na te paski narzędzi rozmieszczanie formantów:  
  
-   **Wyrównywanie lewych krawędzi**  
  
-   **Dopasuj centrów**  
  
-   **Dopasuj prawa**  
  
-   **Dopasuj górne**  
  
-   **Dopasuj lewych**  
  
-   **Wyrównaj do dołu**  
  
-   **Wprowadź równe odstępy w poziomie**  
  
-   **Wprowadź odstępy w pionie**  
  
> [!NOTE]  
>  W projekty programu Word tych przycisków są włączone tylko wtedy, gdy wybrane formanty nie są zgodne z tekstu. Domyślnie przez formanty dodane do dokumentu w czasie projektowania są zgodne z tekstu.  
  
### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Uniemożliwić starych danych znajdujących się w skoroszytach programu Excel w czasie ładowania  
 Po dodaniu formanty formularzy systemu Windows do dokumentów lub arkuszy w czasie projektowania formantów pozostają w dokumencie, gdy użytkownik zamyka dokument. Formanty dodane w czasie projektowania są również nazywane *formantów statycznych*.  
  
 Po otwarciu skoroszytu programu Excel, który zawiera formantów statycznych skoroszyt ma wyświetlać mapę bitową formantu w formancie ActiveX dopiero kod dostosowania ładuje rzeczywistą kontrolę. Excel tworzy tej mapy bitowej i zapisuje go w skoroszycie przy każdym zapisać skoroszyt. Mapa bitowa wyświetlanie formantu okazało się podczas ostatniego zapisu skoroszytu, łącznie z danymi, który został wyświetlanie formantu. Aby uzyskać więcej informacji na temat formantu ActiveX, który zawiera formanty formularzy systemu Windows i mapy bitowe, zobacz [formanty ograniczenia formularzy systemu Windows w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 W pewnych okolicznościach kod nie zostanie załadowany i jest wyświetlany tylko mapy bitowej, np. gdy użytkownik otwiera skoroszyt w trybie projektowania. Ponadto jeśli użytkownik otwiera skoroszytu na komputerze, który nie ma [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zainstalowana, dostosowań nie można uruchomić załadować formantów i dlatego jest widoczny tylko mapy bitowej formantu. Należy zawsze usunąć informacje osobiste z formantów na skoroszytów przed zapisaniem skoroszytu i wysyłania go do innego użytkownika, aby upewnić się, że informacje osobiste nie są przypadkowo ujawniane.  
  
### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Rozmiar formantu dopasowania do rozmiaru komórek w arkuszu programu Excel  
 Można ustawić formant zmieniany automatycznie po zmianie rozmiaru komórki nadrzędnej. Aby uzyskać więcej informacji, zobacz [porady: zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>Dodaj składniki, które są współużytkowane przez wszystkie arkusze  
 Można dodać składniki, które chcesz udostępnić wśród wszystkich arkuszy, takich jak <xref:System.Data.DataSet>, do projektanta skoroszytu, zamiast do arkuszy. Składnik będą wyświetlane na pasku składnika.  
  
### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Formuła osadzania formantów w arkuszu programu Excel  
 Po wybraniu formantu w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest i nie należy go usunąć.  
  
### <a name="layout-style-of-controls-on-a-word-document"></a>Styl układu kontrolek w dokumencie programu Word  
 Po dodaniu formantu do dokumentu programu Word w projektach na poziomie dokumentu za pomocą projektanta programu Visual Studio formant został dodany z tekstu. Aby zmienić stylu układu formantu, kliknij prawym przyciskiem myszy formantu, a następnie kliknij przycisk **Formatuj formant**. Wybierz styl zawijania na **układu** strony **Format obiektu** okno dialogowe.  
  
 Gdy formant zostanie dodany do dokumentu programu Word w czasie wykonywania, można określić styl układu nowego formantu przy użyciu różnych `Add` \< *kontrolować klasy*> Metoda przeciąża z <xref:Microsoft.Office.Tools.Word.ControlCollection> klasy:  
  
-   Aby dodać kontrolki z tekstu, użyj przeciążenia, które akceptuje <xref:Microsoft.Office.Interop.Word.Range> lokalizacji kontrolki.  
  
-   Aby dodać kontrolki jako przestawne kształtu, użyj przeciążenia, które akceptuje po lewej stronie i górna współrzędna formantu.  
  
 Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Po otwarciu szablon programu Word w Visual Studio projektanta formantów z systemem innym niż wbudowany w szablonie mogą nie być widoczne ponieważ Visual Studio otworzy w szablonie w **normalny** widoku. Aby wyświetlić formantów, należy zmienić widok, aby **układ wydruku**.  
  
### <a name="controls-outside-the-main-document-body"></a>Formanty poza ciałem głównego dokumentu  
 Formanty formularzy systemu Windows nie są obsługiwane w nagłówku lub stopce strony lub w ramach podrzędnego.  
  
### <a name="add-components-at-design-time"></a>Dodaj składniki w czasie projektowania  
 Niektóre formanty lub składniki nie są widoczne w dokumencie i zamiast tego są wyświetlane w zasobniku składnika. Program Visual Studio udostępnia zasobnik składników dla każdego okna dokumentu. Składnik na pasku zadań pojawi się na ekranie tylko wtedy, gdy istnieje składniki w dokumencie.  
  
## <a name="see-also"></a>Zobacz także  
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Formanty formularzy systemu Windows](/dotnet/framework/winforms/controls/index)   
 [Ograniczenia formantów formularzy systemu Windows w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Porady: dodawanie formantów formularzy systemu Windows do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Porady: zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Porady: ukrywanie formantów w arkuszu podczas drukowania](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Wskazówki: Zmiana formatowania arkusza za pomocą formantów CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Wskazówki: Zmiana formatowania dokumentu za pomocą formantów CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)   
 [Wskazówki: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Wskazówki: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)   
 [Ograniczenia formantów formularzy systemu Windows w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Wskazówki: Aktualizacja wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)   
 [Wskazówki: Aktualizacja wykresu w arkuszu za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  