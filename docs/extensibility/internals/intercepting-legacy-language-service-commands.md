---
title: Przechwytywaniu polecenia usługi języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38f025e9dab6f93d87660a59421cbd778c92165a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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