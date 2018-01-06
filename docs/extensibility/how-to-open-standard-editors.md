---
title: 'Porady: otwieranie standardowe edytory | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dcf36dc8f4ef818a84719bc534a09ecf30baf76f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-standard-editors"></a>Porady: otwieranie standardowe edytory
Po otwarciu edytora standardowego umożliwisz IDE ustalić standardowego edytora dla typu pliku wyznaczonych, zamiast określania edytorze specyficznego dla projektu dla pliku.  
  
 Wykonaj następującą procedurę, aby zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metody. Spowoduje to otwarcie pliku projektu w standardowego edytora.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Aby zaimplementować metodę OpenItem przy użyciu standardowego edytora  
  
1.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) do określenia, czy plik obiektu danych dokumentu jest już otwarty.  
  
2.  Jeśli plik jest już otwarty, wywołując resurface pliku <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metody, określając wartość `IDO_ActivateIfOpen` dla `grfIDO` parametru.  
  
     Jeśli plik jest otwarty, dokument jest własnością innego projektu niż wywołującym projekt projektu otrzyma ostrzeżenie, że edytor otwierany jest z innego projektu. Okno plików jest następnie udostępniane.  
  
3.  Jeśli dokument nie jest otwarty lub nie znajduje się w uruchomionej tabeli dokumentów wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> — metoda (`OSE_ChooseBestStdEditor`) można otworzyć standardowego edytora dla pliku.  
  
     Po wywołaniu metody IDE wykonuje następujące zadania:  
  
    1.  Edytory skanuje IDE / {guidEditorType} / rozszerzenia podklucza rejestru, aby określić edytor, którego będzie mógł otworzyć plik i ma najwyższy priorytet w ten sposób.  
  
    2.  Po IDE stwierdził, edytor, którego będzie mógł otworzyć plik, wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Edytor implementacja tej metody zwraca informacje, które są wymagane dla IDE wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> i lokacji nowo otwartego dokumentu.  
  
    3.  Na koniec IDE ładuje dokumentu przy użyciu interfejsu zwykle trwałości, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Jeśli IDE wcześniej stwierdził, że hierarchia lub hierarchia elementów jest dostępny, wywołuje metodę IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> metody na projekt, aby pobrać kontekstu poziom projektu <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> wskaźnika do przekazania w z powrotem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> wywołania metody.  
  
4.  Zwraca <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> wskaźnika do środowiska IDE, gdy wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> na projekt, aby umożliwić kontekstu get edytor z projektu.  
  
     Wykonanie tego kroku umożliwia oferta projektu dodatkowe usługi do edytora.  
  
     Jeśli widok dokumentu lub obiekt widoku dokumentu został pomyślnie zlokalizowany w ramkę okna, obiekt jest inicjowany ze swoimi danymi, przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Porady: Otwórz edytory specyficznego dla projektu](../extensibility/how-to-open-project-specific-editors.md)   
 [Porady: Otwórz edytory dla otwarte dokumenty](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Wyświetlanie plików za pomocą polecenia Otwórz plik](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)