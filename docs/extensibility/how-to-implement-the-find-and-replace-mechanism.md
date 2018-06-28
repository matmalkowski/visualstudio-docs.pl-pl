---
title: 'Porady: Implementowanie Znajdź i Zastąp mechanizmu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 45d0b1307d86b32f1def3c4474e1ca25959915c0
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056449"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Porady: Implementowanie Znajdź i Zamień mechanizmu

Program Visual Studio udostępnia dwa sposoby wdrażania Znajdź i Zamień. Jednym ze sposobów jest przekazać obraz tekstu do powłoki i pozwól mu wyszukiwanie, wyróżnianie i zastępując tekst. Dzięki temu użytkownicy mogą określić wiele zakresów tekstu. Alternatywnie VSPackage można kontrolować, ta sama funkcja. W obu przypadkach należy powiadomić powłokę o bieżącą lokalizację docelową i elementów docelowych dla wszystkich otwartych dokumentów.

## <a name="to-implement-findreplace"></a>Aby zaimplementować Znajdź i Zamień

1. Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfejsu na jednym z obiektów zwróconych przez właściwości ramki <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView> lub <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>. Jeśli tworzysz niestandardowy edytor, należy zaimplementować ten interfejs jako część klasy niestandardowego edytora.

2. Użyj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> metody umożliwia określenie opcji, które obsługuje edytora i wskaż, czy implementuje wyszukiwanie obrazów tekstu.

   Edytor obsługuje wyszukiwanie obrazów tekstu, należy wdrożyć <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.

   W przeciwnym razie zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.

3. W przypadku zastosowania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> metod, można ułatwić wyszukiwanie zadań, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfejsu.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>