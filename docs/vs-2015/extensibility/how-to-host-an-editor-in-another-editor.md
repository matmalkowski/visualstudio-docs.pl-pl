---
title: 'Instrukcje: hostowanie redaktorem w innym edytorze | Dokumentacja firmy Microsoft'
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
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6390f5550c445239fbd8f8f72f9c8c4ad013665a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42671058"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Instrukcje: hostowanie redaktorem w innym edytorze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Edytor hosta w innym edytorze](https://docs.microsoft.com/visualstudio/extensibility/how-to-host-an-editor-in-another-editor).  
  
W programie Visual Studio może obsługiwać jednym edytorze wewnątrz innego, określając okna hostowania jako okno nadrzędne. Aby to zrobić, należy ustawić parametry <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> i <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> na ramki okna podrzędnego.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Aby ustawić ramki okna obsługi edytora  
  
1.  Wyznaczanie redaktorem hostowanej edytora, tworząc okienko okna podrzędnego.  
  
     To okienko jest, gdzie edytora tekstu.  
  
2.  Utwórz Edytor hostingu za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> metody.  
  
3.  Ustaw <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> i <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> właściwości w celu wykonania ramki okna edytora hostowanej przez przekazanie te właściwości jako parametry w celu <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> metody, odpowiednio.  
  
     Jeśli musisz pobrać te parametry, należy przekazać te właściwości, aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metody.  
  
4.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metoda zawartej edytora.  
  
     Edytor zostanie wyświetlony w okienku hostowanej zawierającego edytora.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 **Projektanta aplikacji** w Visual Studio Team Edition dla architektów jest przykładem ramki okna edytora obsługującego innym edytorze. **Projektanta aplikacji** hostuje innych projektantów w jej okienku po prawej stronie. Panel projektanta (lub **właściwości** stronie) dla każdej zawartej projektantów jest dodawany do zawierającego ramki okna.

