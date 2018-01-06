---
title: "Porady: Otwórz edytory specyficznego dla projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 66ac0837649b42dc238eac57829c713b2bf83e3a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-project-specific-editors"></a>Porady: Otwórz edytory specyficznego dla projektu
Jeśli plik elementu otwierany przez projekt leżą jest powiązana z określonego edytora dla tego projektu, projekt musi otworzyć plik za pomocą edytora określonego projektu. Plik nie może być delegowane do IDE mechanizm wybierania edytora. Na przykład zamiast za pomocą edytora standardowego mapy bitowej, możesz użyć tej opcji edytora specyficznych dla projektu do określenia Edytor określonych mapy bitowej, które rozpoznaje informacje w pliku, który jest unikatowy dla projektu.  
  
 Wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody, gdy ustali, że plik powinien zostać otwarty przez określonego projektu. Aby uzyskać więcej informacji, zobacz [wyświetlanie plików za pomocą polecenia Otwórz plik](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Skorzystaj z poniższych wskazówek, aby zaimplementować `OpenItem` metody mają projektu otwórz plik za pomocą edytora określonego projektu.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Aby zaimplementować metodę OpenItem za pomocą edytora specyficznego dla projektu  
  
1.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> — metoda (RDT_EditLock) w celu ustalenia, czy plik (obiekt dokument danych) jest już otwarty.  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji o danych dokumentu i obiekty widoku dokumentów, zobacz [dane dokumentu i Widok dokumentu w edytorach niestandardowe](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Jeśli plik jest już otwarty, wywołując resurface pliku <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> — metoda i określenia wartości IDO_ActivateIfOpen dla `grfIDO` parametru.  
  
     Jeśli plik jest otwarty, dokument jest własnością projektu niż wywołującym projekt ostrzeżenie będzie widoczny dla użytkownika, że edytor otwierany z innego projektu. Okno plików jest następnie udostępniane.  
  
3.  Jeśli chcesz dołączyć do niego inny widok z buforu tekstu (obiekt dokument danych) jest już otwarty, jest odpowiedzialny za Przechwytywanie tego widoku. Zalecane podejście do tworzenia wystąpienia widoku (obiekt widoku dokument) z projektu, jest następujący:  
  
    1.  Wywołanie `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> usługi otrzymywać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interfejsu.  
  
    2.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metodę w celu utworzenia wystąpienia klasy widok dokumentu.  
  
4.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metoda określania obiektu widoku dokumentu.  
  
     Ta metoda witryny obiektu widoku dokumentu w oknie dokumentu.  
  
5.  Wykonaj odpowiednie wywołania jednej <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> metody.  
  
     W tym momencie widoku powinna być w pełni zainicjowane i gotowa do otwarcia.  
  
6.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metody, aby wyświetlić i otworzyć widok.  
  
## <a name="see-also"></a>Zobacz też  
 [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Porady: otwieranie standardowe edytory](../extensibility/how-to-open-standard-editors.md)   
 [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../extensibility/how-to-open-editors-for-open-documents.md)