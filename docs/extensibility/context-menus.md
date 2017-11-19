---
title: Menu kontekstowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d56be2fecca89d3cfb5a7b12982a0de7f61d457f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="context-menus"></a>Menu kontekstowe
Menu kontekstowe są wyświetlane, gdy użytkownik kliknie prawym przyciskiem myszy w aktywnego regionu obszaru klienckiego i usuń zaznaczenie po zwolnieniu prawego przycisku myszy.  
  
## <a name="editor-context-menus"></a>Menu kontekstowe edytora  
 Przechwycenie `ECMD_SHOWCONTEXTMENU`, usługi języka można kontrolować menu kontekstowe, które będą wyświetlane w edytorze. Aby wyświetlić własny menu kontekstowego, to polecenie obsługi przekazanej do Twojej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Jeśli nie obsługują tego polecenia, IDE przedstawia standardowe menu kontekstowe podane edytora. Można też kontrolować zawartość elementu menu kontekstowego w zasadzie na znacznika. Aby uzyskać więcej informacji na ten temat, zobacz [przy użyciu znaczników tekstu przy użyciu interfejsu API starszych](../extensibility/using-text-markers-with-the-legacy-api.md) i [przechwytywaniu polecenia usługi języka starszych](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie usługi języka starsza wersja](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)