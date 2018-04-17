---
title: Debuger kontekstów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a9310512417ac0e24046a1b7bcc1fd92099fe98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
  
 [Kontekst dokumentu](../../extensibility/debugger/document-context.md)  
 W tym artykule omówiono jakie kontekstu dokumentu reprezentuje w Visual Studio debugowanie w odniesieniu do pliku źródłowego. Omówiono także sposób obsługi symbol mapowania kontekst kodu dokumentacji kontekstu.  
  
 [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md)  
 Zawiera informacje dotyczące kontekstu oceny wyrażenia w Visual Studio. Na przykład kontekst oceny wyrażenia ramki stosu udostępnia kontekst oceny zmiennych lokalnych, parametrów metod i elementów członkowskich klasy.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugowania](../../extensibility/debugger/debugger-concepts.md)  
 Zawiera opis głównych pojęć architektury debugowania.  
  
 [Składniki debugowania](../../extensibility/debugger/debugger-components.md)  
 Zawiera omówienie składników debugowania programu Visual Studio, które obejmują aparat debugowania (DE), Ewaluator wyrażeń (EE) i obsługi symboli (SH).  
  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)  
 Zawiera łącza do różnych zadań debugowania, takie jak uruchamianie programu i obliczaniu wyrażeń.