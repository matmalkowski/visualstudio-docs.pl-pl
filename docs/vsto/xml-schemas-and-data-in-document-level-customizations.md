---
title: Schematy XML i danych na poziomie dokumentu | Dokumentacja firmy Microsoft
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
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b3f55c8c6b2975e8dbaa85177fddcadaf62e000e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Schematy XML i dane dostosowywane na poziomie dokumentu
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest przedstawioną wyłącznie do korzyści i użyj osób i organizacji, które znajdują się poza Stanami Zjednoczonymi i jego terytoriów lub używający lub tworzenie programy, które działają na, produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy plik XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word może nie być odczytywane lub używane przez osoby lub organizacji w Stanach Zjednoczonych lub w jego terytoriów użytkowników przy użyciu lub tworzenie programów uruchamianych na produktów Microsoft Word, które są licencjonowane przez firmę Microsoft po 10 stycznia 2010 ; te produkty nie będzie działać taka sama jak produktów licencjonowanych przed tą datą lub zakupione i licencję na korzystanie z niego poza Stanami Zjednoczonymi.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Program Microsoft Office Excel i Microsoft Office Word umożliwia mapowanie schematów z dokumentów. Ta funkcja może uprościć importowanie i eksportowanie danych XML do i z dokumentu.  
  
 Visual Studio udostępnia zamapowane elementy schematu w dostosowaniach na poziomie dokumentu jako formanty w modelu programowania. Dla programu Excel programu Visual Studio dodaje obsługę powiązywanie kontrolek z danymi w bazach danych, usługi sieci Web i obiektów. Dla programu Word i Excel Visual Studio dodaje obsługę okienka akcji, które mogą być używane z dokumentem mapowane schematu można utworzyć środowisko rozszerzone użytkownika końcowego dla rozwiązań. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  Nie można użyć wieloczęściowego schematów XML rozwiązania programu Excel.  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Obiekty utworzone podczas schematy są dołączone do skoroszytów programu Excel  
 Po dołączeniu schematu do skoroszytu programu Visual Studio automatycznie tworzy obiekty i dodaje je do projektu. Te obiekty nie powinny być usuwane za pomocą narzędzi Visual Studio, ponieważ są one zarządzane przez program Microsoft Excel. Aby usunąć je, Usuń zamapowane elementy z arkusza lub odłączyć schematu za pomocą narzędzi programu Excel.  
  
 Istnieją dwa obiekty główne:  
  
-   Schemat XML (plik XSD). Dla każdego schematu w skoroszycie programu Visual Studio dodaje schematu do projektu. Pojawia się jako element projektu z rozszerzeniem XSD w **Eksploratora rozwiązań**.  
  
-   Typizowany <xref:System.Data.DataSet> klasy. Ta klasa jest tworzona w oparciu o schemacie. Ta klasa zestawu danych jest widoczny w **widoku klasy**.  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Obiekty utworzone podczas elementy schematu są mapowane na arkusze programu Excel  
 Podczas mapowania elementu schematu z **źródło XML** okienka zadań do arkusza programu Visual Studio automatycznie tworzy obiekty i dodaje je do projektu:  
  
-   Formanty. Dla każdego mapowanego obiektu w skoroszycie <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontroli (dla elementów schematu niepowtarzającymi) lub <xref:Microsoft.Office.Tools.Excel.ListObject> sterowania (do powtarzania elementy schematu) jest tworzony w modelu programowania. <xref:Microsoft.Office.Tools.Excel.ListObject> Formantu można usunąć tylko przez usunięcie mapowania i mapowanych obiektów ze skoroszytu. Aby uzyskać więcej informacji na temat formantów, zobacz [elementów hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md).  
  
