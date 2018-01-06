---
title: Zapisanie dokumentu standardowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0cdfb4631420f6803e6434bd67b93bd713cfd1f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="saving-a-standard-document"></a>Zapisywanie standardowego dokumentu
Środowisko obsługi Zapisz, Zapisz jako i Zapisz wszystkie polecenia. Gdy użytkownik wybierze **zapisać**, **Zapisz jako**, lub **Zapisz wszystko** z **pliku** menu lub rozwiązanie, co powoduje zamknięcie  **Zapisz wszystkie**, odbywa się następujący proces.  
  
 ![Edytor standardowy](../../extensibility/internals/media/public.gif "publiczny")  
Zapisz, Zapisz jako, a następnie zapisz wszystkie polecenia Obsługa standardowego edytora  
  
 Ten proces została szczegółowo opisana w poniższych krokach:  
  
1.  Gdy **zapisać** i **Zapisz jako** polecenia są wybrane, używa środowiska <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi do określenia aktywne okno dokumentu, a w związku z tym jakie elementy ma zostać zapisany. Gdy aktywne okno dokumentu jest znany, środowiska znajduje wskaźnika hierarchii i identyfikator elementu (itemID) dla dokumentu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji, zobacz [systemem tabeli dokumentu](../../extensibility/internals/running-document-table.md).  
  
     Gdy **Zapisz wszystko** polecenia jest zaznaczone, środowisko używa tych informacji w uruchomionej tabeli dokumentów do listy wszystkich elementów do zapisania.  
  
2.  Po rozwiązaniu odbiera <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> wywołanie, jego iterację zbiór wybranych elementów (czyli kolumny wielokrotny udostępnianych przez <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi).  
  
3.  Na każdy element przy wyborze rozwiązania używa wskaźnika hierarchii do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodę, aby określić, czy **zapisać** polecenie powinno być włączone. Jeśli co najmniej jednego elementu zostały zmienione, a następnie **zapisać** polecenie jest włączone. Jeśli hierarchia używa standardowego edytora, następnie delegatów hierarchii wykonywania zapytania dotyczącego zmieniony stan do edytora przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.  
  
4.  Każdego wybranego elementu, który został zmieniony, w tym rozwiązaniu zastosowano wskaźnika hierarchii do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody w odpowiedniej hierarchii.  
  
     Jest typowe dla hierarchii, aby edytować dokument za pomocą edytora standardowego. W takim przypadku dane dokumentu obiekt powinien obsługiwać tego edytora <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfejsu. Odebrane <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> wywołanie metody projektu informowało edytorze zapisywaniu dokumentu przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> metody dla obiekt danych dokumentu. Edytor umożliwia środowiska do obsługi **Zapisz jako** okno dialogowe, wywołując `Query Service` dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interfejsu. Zwraca wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejsu. Edytor musi wywoływać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> jest metoda wskaźnik do edytora <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> wdrożenia za pomocą klasy `pPersistFile` parametru. Następnie wykonuje operację zapisywania środowiska i zapewnia **Zapisz jako** okno dialogowe edytora. Środowisko wywołuje wstecz do edytora z <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Jeśli użytkownik próbuje zapisać dokument bez tytułu (to znaczy wcześniej niezapisane dokumentu), polecenia Zapisz jako faktycznie jest wykonywana.  
  
6.  Dla polecenia Zapisz jako środowisko Wyświetla okno dialogowe Zapisz jako, monitowania użytkownika o podanie nazwy pliku.  
  
     Jeśli zmieniono nazwę pliku, a następnie hierarchii jest odpowiedzialny aktualizowanie ramki dokumentu buforowanych informacji przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
 Jeśli **Zapisz jako** polecenie spowoduje przeniesienie lokalizacji dokumentu i hierarchii jest wielkość liter w lokalizacji dokumentu, a następnie hierarchii jest odpowiedzialny za przekazywanie własność otwartego okna dokumentu do innej hierarchii. Występuje to na przykład jeśli projekt śledzi, czy plik jest wewnętrzny lub zewnętrzny plik (różne) w odniesieniu do projektu. Użyj poniższej procedury można zmienić własności plik do projektu różne pliki.  
  
## <a name="changing-file-ownership"></a>Zmiana własności plików  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Aby zmienić własność pliku do projektu różne pliki  
  
1.  Zapytanie usługi dla <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interfejsu.  
  
     Wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> jest zwracany.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) metodę, aby przenieść dokument do nowej hierarchii. Wykonanie polecenia Zapisz jako hierarchii wywołuje tę metodę.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)