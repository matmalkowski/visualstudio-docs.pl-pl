---
title: Zmienia się na projekt projektów pakietu Office przeznaczonych programu .NET Framework
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, what's new
- what's new [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 84a755d420da494f77397dbad445b7a649f0c943
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Zmiany w projekcie projektów pakietu Office przeznaczonych dla platformy .NET Framework 4 lub .NET Framework 4.5
  Począwszy od [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], Visual Studio wprowadzono pewne zmiany do projektu projektów pakietu Office przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. Jeśli znasz projektów pakietu Office w poprzednich wersjach programu Visual Studio, należy pamiętać o tych zmianach przed opracowanie projektach pakietu Office przeznaczonych te wersje programu .NET Framework 4.0 lub nowszy. Domyślnie wszystkie projekty, które są tworzone przy użyciu programu Visual Studio 2013 lub nowszy dla środowiska .NET Framework 4.0 lub nowszy.  
  
 W poniższych sekcjach opisano te zmiany projektu projektu pakietu Office.  
  
## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Zrozumienie oparty na projekt programu Visual Studio 2010 Tools dla pakietu Office runtime  
 Podczas opracowywania projektu pakietu Office, którego celem jest [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, większość typów używanych w Visual Studio 2010 Tools dla pakietu Office runtime interfejsów. Jest to istotne zmiany z poprzednich wersji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], których te typy są klasy. Na przykład, jeśli zostanie rozpoczęta [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, <xref:Microsoft.Office.Tools.Excel.Worksheet> i <xref:Microsoft.Office.Tools.Word.Document> typy są interfejsy zamiast klasy. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
 Dla wszystkich typów, które można wystąpienia bezpośrednio w poprzednich wersjach [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], możesz teraz użyć metod `Globals.Factory` obiektu można uzyskać wystąpień tych typów. Na przykład, aby pobrać obiekt, który implementuje <xref:Microsoft.Office.Tools.Excel.SmartTag> interfejsu, użyj `Globals.Factory.CreateSmartTag` metody. Więcej informacji znajduje się w następujących tematach:  
  
-   [Aktualizacja programu Excel i Word projektów, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualizowanie dostosowań Wstążki w projektach pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualizowanie regionów formularzy w projektach programu Outlook, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### <a name="new-base-classes-in-office-projects"></a>Nowe klasy podstawowej w projektach pakietu Office  
 Nowy projekt oparty na Visual Studio 2010 Tools dla pakietu Office runtime ma wpływ na wygenerowane klasy w projektach pakietu Office, takich jak `ThisDocument`, `ThisWorkbook`, i `ThisAddIn`. W projektach pakietu Office przeznaczonych dla platformy .NET Framework 3.5 i poprzednie wersje platformy, te wygenerowane klasy pochodzi od klasy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] takich jak `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet`, i `Microsoft.Office.Tools.AddIn`. W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] klas są teraz interfejsów. W związku z tym wygenerowane klasy w projektach pakietu Office nie mogą dziedziczyć ich realizacji z nich. Zamiast tego wygenerowane klasy pochodzi od nowych klas podstawowych takich jak <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>, i <xref:Microsoft.Office.Tools.AddInBase>. Aby uzyskać więcej informacji, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md) i [programowania dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md).  
  
 Klasy podstawowe nie są częścią [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do dystrybucji. Zamiast tego są definiowane w zestawach narzędzia, które są dołączone do programu Visual Studio. Te zestawy są kopiowane do folderu wyjściowego podczas kompilacji w projektach pakietu Office i muszą być wdrażane z rozwiązania. Aby uzyskać więcej informacji na temat zestawów narzędzia, zobacz [zestawy w Visual Studio Tools for Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Fundamentalne zmiany w projektach pakietu Office, które są przekierować do programu .NET Framework 4  
 W poniższej tabeli wymieniono zmiany głównego podziału, może wystąpić w projektach pakietu Office, które są przekierować do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. Aby uzyskać szczegółowe informacje, zobacz [rozwiązań Office migracji do programu .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
|Fundamentalne zmiany|Konsekwencją|  
|---------------------|-----------------|  
|<xref:System.Security.SecurityTransparentAttribute> Nie jest już używana lub jest on obsługiwany w projektach pakietu Office.|Należy usunąć ten atrybut z pliku AssemblyInfo kodu w projektach pakietu Office, które w przypadku uaktualniania z programu Visual Studio 2008. Aby uzyskać więcej informacji, zobacz [wymagane zmiany w celu uruchamiania projektów pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|**ExcelLocale1033Attribute** nie jest już używana lub jest on obsługiwany w projektach programu Excel.|Należy usunąć ten atrybut z *AssemblyInfo* pliku kodu w projektach programu Excel. Aby uzyskać więcej informacji, zobacz [aktualizacji programu Excel i Word projektów, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Model programowania **wstążki (projektanta wizualnego)** — elementy projektu została zmieniona.|Należy zmodyfikować plik CodeBehind dla wszystkich elementów wstążki do projektu. Musisz także zmodyfikować kodu, który tworzy formantów wstążki w czasie wykonywania, obsługuje zdarzenia Wstążki lub programowo Ustawia położenie składnika wstążki. Aby uzyskać więcej informacji, zobacz [dostosowań aktualizacji wstążki w projektach pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Model programowania regionów formularzy programu Outlook został zmieniony.|Należy zmodyfikować plik CodeBehind dla dowolnego regionów formularzy w projekcie kodu, który tworzy niektórych klas regionu formularza w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [aktualizowanie regionów formularzy w projektach programu Outlook, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Model programowania tagów inteligentnych w programie Excel i Word projektach została zmieniona. Tagi inteligentne nie są używane w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Jeśli rozwiązanie korzysta z tagami inteligentnymi, będzie wystąpić błędy podczas kompilowania projektu. Ponieważ tagi inteligentne nie są używane w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)], należy usunąć tagi, aby umożliwić testowanie i debugowanie rozwiązania w [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] lub nowszej.|  
|Składnia `GetVstoObject` i `HasVstoObject` metody została zmieniona.|Należy podać `Globals.Factory` obiektu do tych metod dostępu w macierzystym obiektów z podstawowe zestawy międzyoperacyjne (PIAs) lub można uzyskać dostępu do tych metod dla obiektu, który jest zwracany przez `Globals.Factory` właściwości projektu. Aby uzyskać więcej informacji, zobacz [aktualizacji programu Excel i Word projektów, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Zdarzenia Word formanty zawartości są skojarzone z nowych delegatów.|Należy zmodyfikować każdy kod obsługujący zdarzenia Word formantów zawartości do określenia nowych delegatów. Aby uzyskać więcej informacji, zobacz [aktualizacji programu Excel i Word projektów, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|`OLEObject` i `OLEControl` klasy została zmieniona.|Należy zmodyfikować kodu, który używa wystąpieniami tych klas, aby użyć <xref:Microsoft.Office.Tools.Excel.ControlSite> lub <xref:Microsoft.Office.Tools.Word.ControlSite> zamiast obiektów. Aby uzyskać więcej informacji, zobacz [aktualizacji programu Excel i Word projektów, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|  
|Host klasy elementów, takich jak `ThisWorkbook`, `Sheet` *n*, `ThisDocument`, i `ThisAddIn`, nie zapewniają już `Dispose` — metoda, którą można zastąpić.|Musisz przenieść cały kod z `Dispose` zastąpienie metody `Shutdown` obsługi zdarzeń w klasie elementu hosta, na przykład `ThisAddIn_Shutdown`i Usuń `Dispose` metoda przesłania z klasy elementu host.|  
  
## <a name="see-also"></a>Zobacz także  
 [Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [What's new in programowanie Office](http://msdn.microsoft.com/en-us/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Visual Studio Tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  