---
title: "Porady: Implementowanie zarządzania cofania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f61ee4c561e32f17afa1b53cbf3bd3bf982feeb4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-undo-management"></a>Porady: Implementowanie zarządzania cofania
Podstawowy interfejs używany do zarządzania cofania jest <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, który jest implementowany przez środowisko. Do obsługi zarządzania cofania, wdrożenie jednostek cofania oddzielne (to znaczy <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, które zawierają wiele poszczególne kroki.  
  
 Sposobu implementacji zarządzania cofania może być różna w zależności od tego, czy edytor obsługuje wiele widoków, czy nie. Procedury dla każdego wdrożenia są szczegółowo opisane w poniższych sekcjach.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Przypadków, gdy Edytor obsługuje jeden widok  
 W tym scenariuszu edytor nie obsługuje wielu widoków. Istnieje tylko jeden z nich i jeden dokument, i obsługują cofania. Poniższa procedura umożliwia Implementowanie zarządzania cofania.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Do obsługi zarządzania cofania edytora pojedynczego widoku  
  
1.  Wywołanie `QueryInterface` na `IServiceProvider` interfejsu na ramki okna dla `IOleUndoManager`, z obiektu widoku dokumentu, aby otworzyć menedżera cofania (`IID_IOLEUndoManager`).  
  
2.  Widok jest ulokowany do ramki okna, pobiera wskaźnik lokacji, której można użyć do wywołania `QueryInterface` dla `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Przypadków, gdy Edytor obsługuje wiele widoków  
 Jeśli masz separacji dokument i widoku, oznacza to, że menedżera cofania zazwyczaj co skojarzony z dokumentem. Wszystkie jednostki cofania są umieszczane na menedżera cofania co skojarzony z obiektem danych dokumentu.  
  
 Zamiast widoku wykonywania zapytania dotyczącego menedżera cofania, w których jest on dostępny dla każdego widoku, dane dokumentu obiekt wywołania <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> można utworzyć wystąpienia menedżera cofania, określając identyfikator klasy CLSID_OLEUndoManager. Identyfikator klasy jest zdefiniowana w pliku OCUNDOID.h.  
  
 Korzystając z <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> Aby utworzyć własnego wystąpienia menedżera cofania, użyj poniższej procedury na połączeniu menedżera cofania do środowiska.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Aby przyłączyć menedżera cofania do środowiska  
  
1.  Wywołanie `QueryInterface` zwrócony z obiektu <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> dla `IID_IOleUndoManager`. Wskaźnik do przechowywania <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  Wywołanie `QueryInterface` na `IOleUndoManager` dla `IID_IOleCommandTarget`. Wskaźnik do przechowywania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Przekaźnik Twojej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> wywołuje przechowywanych `IOleCommandTarget` interfejs dla poniższych poleceń StandardCommandSet97:  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Wywołanie `QueryInterface` na `IOleUndoManager` dla `IID_IVsChangeTrackingUndoManager`. Wskaźnik do przechowywania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Za pomocą wskaźnika do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> do wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> metody.  
  
5.  Wywołanie `QueryInterface` na `IOleUndoManager` dla `IID_IVsLinkCapableUndoManager`.  
  
6.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> z dokumentu, które powinny również implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interfejsu. Gdy dokument jest zamykany, wywołaj `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  Gdy dokument jest zamykany, wywołaj `QueryInterface` na menedżera cofania dla `IID_IVsLifetimeControlledObject`.  
  
8.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Podczas wprowadzania zmian do dokumentu, należy wywołać <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> w Menedżerze z `OleUndoUnit` klasy. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> — Metoda przechowuje odwołanie do obiektu, dlatego zazwyczaj należy zwolnić po prawej <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 `OleUndoManager` Klasa reprezentuje wystąpienie stosu cofania pojedynczego. W związku z tym jest jeden obiekt menedżera cofania na jednostkę danych śledzone cofania lub ponownego wykonywania.  
  
> [!NOTE]
>  Gdy obiekt menedżera cofania jest często używany przez Edytor tekstu, jest ogólne składnika, który nie obsługuje określonego edytora tekstu. Jeśli chcesz obsługuje wielopoziomowe cofania lub ponownego wykonywania tego obiektu można używać, aby to zrobić.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Porady: wyczyścić stosu cofania](../extensibility/how-to-clear-the-undo-stack.md)