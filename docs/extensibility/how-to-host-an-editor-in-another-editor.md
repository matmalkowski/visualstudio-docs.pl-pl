---
title: 'Porady: hostowanie edytora w innym edytorze | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53b4f02135b18c4641d4e802df3d1124a5d06b47
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058389"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Porady: hostowanie edytora w innym edytorze

W programie Visual Studio może obsługiwać jeden edytor wewnątrz innego, określając okna hostowania jako okno nadrzędne. Aby to zrobić, należy ustawić parametry <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> i <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> na ramki okna podrzędnego.

## <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Aby skonfigurować ramki okna do hostowania edytora

1.  Wyznaczanie edytora Edytor hostowanej przez utworzenie okienko okna podrzędnego.

     To okienko jest, gdzie w edytorze tekstu.

2.  Utwórz Edytor hostingu za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> metody.

3.  Ustaw <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> i <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> właściwości w implementacji ramki okna edytora hostowanej przez przekazanie te właściwości jako parametry <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> metody odpowiednio.

     Jeśli wymagane jest pobranie tych parametrów, te właściwości, aby przekazać <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metody.

4.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metody zawartych w niej edytora.

     Edytor zostanie wyświetlony w okienku hostowanej zawierającego edytora.

## <a name="robust-programming"></a>Skuteczne programowanie

**Projektanta aplikacji** w Visual Studio Team Edition dla architektów jest przykładem ramki okna edytora obsługującego innego edytora. **Projektanta aplikacji** obsługuje innych projektantów w jej w okienku po prawej stronie. Panel projektanta (lub **właściwości** strony) dla każdego zawartych projektanci jest dodawany do zawierającego ramki okna.