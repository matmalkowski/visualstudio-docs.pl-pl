---
title: Zestawy w Visual Studio Tools for Office Runtime | Dokumentacja firmy Microsoft
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
helpviewer_keywords: Visual Studio Tools for Office runtime, assemblies
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 22750553e714c0aa02577ee95753e7d5b2bf13f4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Zestawy w Visual Studio Tools dla pakietu Office Runtime
  Podczas tworzenia projektu pakietu Office, Visual Studio automatycznie dodaje odwołania do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zestawy, które są używane dla docelowej platformy .NET Framework projektu i typ projektu. Istnieją różne zestawy w rozszerzenia pakietu Office dla programu .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], i [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Aby uzyskać więcej informacji na temat rozszerzeń pakietu Office, zobacz [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenetv45vstoincludesnet-v45-mdmd"></a>Zestawy w rozszerzeniach Office programu .NET Framework 4 i[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 Poniższa tabela zawiera listę zestawów, które znajdują się w Office rozszerzenia [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Dokumentacja obszary nazw i typy w farmie znajduje się w temacie [odwołania zarządzane &#40; programowanie Office w Visual Studio &#41;](../vsto/managed-reference-office-development-in-visual-studio.md).  
  
|Nazwa zestawu|Opis|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.dll|Zapewnia następujące typy:<br /><br /> -Typów w celu utworzenia dostosowań Wstążki i tagów inteligentnych. **Uwaga:** tagi inteligentne nie są używane w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Typów w celu utworzenia okienka akcji w dostosowaniach na poziomie dokumentu i niestandardowych okienek zadań w VSTO dodatki.|  
|Microsoft.Office.Tools.Excel.dll|Udostępnia interfejsy, które reprezentują elementów hosta i formantów hosta dla projektów programu Excel i pomocnicze typy. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.dll|Zawiera typy, które umożliwiają tworzenie regionów formularzy niestandardowych w dodatkach VSTO programu Outlook.|  
|Microsoft.Office.Tools.Word.dll|Udostępnia interfejsy, które reprezentują elementów hosta i formantów hosta dla projektów programu Word i pomocnicze typy. Aby uzyskać więcej informacji, zobacz [automatyzacji programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v4.0.Framework.dll|Zapewnia następujące typy:<br /><br /> -Wyjątki, które mogą być generowane przy użyciu programu Visual Studio Tools dla pakietu Office runtime.<br />-Atrybutów używanych podczas tworzenia programu Outlook tworzą regionów.|  
|Microsoft.Office.Tools.dll|Zawiera typy, które są częścią Visual Studio Tools for Office runtime infrastruktury, a nie są przeznaczone do użycia bezpośrednio w kodzie.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Zapewnia następujące typy:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Atrybutu i <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interfejsu, które służy do buforowania danych obiektów w dostosowaniu poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [buforowanie danych](../vsto/caching-data.md).<br />- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Interfejs, który można zaimplementować w celu uruchomienia dodatkowych kroków instalacji ostatni krok Instalator ClickOnce dla rozwiązań pakietu Office. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office za pomocą technologii ClickOnce za pomocą](../vsto/deploying-an-office-solution-by-using-clickonce.md).<br />-Wyjątki, które mogą być generowane przy użyciu programu Visual Studio Tools dla pakietu Office runtime.<br />-Innych typów, które są częścią Visual Studio Tools for Office runtime infrastruktury, a nie są przeznaczone do użycia bezpośrednio w kodzie.|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Zapewnia następujące typy:<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasy, która służy do podłączenia zestawy dostosowania do dokumentów i dostęp do pamięci podręcznej danych w dokumentach. Aby uzyskać więcej informacji, zobacz [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Kilka klas, które reprezentują hierarchii buforowane dane w dostosowaniu poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).|  
  
 Projektów przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] również odwołuje się do następujących zestawów. Te zestawy nie są częścią [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do dystrybucji. Zamiast tego są one zależne zestawy, które należy wdrożyć wraz z rozwiązaniem. Domyślnie są kopiowane do folderu wyjściowego kompilacji projektu ( **Kopiuj lokalnie** ustawiono właściwość dla tych zestawów **True**). W przypadku wdrożenia projektu przy użyciu technologii ClickOnce, te zestawy są objęte wygenerowany pakiet.  
  
|Nazwa zestawu|Opis|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Udostępnia podstawowe klasy dla wygenerowanej `ThisAddIn` klasy w dodatku VSTO projektów i wygenerowana klasa wstążki we wszystkich projektach.|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Zapewnia następujące typy:<br /><br /> -Podstawowa klasy dla wygenerowanej `ThisWorkbook` i `Sheet` klas w poziomie dokumentu projektów dla programu Excel.<br />-Formanty formularzy systemu Windows używanych w arkuszach w projekty programu Excel.|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Udostępnia klasy podstawowej dla wygenerowanej `ThisAddIn` i tworzą klasy regionu w projektach programu Outlook.|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Zapewnia następujące typy:<br /><br /> -Podstawowa klasy dla wygenerowanej `ThisDocument` klasy w projektów na poziomie dokumentu dla programu Word.<br />-Formanty formularzy systemu Windows używanych w dokumentach w projekty programu Word.|  
  
## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Zestawy w rozszerzenia pakietu Office dla programu .NET Framework 3.5  
 Poniższa tabela zawiera listę zestawów, które znajdują się w Office rozszerzeń dla programu .NET Framework 3.5. Dokumentacja obszary nazw i klasy w farmie, zobacz następującą sekcję informacyjną w dokumentacji programu Visual Studio 2008: [http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
|Nazwa zestawu|Opis|  
|-------------------|-----------------|  
|Microsoft.Office.Tools.Common.v9.0.dll|Zapewnia następujące typy:<br /><br /> -Microsoft.Office.Tools.AddIn klasę podstawową dla VSTO dodatki.<br />-Klasy służące do tworzenia dostosowań Wstążki i tagów inteligentnych. **Uwaga:** tagi inteligentne nie są używane w [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] i [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].<br />-Klasy służące do tworzenia okienka akcji w dostosowaniach na poziomie dokumentu i niestandardowych okienek zadań w VSTO dodatki.|  
|Microsoft.Office.Tools.Excel.v9.0.dll|Udostępnia elementów hosta i formantów hosta dla rozwiązania programu Excel. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|Udostępnia klasy, które umożliwiają tworzenie regionów formularzy niestandardowych w dodatkach VSTO programu Outlook.|  
|Microsoft.Office.Tools.Word.v9.0.dll|Udostępnia elementów hosta i formantów hosta dla rozwiązania programu Word. Aby uzyskać więcej informacji, zobacz [automatyzacji programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md).|  
|Microsoft.Office.Tools.v9.0.dll|Zapewnia następujące typy:<br /><br /> -Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent klasy, która zapewnia możliwości wiązania danych kontrolki hosta w dostosowaniach na poziomie dokumentu.<br />-Innych typów, które są częścią Visual Studio Tools for Office runtime infrastruktury, a nie są przeznaczone do użycia bezpośrednio w kodzie.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Zapewnia następujące typy:<br /><br /> — Ten atrybut Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute i Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType interfejsu, które służy do buforowania danych obiektów w dostosowaniu poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [buforowanie danych](../vsto/caching-data.md).<br />-Wyjątki, które mogą być generowane przy użyciu programu Visual Studio Tools dla pakietu Office runtime.<br />-Innych typów, które są częścią Visual Studio Tools for Office runtime infrastruktury, a nie są przeznaczone do użycia bezpośrednio w kodzie.|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Udostępnia interfejs Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction, które można zaimplementować w celu uruchomienia dodatkowych kroków instalacji ostatni krok Instalator ClickOnce dla rozwiązań pakietu Office. Aby uzyskać więcej informacji, zobacz [zaawansowanego wdrażania rozwiązania pakietu Office](http://msdn.microsoft.com/en-us/9147b6f6-849f-4cb1-b2c5-e22658d74b02).|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Zapewnia następujące typy:<br /><br /> -Microsoft.VisualStudio.Tools.Applications.ServerDocument klasy, która służy do programowane dołączanie zestawy dostosowania do dokumentów i dostęp do pamięci podręcznej danych w dokumentach. Aby uzyskać więcej informacji, zobacz [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Kilka klas, które reprezentują hierarchii buforowane dane w dostosowaniu poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Zapewnia następujące typy:<br /><br /> -Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry i Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList klasy, których można użyć do utworzenia użytkownika włączenia pozycje listy udzielenia zaufania do urzędu rozwiązania, które odnoszą się do programu .NET Framework 3.5.<br />-Innych typów, które są częścią Visual Studio Tools for Office runtime infrastruktury, a nie są przeznaczone do użycia bezpośrednio w kodzie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools dla pakietu Office Runtime — scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  