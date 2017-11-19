---
title: 'Porady: zaktualizuj pasek stanu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6218d697880da3ebf0d9af5599b5a7ca37ddf2f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-the-status-bar"></a>Porady: aktualizowanie paska stanu
**Pasek stanu** pasek sterowania znajduje się u dołu wiele okien aplikacji zawiera jeden lub więcej wierszy tekstu stanu lub wskaźników.  
  
### <a name="to-update-the-status-bar"></a>Aby zaktualizować pasek stanu  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> na każdy obiekt poszczególnych widoku (Widok dokumentu), który zawiera edytor, takie jak widok formularza i widoku kodu.  
  
2.  Gdy wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, zaktualizuj informacje w **pasek stanu** przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> tylko po oknie dokumentu został początkowo uaktywniony. W pozostałej części czas, który oknie dokumentu jest aktywny, należy zaktualizować **pasek stanu** informacji dotyczących stanu zmiany edytora.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 A **pasek stanu** zawiera cztery oddzielne pola:  
  
-   Tekst stanu  
  
-   Pasek postępu  
  
-   Ikona animowany  
  
-   Edytor informacji  
  
 Aby uzyskać więcej informacji, zobacz [pasków stanu](/cpp/mfc/status-bars).  
  
 IDE automatycznie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metody z <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementacji po uaktywnieniu okna dokumentu.  
  
 Realizator pakiet VSPackage jest odpowiedzialny za aktualizowanie tekstu stanu na pasku stanu. IDE resetuje to ciąg "Gotowe", jeśli ustawiono stan pola tekstowego do pusty tekst ("") w czasie bezczynności.  
  
## <a name="see-also"></a>Zobacz też  
 [Paski stanu](/cpp/mfc/status-bars)