-   Źródło BindingSource. Po utworzeniu <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> przez mapowanie elementu schematu niepowtarzającymi w arkuszu <xref:System.Windows.Forms.BindingSource> jest tworzony i <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>. Należy powiązać <xref:System.Windows.Forms.BindingSource> do wystąpienia źródła danych zgodny schemat zamapowane do dokumentu, takie jak wystąpienia typu <xref:System.Data.DataSet> klasy, która została utworzona. Utwórz powiązanie przez ustawienie <xref:System.Windows.Forms.BindingSource.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości, które są widoczne w **właściwości** okna.  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource> Nie został utworzony dla <xref:Microsoft.Office.Tools.Excel.ListObject> obiektów. Należy ręcznie powiązać <xref:Microsoft.Office.Tools.Excel.ListObject> ze źródłem danych, ustawiając <xref:System.Windows.Forms.BindingSource.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości w **właściwości** okna.  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office mapowane schematy i okna źródeł danych programu Visual Studio  
 Funkcji mapowanej schematu pakietu Office i programu Visual Studio **źródeł danych** okna może pomóc w przedstawiać dane w arkuszu programu Excel, raportowanie i edytowania. W obu przypadkach można przeciągnij elementy danych na arkuszu programu Excel. Obie metody tworzenia formantów, które są danymi powiązanymi za pośrednictwem <xref:System.Windows.Forms.BindingSource> ze źródłem danych, takich jak <xref:System.Data.DataSet> lub usługi sieci Web.  
  
> [!NOTE]  
>  Podczas mapowania powtarzający się element schematu do arkusza, program Visual Studio tworzy <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Automatycznie nie jest powiązany z danymi za pomocą <xref:System.Windows.Forms.BindingSource>. Należy ręcznie powiązać <xref:Microsoft.Office.Tools.Excel.ListObject> ze źródłem danych, ustawiając <xref:System.Windows.Forms.BindingSource.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości w **właściwości** okna.  
  
 W poniższej tabeli przedstawiono niektóre różnice między obiema metodami.  
  
|Schemat XML|Data Sources — Okno|  
|----------------|-------------------------|  
|Używa interfejsu pakietu Office.|Używa **źródeł danych** okna w programie Visual Studio.|  
|Włącza wbudowane funkcje pakietu Office do importowania i eksportowania danych z plików XML.|Musi Podaj importowanie i eksportowanie funkcji programowo.|  
|Należy napisać kod do wypełnienia wygenerowanego kontrolek z danymi.|Formanty dodawane z **źródeł danych** okno ma kod wygenerowany automatycznie, aby wypełnić je, oraz parametry połączenia niezbędne podczas korzystania z serwerów bazy danych.|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Zachowanie, gdy schematy są dołączone do dokumentów programu Word  
 Obiekty danych nie są tworzone po dołączeniu schematu do dokumentu programu Word, który jest używany w projektach na poziomie dokumentu pakietu Office. Jednak podczas mapowania elementu schematu do dokumentu, formanty są tworzone. Typ formantu zależy od rodzaju elementu mapy; powtarzające się elementy generują <xref:Microsoft.Office.Tools.Word.XMLNodes> kontrolek i elementy niepowtarzającymi Generowanie <xref:Microsoft.Office.Tools.Word.XMLNode> kontrolki. Aby uzyskać więcej informacji, zobacz [formant XMLNodes](../vsto/xmlnodes-control.md) i [formant XMLNode](../vsto/xmlnode-control.md).  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Wdrażanie rozwiązań, które obejmują schematy XML  
 Należy utworzyć Instalatora w celu wdrożenia rozwiązania, który korzysta ze schematu XML, który jest zamapowany do dokumentu. Instalator należy zarejestrować schematu w bibliotece schematu na komputerze użytkownika. Jeśli nie zarejestrujesz schematu rozwiązania będą nadal działać, ponieważ program Word generuje tymczasowego schematu oparte na elementach, które są w dokumencie, gdy użytkownik otwiera go. Jednak użytkownik nie będzie mógł wykonywać sprawdzanie poprawności względem lub zapisać schemat, który został użyty do utworzenia projektu. Aby uzyskać więcej informacji na temat instalatorów, zobacz [wdrażanie aplikacji, usług i składników](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 Można również dodać kod do projektu, aby sprawdzić, czy schemat jest w bibliotece i zarejestrowany. Jeśli nie jest dostępne, można ostrzeżenia dla użytkownika.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: mapowanie schematów z dokumentami programu Word w Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Instrukcje: Mapowanie schematów z arkuszami w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  