---
title: "Debuger kontekstów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 809f0f50ace62253371d4fd14425bb870a3be633
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="debugger-contexts"></a>Konteksty debugera
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania, aparat debugowania (DE) działa jednocześnie w kilku różnych kontekstach, w następujący sposób:  
  
-   Kontekst kodu, który opisuje bieżącej lokalizacji w strumieniu wykonywania programu.  
  
-   Kontekst dokumentacji lub pozycji, które opisano bieżącą pozycję w dokumencie źródłowym.  
  
-   Kontekst oceny wyrażenia, który opisuje kontekst, w którym wyrażenie oceny będą miały miejsce.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontekst kodu](../../extensibility/debugger/code-context.md)  
 W tym artykule omówiono kontekst kodu jako adresu w strumieniu instrukcji programu w bieżącej środowiska wykonawczego architektury i nietradycyjnych języków, gdy kodu nie może być reprezentowany przez instrukcje, ale w inny sposób.  
  
 [Położenie dokumentu](../../extensibility/debugger/document-position.md)  
 Definiuje położenie dokumentu w Visual Studio debugowanie za pomocą abstrakcję pozycji w pliku źródłowym, ponieważ znana IDE.  
  
 [Kontekstu dokumentu](../../extensibility/debugger/document-context.md)  
 W tym artykule omówiono jakie kontekstu dokumentu reprezentuje w Visual Studio debugowanie w odniesieniu do pliku źródłowego. Omówiono także sposób obsługi symbol mapowania kontekst kodu dokumentacji kontekstu.  
  
 [Kontekst oceny wyrażenia](../../extensibility/debugger/expression-evaluation-context.md)  
 Zawiera informacje dotyczące kontekstu oceny wyrażenia w Visual Studio. Na przykład kontekst oceny wyrażenia ramki stosu udostępnia kontekst oceny zmiennych lokalnych, parametrów metod i elementów członkowskich klasy.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugowania](../../extensibility/debugger/debugger-concepts.md)  
 Zawiera opis głównych pojęć architektury debugowania.  
  
 [Składniki debugowania](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie składników debugowania programu Visual Studio, które obejmują aparat debugowania (DE), Ewaluator wyrażeń (EE) i obsługi symboli (SH).  
  
 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera łącza do różnych zadań debugowania, takie jak uruchamianie programu i obliczaniu wyrażeń.