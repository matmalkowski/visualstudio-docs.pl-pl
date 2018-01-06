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
ms.workload: vssdk
ms.openlocfilehash: 43d9c59beaddfc6992e7b9e16e0e778be2a6d30f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatyczne formatowanie starsza wersja usługi języka
Z automatycznego formatowania usługi języka automatycznie wstawia fragment kodu, gdy użytkownik rozpoczyna wpisz konstrukcję kodu znane.  
  
## <a name="automatic-formatting-behavior"></a>Zachowanie automatyczne formatowanie  
 Na przykład po wpisaniu `if`, usługa języka automatycznie wstawia pasujących nawiasów klamrowych lub po naciśnięciu klawisza ENTER usługi języka wymusza punkt wstawiania w nowym wierszu poziomu wcięcia odpowiednie, w zależności od tego, czy poprzednie wiersz otwiera nowy zakres.  
  
 Filtr polecenia używane w pozostałej części usługi języka można również automatycznego formatowania. Można też wyróżnić pasujących nawiasów klamrowych, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)