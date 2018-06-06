---
title: Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1047d7ddd3724877aa6933f20f08df39d1e2e240
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693422"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office
  Podczas wykonywania następujących zadań, podczas opracowywania rozwiązań pakietu Office w Visual Studio, mogą wystąpić problemy:  
  
-   [Tworzenie, uaktualniania i otwierania projektów](#creating)  
  
-   [Użyj projektantów](#designers)  
  
-   [Pisanie kodu](#code)  
  
-   [Tworzenie projektów](#building)  
  
-   [Debugowanie projektów](#debugging)  
  
##  <a name="creating"></a> Tworzenie, uaktualniania i otwierania projektów  
 Mogą wystąpić następujące błędy podczas tworzenia lub otwierania projektów pakietu Office.  
  
### <a name="the-project-cannot-be-created"></a>Nie można utworzyć projektu  
 Wystąpił błąd podczas próby tworzenia lub otwierania projektu pakietu Office, ale Visual Studio nie miał wystarczających informacji do ustalenia przyczyny. Zamknij projekt zamykania programu Visual Studio, a następnie ponownie uruchomić.  
  
 Jeśli próbujesz utworzyć projektu na poziomie dokumentu, jest to możliwe, że innego dokumentu o takiej samej nazwie jak dokument w nowym projekcie jest już otwarty w programie Excel lub Word. Upewnij się, że wszystkie inne wystąpienia programu Excel lub Word są zamknięte.  
  
### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>Właściwości formantów zostaną utracone podczas tworzenia nowego projektu na podstawie dokumentu z istniejącego projektu  
 W przypadku utworzenia nowego projektu pakietu Office na podstawie dokumentu z istniejącego projektu, właściwości wszystkie formanty, które znajdują się w dokumencie nie są kopiowane do nowego projektu. Można ręcznie zresetować właściwości dla wszystkich istniejących formantów. Alternatywnie można zachować właściwości formantu, tworząc kopię istniejącego projektu zamiast tworzenia nowego projektu lub ładowania istniejący projekt do nowego rozwiązania (w Projektancie) i kopiowanie i wklejanie formantów z istniejącego dokument do nowego dokumentu.  
  
### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>Błędy podczas tworzenia projektu skoroszyt programu Excel oparte na podstawie istniejącego skoroszytu  
 W przypadku utworzenia nowego projektu skoroszyt programu Excel oparte na istniejący skoroszyt, można napotkać kombinację następujące błędy.  
  
 Z programu Excel: "Ostrzeżenie dotyczące prywatności: ten dokument zawiera makra, formantów ActiveX, informacje o pakietach rozszerzeń XML lub składniki sieci Web. Te mogą obejmować informacje osobiste, których nie można usunąć przez inspektora dokumentu."  
  
 W programie Visual Studio: "Designer nie można poprawnie załadować."  
  
 Te błędy mogą występować, spróbuj utworzyć projekt, który jest oparty na skoroszytu, który miał jego informacje osobiste, które zostały usunięte za pomocą Inspektora dokumentów. Aby uniknąć tego błędu, wykonaj następujące kroki przed utworzeniem projektu.  
  
1.  Otwórz skoroszyt w programie Excel.  
  
2.  W programie Excel otwórz Centrum zaufania.  
  
3.  Na **opcje prywatności** kartę wyczyść **Usuń informacje osobiste z właściwości pliku przy zapisywaniu** pole wyboru.  
  
4.  Zapisz skoroszyt i zamykania programu Excel.  
  
### <a name="cannot-open-a-project-after-migration"></a>Nie można otworzyć projektu po migracji  
 Po pakietu Office, które rozwiązanie migracji do programu Microsoft Office 2010 nie można otworzyć projektu na komputerze dewelopera o tylko systemu Microsoft Office 2007, które są zainstalowane. Mogą zostać wyświetlone następujące błędy.  
  
 "Co najmniej jeden projekt w rozwiązaniu nie zostały poprawnie załadowane. Zobacz okno danych wyjściowych, aby uzyskać szczegółowe informacje."  
  
 "Nie można utworzyć projektu, ponieważ aplikację skojarzoną z tym typem projektu nie jest zainstalowany na tym komputerze. Zainstalowanie aplikacji Microsoft Office, który jest skojarzony z tym typem projektu."  
  
 Aby rozwiązać ten problem, Edytuj *vbproj* lub *.csproj* pliku. Dla projektu programu Word, Zastąp HostPackage = "{763FDC83-64E5-4651-AC9B-28C4FEB985A1}" z HostPackage = "{6CE98B71-D55A-4305-87A8-0D6E368D9600}". W projekcie programu Excel, Zastąp HostPackage = "{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}" z HostPackage = "{825100CF-0BA7-47EA-A084-DCF3308DAF74}". W projekcie programu Outlook, Zastąp HostPackage = "{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}" z HostPackage = "{20A848B8-E01F-4801-962E-25DB0FF57389}".  
  
 Alternatywnie upewnij się, że zmigrowane projekty tylko są otwarte na komputerach programowanie z już zainstalowany program Microsoft Office 2010.  
  
### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Błędy w uaktualnionych projektów poziomie dokumentu pakietu Office 2003 zawierające formanty formularzy systemu Windows  
 Jeśli uaktualnić projekt poziomie dokumentu pakietu Microsoft Office 2003, a dokument zawiera formanty formularzy systemu Windows, uaktualnionym projekcie mogą zawierać błędy kompilacji lub środowisko uruchomieniowe. Aby uniknąć tego problemu, zainstaluj program Visual Studio 2005 Tools dla pakietu Office Runtime drugi w wersji na komputerze dewelopera przed rozpoczęciem uaktualniania projektu. Ta wersja środowiska wykonawczego jest dostępna jako pakiet redystrybucyjny z Microsoft Download Center na [Microsoft Visual Studio 2005 Tools for Office Runtime Edition drugi (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).  
  
 Po zakończeniu uaktualniania projektu, można odinstalować programu Visual Studio 2005 Tools for Office Runtime drugi w wersji z na komputerze deweloperskim, jeśli nie jest on używany przez innych rozwiązań pakietu Office.  
  
##  <a name="designers"></a> Użyj projektantów  
 Mogą wystąpić następujące błędy podczas pracy z dokumentu, skoroszytu lub projektanta arkusza w projektach na poziomie dokumentu.  
  
### <a name="designer-failed-to-load-correctly"></a>Nie można poprawnie załadować projektanta  
 Program Visual Studio nie może otworzyć projektanta w następujących przypadkach:  
  
-   Excel lub Word jest już otwarty i wyświetla modalne okno dialogowe. Aby otworzyć projektanta, sprawdź, czy programu Excel lub Word ma modalnego okna dialogowego otwierania i zamykania otwarte modalne okna dialogowe. Jeśli nie nie modalne okna dialogowe otwarte, może być innych działań wymagany dla programu Excel lub Word odpowiada.  
  
-   Projekt jest obecnie debugowane. Aby otworzyć projektanta, Zatrzymaj lub Zakończ debugowania.  
  
-   Dodatek VSTO programu Excel, który jest zainstalowany na komputerze dewelopera jest wyświetlane okno dialogowe po uruchomieniu programu Excel. Aby utworzyć projekt poziomie dokumentu programu Excel, należy najpierw wyłączyć dodatku VSTO.  
  
### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>Formanty są wyświetlane jako czarne prostokąty w dokumencie lub arkusz  
 Jeśli grupa formantów w dokumencie lub arkusz programu Visual Studio nie rozpoznaje już kontrolki. Nie można uzyskać dostępu do formantów zgrupowane w **właściwości** i będą wyświetlane jako czarne prostokąty w dokumencie lub arkusz. Formanty musi rozgrupować w celu przywrócenia ich funkcjonalności.  
  
### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>Formanty na szablon programu Word nie są widoczne w programie Visual Studio  
 Jeśli otworzyć szablon programu Word w projektancie programu Visual Studio, formantów w szablonie, które nie są zgodne z tekstu może nie być widoczne. Jest to spowodowane szablony programu Word w Visual Studio otworzy w **normalny** widoku. Aby wyświetlić formantów, kliknij **widoku** menu wskaż **Microsoft Office Word widoku** , a następnie kliknij przycisk **układ wydruku**.  
  
### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>Polecenie grafikę klip INSERT nie działa w projektancie programu Visual Studio  
 Gdy programu Excel lub Word jest otwarty w projektancie programu Visual Studio, klikając pozycję **grafikę klip** znajdującego się na **ilustracje** nie można otworzyć kartę na wstążce **grafikę klip** okienka zadań. Aby dodać klip grafik, należy otworzyć kopię skoroszytu lub dokument, który znajduje się w folderze głównym projektu (nie kopię, który znajduje się w *\bin* folder) poza Visual Studio, należy dodać ten element klip, a następnie zapisz skoroszyt lub dokumentu.  
  
##  <a name="code"></a> Pisanie kodu  
 Mogą wystąpić następujące błędy podczas pisania kodu w projektach pakietu Office.  
  
### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>Niektóre zdarzenia obiektów pakietu Office nie są dostępne przy użyciu języka C#  
 W niektórych przypadkach można napotkać błąd kompilatora, podobnie do następującej podczas próby uzyskania dostępu do określonego zdarzenia wystąpienia pakietu Office, typ podstawowy zestaw międzyoperacyjny (PIA) w projektach Visual C#.  
  
 "Niejednoznaczności między"Microsoft.Office.Interop.Excel._Application.NewWorkbook"i"Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook""  
  
 Ten błąd oznacza, że próbujesz uzyskać dostępu do zdarzeń, który ma taką samą nazwę jak inny właściwości lub metody obiektu. Aby uzyskać dostęp do zdarzenia, należy rzutować obiekt do jego *interfejsu zdarzenia*.  
  
 Typy PIA pakietu Office, które mają zdarzenia zaimplementować dwa interfejsy: interfejs sieci podstawowej z wszystkich właściwości i metod i interfejsu zdarzenia, który zawiera zdarzenia, które są udostępniane przez obiekt. Te interfejsy zdarzeń używać konwencji nazewnictwa *objectname*zdarzenia*n*_Event, takich jak <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> i <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event>. Jeśli nie masz dostępu do zdarzeń, które należy się spodziewać na obiekt, rzutowanie tego obiektu na jego interfejsu zdarzenia.  
  
 Na przykład <xref:Microsoft.Office.Interop.Excel.Application> obiekty mają <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> zdarzeń i <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> właściwości. Do obsługi <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> rzutowania zdarzenia <xref:Microsoft.Office.Interop.Excel.Application> do <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> interfejsu. W poniższym przykładzie pokazano, jak to zrobić w projektach na poziomie dokumentu dla programu Excel.  
  
 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]  
  
 Aby uzyskać więcej informacji na temat interfejsów zdarzeń w PIAs pakietu Office, zobacz [Przegląd klasy i interfejsy w podstawowe zestawy międzyoperacyjne pakietu Office](http://msdn.microsoft.com/en-us/da92dc3c-8209-44de-8095-a843659368d5).  
  
### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-includenetv40shortsharepointincludesnet-v40-short-mdmd-or-the-includenetv45vstoincludesnet-v45-mdmd"></a>Nie można odwołania Office PIA klas w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], domyślnie nie zostanie skompilowany kod, który odwołuje się do klasy, która jest zdefiniowana w PIA pakietu Office. Klasy w PIAs zastosować konwencję nazewnictwa *objectname*klas, takich jak <xref:Microsoft.Office.Interop.Word.DocumentClass> i <xref:Microsoft.Office.Interop.Excel.WorkbookClass>. Na przykład następujący kod z projektów dodatku VSTO programu Word nie zostanie skompilowany.  
  
```vb  
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Ten kod powoduje następujące błędy kompilacji:  
  
-   Visual Basic: "odwołanie do klasy"Klasa dokumentu"jest niedozwolone podczas jej zestaw jest połączony za pomocą trybu No-PIA."  
  
-   Visual C#: "typu międzyoperacyjnego, który nie może zostać osadzony"Microsoft.Office.Interop.Word.DocumentClass". Użyj odpowiedniego interfejsu."  
  
 Aby rozwiązać ten problem, należy zmodyfikować kod, aby odwołać zamiast tego odpowiedniego interfejsu. Na przykład zamiast odwołania <xref:Microsoft.Office.Interop.Word.DocumentClass> obiektów, odwołanie wystąpienia <xref:Microsoft.Office.Interop.Word.Document> zamiast tego interfejsu.  
  
```vb  
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 Projektów przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], automatycznie osadzić wszystkich typów międzyoperacyjnych z Office PIAs domyślnie. Ten błąd kompilacji występuje, ponieważ funkcja osadzone typy międzyoperacyjne działa tylko z interfejsami, nie klasy. Aby uzyskać więcej informacji na temat interfejsów i klasy w PIAs pakietu Office, zobacz [Przegląd klasy i interfejsy w podstawowe zestawy międzyoperacyjne pakietu Office](http://go.microsoft.com/fwlink/?LinkId=189592). Aby uzyskać więcej informacji na temat funkcji osadzone typy międzyoperacyjne w projektach pakietu Office, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="references-to-office-classes-are-not-recognized"></a>Odwołania do klasy pakietu Office nie są rozpoznawane.  
 Niektóre nazwy klasy, na przykład aplikacji, znajdują się w kilku obszarów nazw takich jak <xref:Microsoft.Office.Interop.Word> i <xref:System.Windows.Forms>. Z tego powodu **importów**/**przy użyciu** instrukcja w górnej części szablonów projektu zawiera skróconą kwalifikowanie stałą, na przykład:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]  
  
 To użycie **importów**/**przy użyciu** instrukcja wymaga rozróżnianie odwołania do klasy pakietu Office z kwalifikatorem Word czy Excel, na przykład:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]  
  
 Otrzymasz błędy, jeśli na przykład użyć deklaracji niekwalifikowanych:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]  
  
 Mimo że zaimportowano Word czy Excel przestrzeni nazw i mają dostęp do wszystkich klas w nim, należy pełnej kwalifikacji wszystkie typy z Word czy Excel, aby usunąć niejednoznaczność przestrzeni nazw.  
  
##  <a name="building"></a> Tworzenie projektów  
 Mogą wystąpić następujące błędy podczas kompilacji projektów pakietu Office.  
  
### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>Nie można utworzyć projektu poziomie dokumentu, który jest oparta na dokumentów z ograniczonymi uprawnieniami  
 Program Visual Studio nie może utworzyć projektów na poziomie dokumentu, jeśli dokument ma ograniczone uprawnienia. Jeśli projekt zawiera dokument, który ma ograniczone uprawnienia, projekt nie zostanie skompilowany i zostanie wyświetlony następujący komunikat w **listy błędów** okna.  
  
 "Nie można dodać dostosowań".  
  
 Jeśli chcesz dołączyć dokument, który ma ograniczone uprawnienia, użyj nieograniczony dokumentu, podczas tworzenia i Skompiluj rozwiązanie. Następnie należy zastosować ograniczone uprawnienia do dokumentu w lokalizacji, po opublikowaniu rozwiązania.  
  
### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>Błędy kompilatora są wykonywane po usunięciu namedrange — formant  
 Jeśli usuniesz <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu w arkuszu, który nie jest aktywny arkusz w Projektancie automatycznie wygenerowany kod nie może zostać usunięta z projektu i mogą wystąpić błędy kompilatora. Aby upewnić się, kod zostanie usunięty, należy zawsze wybierać arkusz zawierający <xref:Microsoft.Office.Tools.Excel.NamedRange> celu nadania mu aktywnego arkusza przed usunięciem formantu. Automatycznie wygenerowany kod nie zostanie usunięta po usunięciu formantu, może spowodować projektanta, aby usunąć kod aktywacji arkusza i wprowadzenie zmiany, tak aby arkusz jest oznaczony jako zmodyfikowane. Gdy zostanie ponownie skompilować projekt, kod zostanie usunięty.  
  
##  <a name="debugging"></a> Debugowanie projektów  
 Mogą wystąpić następujące błędy podczas debugowania w projektach pakietu Office.  
  
### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Podczas publikowania i zainstalować na komputerze dewelopera rozwiązanie zostanie wyświetlony monit, aby odinstalować  
 Podczas debugowania rozwiązania do pakietu Office może zostać wyświetlony następujący błąd.  
  
 "Nie można zainstalować dostosowań, ponieważ aktualnie jest zainstalowana inna wersja nie może zostać uaktualnione z tej lokalizacji."  
  
 Ten błąd wskazuje, że został wcześniej publikowane i zainstalowane na komputerze deweloperskim rozwiązań pakietu Office. Aby zapobiec wyświetlaniu komunikatu, należy odinstalować rozwiązanie z listy zainstalowanych programów na komputerze przed debugowania rozwiązania. Alternatywnie można utworzyć innego konta użytkownika na komputerze deweloperskim, aby przetestować instalację opublikowanych rozwiązania.  
  
### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>Projektów na poziomie dokumentu utworzone w lokalizacjach sieciowych UNC nie są uruchamiane w programie Visual Studio  
 Jeśli tworzysz projekt poziomie dokumentu dla programu Excel lub Word w lokalizacji sieciowej UNC, należy dodać do listy zaufanych lokalizacji w programie Excel lub Word lokalizację dokumentu. W przeciwnym razie dostosowań nie zostanie załadowany, gdy próbuje uruchomić ani debugować projektu programu Visual Studio. Aby uzyskać więcej informacji o zaufanych lokalizacji, zobacz [przyznać zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
### <a name="threads-are-not-stopped-correctly-after-debugging"></a>Wątki nie są poprawnie zatrzymane po debugowaniu  
 Projekty pakietu Office w Visual Studio wykonaj wątku nazewnictwa Konwencji, który umożliwia debugera zamknąć program poprawnie. Jeśli utworzysz wątków w rozwiązaniu powinien nazw każdy wątek z prefiksem VSTA_, aby upewnić się, że te wątki są obsługiwane poprawnie po zatrzymaniu debugowania. Na przykład można ustawić `Name` właściwości wątku, który oczekuje na zdarzenia sieci **VSTA_NetworkListener**.  
  
### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>Nie można uruchomić lub dowolnego rozwiązania do pakietu Office na komputerze dewelopera debugowania  
 Jeśli nie można uruchomić lub tworzenie projektu pakietu Office na komputerze deweloperskim, mogą pojawić się następujący komunikat o błędzie.  
  
 "Dostosowania nie można załadować, ponieważ nie można utworzyć domeny aplikacji."  
  
 Visual Studio będzie korzystać Fusion, moduł ładujący zestawu .NET Framework do pamięci podręcznej zestawów przed załadowaniem rozwiązań pakietu Office. Upewnij się, że Visual Studio można zapisać w pamięci podręcznej Fusion i spróbuj ponownie. Aby uzyskać więcej informacji, zobacz [zestawów kopii w tle](/dotnet/framework/app-domains/shadow-copy-assemblies).  
  
### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>Błąd podczas zatrzymywania debugera w projektach na poziomie dokumentu po użyciu Edytuj i Kontynuuj  
 Jeśli używasz **Edytuj** i **Kontynuuj** wprowadzania zmian kodu w projektach na poziomie dokumentu dla programu Excel lub Word, gdy projekt jest w trybie przerwania, może być wyświetlone okno dialogowe z następujący komunikat o błędzie, jeśli użytkownik następnie zatrzymać debuggera.  
  
 "Przerywa proces w bieżącym stanie może spowodować niepożądane wyniki utraty danych i niestabilność systemu."  
  
 Określa, czy kliknij **tak** lub **nr** w oknie dialogowym programu Visual Studio kończy proces programu Excel lub Word i zatrzymuje się debuger. Aby zatrzymać debugowanie projektu bez wyświetlania tego okna dialogowego, Zakończ działanie programu Excel lub Word bezpośrednio zamiast zatrzymywanie w debugerze programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązywanie problemów z rozwiązań pakietu Office](../vsto/troubleshooting-office-solutions.md)   
 [Rozwiązywanie problemów z zabezpieczeniami rozwiązań pakietu Office](../vsto/troubleshooting-office-solution-security.md)   
 [Rozwiązywanie problemów z wdrażaniem rozwiązań Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  