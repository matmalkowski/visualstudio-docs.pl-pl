---
title: 'Porady: Implementowanie Znajdź i Zastąp mechanizmu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26d1866d9b816dfca3f82f98db372865f9d27a68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128947"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Porady: Implementowanie Znajdź i Zastąp mechanizmu
Program Visual Studio udostępnia dwa sposoby wdrażania Znajdź i Zamień. Jednym ze sposobów jest przekazać obraz tekstu do powłoki i pozwól mu wyszukiwanie, wyróżnianie i zastępując tekst. Dzięki temu użytkownicy mogą określić wiele zakresów tekstu. Alternatywnie VSPackage można kontrolować, ta sama funkcja. W obu przypadkach należy powiadomić powłokę o bieżącą lokalizację docelową i elementów docelowych dla wszystkich otwartych dokumentów.  
  
### <a name="to-implement-findreplace"></a>Aby zaimplementować Znajdź i Zamień  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfejsu na jednym z obiektów zwróconych przez właściwości ramki <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> lub <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. W przypadku tworzenia edytora niestandardowego, należy zaimplementować ten interfejs jako część klasy niestandardowego edytora.  
  
2.  Użyj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> metody umożliwia określenie opcji, które obsługuje edytora i wskaż, czy implementuje wyszukiwanie obrazów tekstu.  
  
     Edytor obsługuje wyszukiwanie obrazów tekstu, należy wdrożyć <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     W przeciwnym razie zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  W przypadku zastosowania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> metod, można ułatwić wyszukiwanie zadań, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>