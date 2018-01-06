---
title: Uproszczone osadzanie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 183dc4ad9d7ea1a2f6855be050ad8459a3f801ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="simplified-embedding"></a>Uproszczone osadzanie
Osadzanie uproszczony jest włączona w edytorze, po jego obiekt widoku dokumentu jest elementem nadrzędnym (to znaczy dokonać elementu podrzędnego) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]i <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejs jest implementowany jej okna poleceń. Uproszczony edytory osadzania nie może obsługiwać aktywny formant. Obiekty używane do tworzenia edytora z uproszczone osadzanie przedstawiono na poniższej ilustracji.  
  
 ![Uproszczone osadzanie edytor grafiki](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Edytor z uproszczone osadzanie  
  
> [!NOTE]
>  Na tej ilustracji tylko obiektów `CYourEditorFactory` obiektu jest wymagane do utworzenia standardowego edytora opartych na plikach. W przypadku tworzenia edytora niestandardowego, nie należy do implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, ponieważ edytora prawdopodobnie będzie miał własną mechanizmu stanu trwałego prywatnych. Dla edytora z systemem innym niż niestandardowe jednak należy to zrobić.  
  
 Wszystkie interfejsy implementowane tworzenia edytora z osadzanie uproszczone są zawarte w `CYourEditorDocument` obiektu. Jednak do obsługi wielu widoków danych dokumentu, Podziel interfejsy na oddzielnych obiektów dane i przeglądać opisane w poniższej tabeli.  
  
|Interface|Lokalizacja interfejsu|Zastosowanie|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Widok|Zapewnia połączenie okno nadrzędne.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Widok|Obsługi poleceń.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Widok|Włącza aktualizacje paska stanu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Widok|Umożliwia **przybornika** elementów.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dane|Wysyła powiadomienia o zmianie pliku.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dane|Włącza funkcję Zapisz jako dla typu pliku.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dane|Włącza trwałość dla dokumentu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dane|Umożliwia pomijanie pliku zdarzenia zmiany, takie jak ponowne załadowanie wyzwalania.|