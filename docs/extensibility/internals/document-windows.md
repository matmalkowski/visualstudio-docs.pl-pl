---
title: Dokument z systemem Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 03e61b80aaf4c5c8b0e25f5b2a4a42f13d75d305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="document-windows"></a>Okna dokumentów
W programie Visual Studio *okno dokumentu* jest skojarzony z oknem interfejsu wielu dokumentów (MDI) okna podrzędnego ramce. Okna dokumentów są zwykle używane do wyświetlanie i modyfikowanie kodu źródłowego lub tekstu, ale może to również obsługiwać inne typy funkcjonalności. Okna dokumentów:  
  
-   Można organizować w grupach osobnej karcie pozioma lub pionowa w obiekcie nadrzędnym MDI tak, aby wiele pliki mogą być wyświetlane w tym samym czasie.  
  
-   Może być zadokowany w dowolnej kolejności w obiekcie nadrzędnym MDI.  
  
-   Może być za darmo przestawione.  
  
-   Są połączone w kolejności tabulacji inne okna MDI.  
  
 Polecenia do grupowania zadokowane i przestawne można znaleźć w menu skrótów kartę okno dokumentu.  
  
 Aby uzyskać więcej informacji dotyczących zachowania okna w programie Visual Studio, zobacz [dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implementacji okna dokumentu  
 Okna dokumentów są tworzone z zastosowaniem edytora. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Interfejsu tworzy okna dokumentów w ramach tworzenia wystąpienia edytora. Aby uzyskać więcej informacji, zobacz [starszych interfejsów w edytorze](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Aby zapewnić Wstecz i do przodu punkty nawigacji w oknie, należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfejsu. Edytor tekstu używa znacznikach tekstu, aby zidentyfikować punkty nawigacji w dokumencie.  
  
## <a name="the-running-document-table"></a>Uruchamianie tabeli dokumentu  
 IDE używa uruchomionej tabeli dokumentów (Normalizacją) do śledzenia stanu okna dokumentu. Normalizacją to mechanizm, przez który dokument systemu windows są powiadamiani o zdarzeń, takich jak zamknięcia rozwiązania lub plik został zmodyfikowany. Aby uzyskać więcej informacji, zobacz [systemem tabeli dokumentu](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Opóźnione ładowanie dokumentu](../../extensibility/internals/delayed-document-loading.md)