---
title: Obiekt VSCodeWindow | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2de0998a3d89c1af3e18fa60aa3f8511716f6165
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="vscodewindow-object"></a>Obiekt VSCodeWindow
Okno kodu jest oknem dokument specjalistycznych, które mogą obejmować co najmniej jeden widok tekstu, zwykle <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiektu.  
  
 Pod względem architektury okno Kod jest okno dokumentu, który mieści się w ramkę okna. Okno Kod jest funkcjonalnie, po prostu okno dokumentu z dodatkowych funkcji. W trybie interfejsu wielu dokumentów (MDI) okno Kod jest ramki podrzędnych MDI. Aby uzyskać więcej informacji, zobacz [dostosowywania kodu systemu Windows przy użyciu interfejsu API starszych](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Poniższa tabela zawiera interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Udostępnia mechanizm podstawowego dostępu do lokalizowania usługi, która identyfikuje Unikatowy identyfikator globalny (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Reprezentuje wiele podrzędnych interfejsu (MDI) dokumentu zawierającego co najmniej jeden widok kodu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Wypełnia ramki okna.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Edytowanie danych](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)