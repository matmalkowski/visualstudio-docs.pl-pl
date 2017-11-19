---
title: Hierarchie w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a651267ed279fa5efaf14efb4f1f866794c5cc3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="hierarchies-in-visual-studio"></a>Hierarchie w programie Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zintegrowane środowisko programistyczne (IDE) Wyświetla projektu jako *hierarchii*. W środowisku IDE programu hierarchii jest drzewo węzłów, gdzie każdy węzeł ma zestaw właściwości. A *projektu hierarchii* jest kontenerem, który zawiera elementy projektu, relacje elementów członkowskich i elementów powiązanych właściwości i poleceń.  
  
 W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], projektu hierarchii można zarządzać za pomocą interfejsu hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Interfejsu przekierowuje wywołania z elementów projektu do okna odpowiedniej hierarchii zamiast standardowego polecenia program obsługi poleceń.  
  
## <a name="project-hierarchies"></a>Projekt hierarchii  
 Każda hierarchia projektu zawiera elementy, które można wyświetlać i edytować. Te elementy różnią się w zależności od typu projektu. Na przykład projekt bazy danych może zawierać procedur składowanych, widoków bazy danych i tabel bazy danych. Projekt język programowania, z drugiej strony, prawdopodobnie zawiera pliki źródłowe i pliki zasobów dla mapy bitowe i okna dialogowe pól. Hierarchie mogą być zagnieżdżane, które zapewnia elastycznością dodane podczas tworzenia hierarchii projektu.  
  
 Podczas tworzenia nowego typu projektu typ projektu określa pełny zestaw elementów, które mogą być edytowane w nim. Jednak projekty mogą zawierać elementy, dla których nie mają edycji pomocy technicznej. Na przykład projektów Visual C++ może zawierać pliki HTML, mimo że Visual C++ nie zapewnia dowolnego edytora dostosowane dla danego typu pliku HTML.  
  
 Hierarchie Zarządzanie trwałości elementów, które zawierają. Implementacja w hierarchii musi kontrolować specjalnych właściwości, które mają wpływ na trwałości elementów w hierarchii. Na przykład jeśli elementy reprezentują obiektów w repozytorium zamiast plików, implementacja hierarchii musi kontrolować trwałości tych obiektów. IDE sam kieruje hierarchii do zapisania elementów zgodnie z danych wejściowych użytkownika, ale IDE nie kontroluje żadnych akcji, aby zapisać te elementy. Zamiast tego projektu jest w formancie.  
  
 Po otwarciu elementu w edytorze, hierarchii, która kontroluje ten element jest zaznaczony, a staje się aktywnej hierarchii. Wybrana hierarchia określa zestaw poleceń do działania w elemencie. Fokus w ten sposób śledzenia umożliwia hierarchii w celu odzwierciedlenia bieżącego kontekstu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy projektów](../../extensibility/internals/project-types.md)   
 [Wybór i waluty w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Przykłady VSSDK](http://aka.ms/vs2015sdksamples)