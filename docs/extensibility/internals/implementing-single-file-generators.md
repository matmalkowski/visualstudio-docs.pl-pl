---
title: "Wdrażanie pojedynczego pliku generatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b9fed2f4118600c48ad6cb769c8e697b06ae77d1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-single-file-generators"></a>Implementowanie generatory pojedynczego pliku
Niestandardowe narzędzie — czasami określane jako generatora pojedynczych plików — umożliwiają rozszerzanie [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu systemów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Niestandardowe narzędzie jest składnik modelu COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejsu. Przy użyciu tego interfejsu, niestandardowe narzędzie przekształca pojedynczego pliku wejściowego w pojedynczym wyjściowym pliku. Wynik transformacji może być kodu źródłowego lub innych danych wyjściowych przydatne. Dwa przykłady kod wygenerowany przez narzędzie niestandardowe pliki są kod wygenerowany w odpowiedzi na zmiany w wizualnego projektanta i pliki generowane przy użyciu usługi sieci Web Services Description Language (WSDL).  
  
 Po załadowaniu niestandardowego narzędzia lub zapisaniu pliku wejściowego, system projektu wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metody i odwołuje się do <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interfejs wywołania zwrotnego, zgodnie z którymi narzędzia można raportowania postępu dla użytkownika.  
  
 Plik wyjściowy generowany przez niestandardowe narzędzie jest dodane do projektu z zależnością pliku wejściowego. System projektu automatycznie określa nazwę pliku wyjściowego, oparte na długość ciągu zwróconego przez niestandardowe narzędzie wdrożenia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Niestandardowe narzędzie musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfejsu. Opcjonalnie, narzędzia niestandardowe obsługuje <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interfejsu, aby pobrać informacje ze źródeł innych niż pliku wejściowego. W każdym przypadku przed użyciem narzędzia niestandardowego, musi być zarejestrowany w systemie lub w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lokalnego rejestru. Aby uzyskać więcej informacji o rejestrowaniu narzędzi niestandardowych, zobacz [rejestrowanie generatory pojedynczy plik](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie typów dla projektantów wizualnych](../../extensibility/internals/exposing-types-to-visual-designers.md)