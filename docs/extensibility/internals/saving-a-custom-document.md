---
title: Zapisywanie dokumentu niestandardowego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2b19c6ba222644bc9d5fb97874f50bf6a6aa59d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="saving-a-custom-document"></a>Zapisanie dokumentu niestandardowych
Uchwyty środowiska **zapisać**, **Zapisz jako**, i **Zapisz wszystko** poleceń. Gdy użytkownik kliknie **zapisać**, **Zapisz jako**, **lub zapisać wszystkie** na **pliku** menu lub zamyka rozwiązanie, co powoduje Zapisz wszystko, następujące proces.  
  
 ![Zapisywanie w edytorze niestandardowym](../../extensibility/internals/media/private.gif "prywatnych")  
Zapisz, Zapisz jako, a następnie zapisz wszystkie polecenia Obsługa niestandardowego edytora  
  
 Ten proces została szczegółowo opisana w poniższych krokach:  
  
1.  Dla **zapisać** i **Zapisz jako** polecenia używa środowiska <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi do określenia aktywne okno dokumentu, a w związku z tym jakie elementy ma zostać zapisany. Gdy aktywne okno dokumentu jest znany, środowiska znajduje wskaźnika hierarchii i identyfikator elementu (itemID) dla dokumentu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji, zobacz [systemem tabeli dokumentu](../../extensibility/internals/running-document-table.md).  
  
     Zapisz wszystkie polecenia środowiska informacje są używane w uruchomionej tabeli dokumentów do listy wszystkich elementów, aby zapisać.  
  
2.  Po rozwiązaniu odbiera <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> wywołanie, jego iterację zbiór wybranych elementów (czyli kolumny wielokrotny udostępnianych przez <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usługi).  
  
3.  Na każdy element przy wyborze rozwiązania używa wskaźnika hierarchii do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> metodę, aby określić, czy polecenie Zapisz powinno być włączone. Jeśli co najmniej jednego elementu zostały zmienione, polecenie Zapisz jest włączone. Jeśli hierarchia używa standardowego edytora, następnie delegatów hierarchii wykonywania zapytania dotyczącego zmieniony stan do edytora przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> metody.  
  
4.  Każdego wybranego elementu, który został zmieniony, w tym rozwiązaniu zastosowano wskaźnika hierarchii do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> metody w odpowiedniej hierarchii.  
  
     W przypadku edytora niestandardowego komunikacji między obiektem danych dokumentu i projektu jest prywatne. W związku z tym wszelkie problemy dotyczące trwałości specjalne są obsługiwane między tymi dwoma obiektami.  
  
    > [!NOTE]
    >  W przypadku zastosowania własnych trwałości, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> metodę, aby zaoszczędzić czas. Ta metoda sprawdza się, że jest bezpieczne zapisać plik (na przykład plik nie jest tylko do odczytu).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)