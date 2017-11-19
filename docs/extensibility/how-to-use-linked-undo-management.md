---
title: "Porady: za pomocą przystawki Zarządzanie połączonego cofania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05e10305f7e4c243f799cfe33d4d9b86418eed86
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-linked-undo-management"></a>Porady: za pomocą przystawki Zarządzanie połączonego cofania
Połączonego cofania umożliwia użytkownikowi cofnąć równocześnie w tej samej zmiany w wielu plikach. Na przykład jednoczesnych tekst zostanie zmieniony na wiele plików programów, takich jak plik nagłówka i plik Visual C++ jest transakcją połączonego cofania. Możliwość połączonego cofania jest wbudowana w implementacji środowiska menedżera cofania i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> umożliwia manipulowanie tej możliwości. Połączonego cofania jest implementowany przez modułu cofnięcia nadrzędnego, który można połączyć stosy oddzielne cofania razem powinien być traktowany jako jednostki cofania pojedynczego. Procedury dotyczące korzystania z połączonego cofania została szczegółowo opisana w następnej sekcji.  
  
### <a name="to-use-linked-undo"></a>Aby użyć połączonego cofania  
  
1.  Wywołanie `QueryService` na `SVsLinkedUndoManager` otrzymywać wskaźnik do `IVsLinkedUndoTransactionManager`.  
  
2.  Tworzenie początkowej nadrzędnej jednostki połączonego cofania przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Pojedynczy punkt początkowy dla zestawu stosów cofania mają być grupowane w stosy połączonego cofania. W `OpenLinkedUndo` metody należy również określić, czy połączonego cofania ograniczeniami lub z systemem innym niż strict. Zachowanie non-strict połączonego cofania oznacza, że można zamknąć niektórych dokumentów z połączonego cofania elementów równorzędnych i nadal pozostaw innych połączone cofanie elementów równorzędnych na ich stosy. Zachowanie Strict połączonego cofania Określa, że można cofnąć razem lub w ogóle nie wszystkie stosy element równorzędny połączonego cofania. Dodaj kolejne połączone cofanie stosy przez wywołanie metody [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) metody.  
  
3.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> wycofanie wszystkich jednostek połączonego cofania jako jeden.  
  
    > [!NOTE]
    >  Aby zaimplementować Zarządzanie połączonego cofania w edytorze, Dodaj zarządzania cofania. Aby uzyskać więcej informacji na implementacji zarządzania połączonego cofania, zobacz [jak: Implementowanie zarządzania cofnąć](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Porady: Implementowanie zarządzania cofania](../extensibility/how-to-implement-undo-management.md)