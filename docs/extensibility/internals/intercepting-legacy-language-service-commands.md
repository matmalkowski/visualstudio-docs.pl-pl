---
title: "Przechwytywaniu polecenia usługi języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73524ce47dfea2d30e44e51e97bf584a95a86482
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="intercepting-legacy-language-service-commands"></a>Przechwytywaniu polecenia usługi języka starsza wersja
Z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], może mieć polecenia intercept usługi języka, które widoku tekstu może obsłużyć w inny sposób. Pozwala to na zachowanie specyficzne dla języka, które nie zarządza widoku tekstu. Można przechwycić tych poleceń, dodając co najmniej jeden filtr polecenia do widoku tekstu z usługi języka.  
  
## <a name="getting-and-routing-the-command"></a>Pobieranie i Routing poleceń  
 Filtr polecenia jest <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt, który monitoruje niektórych sekwencje znaków lub klucza poleceń. Z widoku jeden tekst można skojarzyć więcej niż jeden filtr polecenia. Każdy widok tekstu zachowuje filtry służbowej. Po utworzeniu nowego filtru polecenia, możesz dodać filtr w łańcuchu widoku odpowiedni tekst.  
  
 Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> można dodać filtru polecenia w łańcuchu. Podczas wywoływania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zwraca inny filtr polecenia, do którego można przekazać poleceń, które nie obsługuje polecenia filtru.  
  
 Masz następujące opcje obsługi polecenia:  
  
-   Obsługa polecenia, a następnie przekazać polecenia do następnego polecenia Filtr w łańcuchu.  
  
-   Obsługa polecenia i nie są przekazywane do polecenia do następnego polecenia Filtr.  
  
-   Nie obsługują polecenia, ale polecenia do następnego filtru polecenia zostały spełnione.  
  
-   Ignoruj polecenia. Nie obsługują w bieżący filtr, a nie są przekazywane do następnego filtru.  
  
 Aby uzyskać informacje dotyczące polecenia usługi języka powinna obsługiwać, zobacz [ważne poleceń dla filtrów usługi języka](../../extensibility/internals/important-commands-for-language-service-filters.md).