---
title: Uzyskiwanie dostępu do theText widoku przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7aa879847e87b1a0372e2a8e9a3a6ec712041a56
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Uzyskiwanie dostępu do theText widoku przy użyciu interfejsu API starsza wersja
Widok tekstu jest prezentacji tekstu, który jest przechowywany w buforu tekstu. Przy użyciu starszej wersji interfejsu API, jak pokazano w poniższej sekcji można uzyskać dostępu do widoku tekstu.

## <a name="text-view-object"></a>Obiekt widoku tekstu
 Każdy widok jest skojarzony z buforu tekstu, a widok jest oknem na dane w buforze. Na poniższym diagramie przedstawiono kluczowe interfejsy obiekt widoku tekstu, który jest reprezentowany przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 ![Obiekt widoku tekstu w usłudze Visual Studio](../extensibility/media/vstextview.gif "vstextview") obiekt widoku tekstu

 Widok jest sposób przedstawiania tekstu w buforze. Zawiera funkcje, takie jak zawijanie, wskazujący, dzięki czemu można zobaczyć w widoku nie jest dokładnie reprezentację tekstu w buforze.

 Widok umożliwia innych usług lub procesów przechwycenia przychodzących poleceń i działają na nich przed widoku działa na nich. Najbardziej typowe usługi, w tym celu jest usługi języka. Usługa języka może być konieczne na przykład przechwycenia polecenia dla klawisz ENTER, aby zapewnić niestandardowe wcięcia tekstu etykietki narzędzia lub zachowanie.

## <a name="adding-functionality-to-the-text-view"></a>Dodawanie funkcji do widoku tekstu
 Aby dostosować zachowanie widoku tekstu, obsługi określonego klawisza. Przechwycenia naciśnięcia klawiszy, należy zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> na nazwę obiektu i podaj docelowym polecenia (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) do monitorowania i przecięcia poleceń.

 Widok tekstu korzysta sekwencyjnych architektury polecenia filtrów. Nowe filtry polecenia (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiektów) są dodawane do sekwencji przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody.

 Powiadamianie o zdarzeniach dla widoku tekstu odbywa się przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents> interfejsu. Implementuje ten interfejs na obiekt klienta do otrzymywania powiadomień o zmianach w widoku tekstu. Uwidacznia interfejsu do widoku tekstu przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfejsu w widoku tekstu, aby otrzymywać powiadomienia o zmianach z widoku.

## <a name="see-also"></a>Zobacz też

- [Zmiana ustawień widoku przy użyciu interfejsu API starsza wersja](../extensibility/changing-view-settings-by-using-the-legacy-api.md)
- [Za pomocą Menedżera tekstu do monitorowania ustawień globalnych](../extensibility/using-the-text-manager-to-monitor-global-settings.md)