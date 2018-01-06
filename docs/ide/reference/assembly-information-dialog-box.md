---
title: "Informacje o zestawie — okno dialogowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords: Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: febf90633994dd825bd6ce84de8ecdc97d469e84
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-information-dialog-box"></a>Informacje o zestawie — Okno dialogowe
**Informacji o zestawie** okno dialogowe służy do określania wartości [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] GAC atrybuty, które są przechowywane w pliku AssemblyInfo tworzone automatycznie w projekcie. W **Eksploratora rozwiązań**, plik znajduje się w **mój projekt** w węźle [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (kliknij **Pokaż wszystkie pliki** aby go wyświetlić); znajduje się w obszarze  **Właściwości** w [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Aby uzyskać więcej informacji na temat atrybutów zestawu, zobacz [atrybutów](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).  
  
 Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Gdy **projektanta projektu** zostanie wyświetlony, kliknij przycisk **aplikacji** kartę. Na **aplikacji** kliknij przycisk **informacji o zestawie** przycisku.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Tytuł**  
 Określa tytuł dla manifest zestawu. Odpowiada <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Opis**  
 Określa opcjonalny opis dla manifest zestawu. Odpowiada <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Firmy**  
 Określa nazwę firmy dla manifest zestawu. Odpowiada <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Produktu**  
 Określa nazwę produktu dla manifest zestawu. Odpowiada <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Prawa autorskie**  
 Określa informacje o prawach autorskich dla manifest zestawu. Odpowiada <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Znak towarowy**  
 Określa znak towarowy dla manifest zestawu. Odpowiada <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Wersja zestawu**  
 Określa numer wersji zestawu. Odpowiada <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Wersja pliku**  
 Określa numer wersji, który nakazuje kompilatorowi używanie określonej wersji dla zasobu wersji pliku Win32. Odpowiada <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **IDENTYFIKATOR GUID**  
 Unikatowy identyfikator GUID, który identyfikuje zestaw. Podczas tworzenia projektu Visual Studio generuje identyfikator GUID dla zestawu. Odpowiada <xref:System.Guid>.  
  
 **Niezależnym od języka.**  
 Określa, które kultury obsługuje zestawu. Odpowiada <xref:System.Resources.NeutralResourcesLanguageAttribute>. Wartość domyślna to **(Brak)**.  
  
 **Wprowadź zestawu widoczny dla modelu COM**  
 Określa, czy typów w zestawie będzie dostępny do modelu COM. Odpowiada <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona aplikacji, Projektant projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Atrybuty](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)