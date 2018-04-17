---
title: Dane dokumentu i zarządzania dokumentami wyświetlić w niestandardowych edytorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb445ca70ac74cf2601e9f1035549bb686fca798
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dane dokumentu i Widok dokumentu w edytorach niestandardowych
Niestandardowy Edytor składa się z dwóch części: obiekt danych dokumentu i obiektu widoku dokumentu. Jako nazwy sugerują, obiekt danych dokumentu reprezentuje danych tekst do wyświetlenia, a obiekt widoku dokumentu (lub "Widok") — co najmniej jeden windows wyświetlania obiektu danych dokumentu.  
  
## <a name="document-data-object"></a>Obiekt danych dokumentu  
 Obiekt danych dokumentu jest reprezentację danych tekstu w buforze tekstu. Jest obiekt COM, który przechowuje tekst dokumentu i inne informacje, obsługuje trwałości dokumentu i umożliwia jego danych z wielu widoków. Aby uzyskać więcej informacji, zobacz artykuł  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> i [dokumentu Windows](../extensibility/internals/document-windows.md).  
  
 Projektanci i edytory niestandardowych można zdecydować się na użycie <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu lub własne niestandardowe buforu. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> następuje uproszczony model osadzania dla standardowego edytora, obsługuje wiele widoków i zapewnia interfejsów zdarzeń, które są używane do zarządzania wielu widoków.  
  
## <a name="document-view-object"></a>Obiekt widoku dokumentu  
 Okno wyświetla kod i innych tekst jest znany jako dokument widoku lub widok. Podczas tworzenia edytora, można wybrać jeden widok, w którym jest wyświetlany tekst w jednym oknie, lub wiele widok, w którym jest wyświetlany tekst w więcej niż jedno okno. Wybór zależy od aplikacji. Na przykład edytowanie side-by-side, należy wybrać wiele widoku. Każdy widok jest skojarzony z wpisem w zintegrowane środowisko programistyczne firmy (IDE) z tabeli dokumentu (Normalizacją). Widok systemu windows należy do projektu lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu.  
  
 Jeśli Edytor obsługuje wiele widoków obiektu danych dokumentu, dokument danych i obiektów widoku dokumentu musi być oddzielne. W przeciwnym razie one mogą być zgrupowane razem. Aby uzyskać więcej informacji, zobacz [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).  
  
 IDE powiadamia widoków o zdarzeniach (na przykład, gdy rozwiązanie zawierające dokument jest zamykany) przez dopasowanie identyfikatora elementu (ItemID) dla każdego wpisu w uruchomionej tabeli dokumentów. Aby uzyskać więcej informacji o tym, zobacz [systemem tabeli dokumentu](../extensibility/internals/running-document-table.md).  
  
 Dostępne są dwie opcje tworzenia widoku edytora niestandardowego. Jedna jest modelu aktywacji w miejscu, gdzie jest hostowana widoku w oknie za pomocą formantu ActiveX lub obiektu danych dokumentu. Drugim jest uproszczony model osadzania, gdy widok jest hostowana przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> zaimplementowano okna poleceń. Aby uzyskać informacje na temat modelu aktywacji w miejscu, zobacz [Aktywacja w miejscu](../extensibility/in-place-activation.md). Informacje o uproszczony model osadzania, zobacz [uproszczone osadzanie](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md)   
 [Uproszczone osadzanie](../extensibility/simplified-embedding.md)   
 [Porady: dołączanie widoków danych dokumentów](../extensibility/how-to-attach-views-to-document-data.md)   
 [Zarządzanie właściciela blokady dokumentu](../extensibility/document-lock-holder-management.md)   
 [Jedno- i kartę wielu widoków](../extensibility/single-and-multi-tab-views.md)   
 [Zapisywanie standardowego dokumentu](../extensibility/internals/saving-a-standard-document.md)   
 [Trwałość i uruchomiona tabeli dokumentu](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Określanie otwieranym edytora plików w projekcie](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Fabryki edytora](../extensibility/editor-factories.md)