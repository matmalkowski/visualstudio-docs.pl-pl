---
title: "Automatyczne formatowanie starsza wersja usługi języka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09ab8a948011cdc53516ec21f0d213852166956
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatyczne formatowanie starsza wersja usługi języka
Z automatycznego formatowania usługi języka automatycznie wstawia fragment kodu, gdy użytkownik rozpoczyna wpisz konstrukcję kodu znane.  
  
## <a name="automatic-formatting-behavior"></a>Zachowanie automatyczne formatowanie  
 Na przykład po wpisaniu `if`, usługa języka automatycznie wstawia pasujących nawiasów klamrowych lub po naciśnięciu klawisza ENTER usługi języka wymusza punkt wstawiania w nowym wierszu poziomu wcięcia odpowiednie, w zależności od tego, czy poprzednie wiersz otwiera nowy zakres.  
  
 Filtr polecenia używane w pozostałej części usługi języka można również automatycznego formatowania. Można też wyróżnić pasujących nawiasów klamrowych, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie usługi języka starsza wersja](../../extensibility/internals/developing-a-legacy-language-service.md)