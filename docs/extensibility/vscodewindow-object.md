---
title: Obiekt VSCodeWindow | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dcd2bf5768b26237c5bc9301de9480b549ce01de
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495365"
---
# <a name="vscodewindow-object"></a>Obiekt VSCodeWindow
Okno kodu jest okno dokumentu specjalistyczne, który może zawierać jeden lub więcej widoków tekstu, zwykle <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiektu.  
  
 Pod względem architektury w oknie Kod jest okno dokumentu, który znajduje się w ramki okna. Funkcjonalnie okna kodu jest po prostu okno dokumentu z dodatkowych funkcji. W trybie interfejsu wielu dokumentów (MDI) w oknie Kod jest podrzędna ramka MDI. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kodu systemu windows przy użyciu starszej wersji interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Poniższa tabela zawiera interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Dostarcza mechanizm ogólnego dostępu do lokalizowania usługi, która identyfikuje Unikatowy identyfikator globalny (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Reprezentuje wiele podrzędnych interfejsu (MDI) dokumentu zawierającego jeden lub więcej widoków kodu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Wypełnia ramki okna.|  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Edytuj dane](https://www.microsoft.com/download/details.aspx?id=55984)