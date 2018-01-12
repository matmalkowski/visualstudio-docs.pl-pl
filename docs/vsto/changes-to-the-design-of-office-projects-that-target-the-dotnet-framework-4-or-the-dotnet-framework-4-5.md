---
title: "Zmiany w projekcie projektów pakietu Office, które odnoszą się do programu .NET Framework 4 lub .NET Framework 4.5 | Dokumentacja firmy Microsoft"
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
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 059d259b669e63c26759782010be7ff78691ffc3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Zmiany w projektach związanych z pakietem Office tworzonych pod kątem oprogramowania .NET Framework w wersji 4 lub 4.5
  Począwszy od [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], Visual Studio wprowadzono pewne zmiany do projektu projektów pakietu Office przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. Jeśli znasz projektów pakietu Office w poprzednich wersjach programu Visual Studio, należy pamiętać o tych zmianach przed opracowanie projektach pakietu Office przeznaczonych te wersje programu .NET Framework 4.0 lub nowszy. Domyślnie wszystkie projekty, które są tworzone przy użyciu programu Visual Studio 2013 lub nowszy dla środowiska .NET Framework 4.0 lub nowszy.  
  
 W poniższych sekcjach opisano te zmiany projektu projektu pakietu Office.  
  
## <a name="understanding-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Opis interfejsu na podstawie projektu Visual Studio 2010 Tools for Office Runtime  
 Podczas opracowywania projektu pakietu Office, którego celem jest [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, większość typów używanych w Visual Studio 2010 Tools for Office Runtime interfejsów. Jest to istotne zmiany z poprzednich wersji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], których te typy są klasy. Na przykład, jeśli zostanie rozpoczęta [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, <xref:Microsoft.Office.Tools.Excel.Worksheet> i <xref:Microsoft.Office.Tools.Word.Document> typy są interfejsy zamiast klasy. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
 Dla wszystkich typów, które można wystąpienia bezpośrednio w poprzednich wersjach [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], teraz używać metody obiektu Globals.Factory można uzyskać wystąpień tych typów. Na przykład, aby pobrać obiekt, który implementuje <xref:Microsoft.Office.Tools.Excel.SmartTag> interfejsu, należy użyć metody Globals.Factory.CreateSmartTag. Więcej informacji znajduje się w następujących tematach:  
  
-   [Aktualizowanie programu Excel i Word projektów, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualizowanie dostosowań Wstążki w projektach pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualizowanie regionów formularzy w projektach programu Outlook, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Nowe klasy podstawowej w projektach pakietu Office  
 Nowy projekt oparty na Visual Studio 2010 Tools for Office Runtime ma wpływ na wygenerowane klasy w projektach pakietu Office, takich jak `ThisDocument`, `ThisWorkbook`, i `ThisAddIn`. W projektach pakietu Office przeznaczonych dla platformy .NET Framework 3.5 i poprzednie wersje platformy, te wygenerowane klasy pochodzi od klasy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] takich jak Microsoft.Office.Tools.Word.Document, Microsoft.Office.Tools.Excel.Worksheet, i Microsoft.Office.Tools.AddIn. W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] klas są teraz interfejsów. W związku z tym wygenerowane klasy w projektach pakietu Office nie mogą dziedziczyć ich realizacji z nich. Zamiast tego wygenerowane klasy pochodzi od nowych klas podstawowych takich jak <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>, i <xref:Microsoft.Office.Tools.AddInBase>. Aby uzyskać więcej informacji, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md) i [programowania dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md).  
  
 Klasy podstawowe nie są częścią [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do dystrybucji. Zamiast tego są definiowane w zestawach narzędzia, które są dołączone do programu Visual Studio. Te zestawy są kopiowane do folderu wyjściowego podczas kompilacji w projektach pakietu Office i muszą być wdrażane z rozwiązania. Aby uzyskać więcej informacji na temat zestawów narzędzia, zobacz [zestawy w Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Fundamentalne zmiany w projektach pakietu Office, które są przekierować programu .NET Framework 4  
 W poniższej tabeli wymieniono zmiany głównego podziału, może wystąpić w projektach pakietu Office, które są przekierować do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. Aby uzyskać szczegółowe informacje, zobacz [Migrowanie rozwiązań pakietu Office do programu .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
|Fundamentalne zmiany|Konsekwencją|  
|---------------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute> Nie jest już używana lub jest on obsługiwany w projektach pakietu Office.|Należy usunąć ten atrybut z pliku AssemblyInfo kodu w projektach pakietu Office, które w przypadku uaktualniania z programu Visual Studio 2008. Aby uzyskać więcej informacji, zobacz [zmiany wymagane do uruchomienia projektów pakietu Office migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|ExcelLocale1033Attribute jest już używane lub obsługiwany w projektach programu Excel.|Należy usunąć ten atrybut z pliku AssemblyInfo kodu w projektach programu Excel. Aby uzyskać więcej informacji, zobacz [aktualizowanie programu Excel i Word projekty, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Model programowania **wstążki (projektanta wizualnego)** — elementy projektu została zmieniona.|Należy zmodyfikować plik CodeBehind dla wszystkich elementów wstążki do projektu. Musisz także zmodyfikować kodu, który tworzy formantów wstążki w czasie wykonywania, obsługuje zdarzenia Wstążki lub programowo Ustawia położenie składnika wstążki. Aby uzyskać więcej informacji, zobacz [aktualizowanie dostosowań Wstążki w pakiecie Office projektów tej migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Model programowania regionów formularzy programu Outlook został zmieniony.|Należy zmodyfikować plik CodeBehind dla dowolnego regionów formularzy w projekcie kodu, który tworzy niektórych klas regionu formularza w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [aktualizowanie regionów formularzy w programie Outlook projektów tej migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Model programowania tagów inteligentnych w programie Excel i Word projektach została zmieniona. Tagi inteligentne nie są używane w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Jeśli rozwiązanie korzysta z tagami inteligentnymi, będzie wystąpić błędy podczas kompilowania projektu. Ponieważ tagi inteligentne nie są używane w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], należy usunąć tagi, aby umożliwić testowanie i debugowanie rozwiązania w [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] lub nowszej.|  
|Składnia metody GetVstoObject i HasVstoObject została zmieniona.|Obiekt Globals.Factory musi przejść do tych metod dostępu na obiektów macierzystych z podstawowe zestawy międzyoperacyjne (PIAs) lub można uzyskać dostępu do tych metod dla obiektu, który jest zwracany za pomocą właściwości Globals.Factory w projekcie. Aby uzyskać więcej informacji, zobacz [aktualizowanie programu Excel i Word projekty, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Zdarzenia Word formanty zawartości są skojarzone z nowych delegatów.|Należy zmodyfikować każdy kod obsługujący zdarzenia Word formantów zawartości do określenia nowych delegatów. Aby uzyskać więcej informacji, zobacz [aktualizowanie programu Excel i Word projekty, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Nazwa klasy OLEObject i OLEControl została zmieniona.|Należy zmodyfikować kodu, który używa wystąpieniami tych klas, aby użyć <xref:Microsoft.Office.Tools.Excel.ControlSite> lub <xref:Microsoft.Office.Tools.Word.ControlSite> zamiast obiektów. Aby uzyskać więcej informacji, zobacz [aktualizowanie programu Excel i Word projekty, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Host klasy elementów, takich jak `ThisWorkbook`, `Sheet`  *n* , `ThisDocument`, i `ThisAddIn`, nie zapewniają już metodę Dispose, którą można zastąpić.|Należy przenieść cały kod w zastąpienie metody Dispose obsługi zdarzeń zamknięcia systemu w klasie elementu hosta, na przykład `ThisAddIn_Shutdown`i Usuń zastąpienie metody Dispose z klasy elementu host.|  
  
## <a name="see-also"></a>Zobacz też  
 [Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [What's New in programowanie Office](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Visual Studio Tools dla pakietu Office Runtime — przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  