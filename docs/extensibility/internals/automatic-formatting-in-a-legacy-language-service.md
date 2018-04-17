---
title: Automatyczne formatowanie starsza wersja usługi języka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e052c62afcf9551cc54373da15071fb3903fe950
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Automatyczne formatowanie starsza wersja usługi języka
Z automatycznego formatowania usługi języka automatycznie wstawia fragment kodu, gdy użytkownik rozpoczyna wpisz konstrukcję kodu znane.  
  
## <a name="automatic-formatting-behavior"></a>Zachowanie automatyczne formatowanie  
 Na przykład po wpisaniu `if`, usługa języka automatycznie wstawia pasujących nawiasów klamrowych lub po naciśnięciu klawisza ENTER usługi języka wymusza punkt wstawiania w nowym wierszu poziomu wcięcia odpowiednie, w zależności od tego, czy poprzednie wiersz otwiera nowy zakres.  
  
 Filtr polecenia używane w pozostałej części usługi języka można również automatycznego formatowania. Można też wyróżnić pasujących nawiasów klamrowych, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)