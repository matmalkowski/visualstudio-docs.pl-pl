---
title: 'Porady: aktualizowanie pasek stanu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 97b96023682d1acfda5aa0c47c07169b558c7569
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679778"
---
# <a name="how-to-update-the-status-bar"></a>Porady: aktualizowanie paska stanu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: aktualizowanie pasek stanu](https://docs.microsoft.com/visualstudio/extensibility/how-to-update-the-status-bar).  
  
**Pasek stanu** pasek sterowania znajduje się w dolnej części wiele okien aplikacji, zawierający co najmniej jeden stan wierszy tekstu lub wskaźniki.  
  
### <a name="to-update-the-status-bar"></a>Aby zaktualizować paska stanu  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> dla każdego obiektu poszczególnych widoku (DocView), zapewniająca edytora, takie jak widok formularza i widoku kodu.  
  
2.  Kiedy wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, zaktualizuj informacje w **pasek stanu** przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Wywołania środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> tylko kiedy okno dokumentu został początkowo uaktywniony. Pozostały okres czasu, który okna dokumentu jest aktywny, należy zaktualizować **pasek stanu** informacji jako stan zmiany edytora.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 A **pasek stanu** zawiera cztery oddzielne pola:  
  
-   Tekst statusu  
  
-   Pasek postępu  
  
-   Animowaną ikonę  
  
-   Edytor informacji  
  
 Aby uzyskać więcej informacji, zobacz [paski stanu](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
 IDE automatycznie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metody usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> wdrożenia po uaktywnieniu okna dokumentu.  
  
 Implementujący pakietu VSPackage jest odpowiedzialny za aktualizowanie tekst statusu na pasku stanu. IDE resetuje ten ciąg na "GOTOWY", jeśli pole tekstowe stan jest ustawiony na pusty tekst ("") w czasie bezczynności.  
  
## <a name="see-also"></a>Zobacz też  
 [Paski stanu](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)

