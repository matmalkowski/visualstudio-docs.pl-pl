---
title: Różne pliki projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a637b37590a0aaf321a4e04896b2cbe12c29691f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129980"
---
# <a name="miscellaneous-files-project"></a>Projekt różne pliki
Po otwarciu elementy projektu IDE przypisuje do projektu różne pliki wszystkie elementy, które nie są elementami członkowskimi żadnych projektów w rozwiązaniu.  
  
 Projekty odtworzyć istotną rolę w określeniu, edytor, którego jest używany, gdy użytkownik otwiera element projektu. Projekt może być zaprojektowana do otwierania niektórych plików za pomocą edytora określonego projektu lub standardowego edytora.  
  
 Edytor specyficznego dla projektu wymaga zwykle użytkownik znają specjalnych lub używać specjalnych interfejsów z projektu. Aby uzyskać więcej informacji, zobacz [porady: Otwórz edytory specyficznego dla projektu](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Standardowy edytor może otwierania plików z określonym rozszerzeniem w żadnym projekcie. Użytkownik może dostosować niektóre standardowe edytory, takich jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Edytor tekstu, dla projektów ale zachować ich publicznego znaków. Standardowe edytory są tworzone za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody.  
  
 Jeśli żaden projekt w rozwiązaniu odpowiada, że można otworzyć elementu projektu, IDE zapewnia projektu o nazwie projektu różne pliki, który otwiera dowolnego pliku.  
  
 Ten projekt specjalne udostępnia otwierania pliku poza kontekstem projektu. Podczas przetwarzania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metody projekcie plików pozostałych zawsze odpowiada z bardzo niskim priorytetem. W związku z tym zawsze wydajności do każdego projektu o wyższym priorytecie, które można otwierać plików projektu różne pliki.  
  
 Projekt różne pliki wymaga od użytkownika można jawnie utworzyć za pomocą **nowy projekt** okno dialogowe. Ponadto projekcie plików pozostałych nie zarządza trwale listę elementów projektu. Opcjonalna funkcja używa Aby zarejestrować listę ostatnio używanych plików, dla każdego użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Porady: Otwórz edytory specyficznego dla projektu](../../extensibility/how-to-open-project-specific-editors.md)   
 [Porady: otwieranie standardowe edytory](../../extensibility/how-to-open-standard-editors.md)   
 [Dodawanie projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)