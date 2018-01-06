---
title: "Kontekst dokumentów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b121259f9be23d235386d7156ca8d326c5847f87
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="document-context"></a>Kontekstu dokumentu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania, **kontekstu dokumentu**:  
  
-   Reprezentuje pozycji w pliku źródłowym. W przypadku języków, gdy plik źródłowy może nie być obecny kontekstu dokumentu identyfikuje pozycji w dokumencie zwykle generowane przez środowisko wykonawcze. Na przykład aparat skryptów może generować dokumentu ze skryptu. Aby uzyskać więcej informacji, zobacz [położenie dokumentu](../../extensibility/debugger/document-position.md).  
  
-   W tym artykule opisano pozycji w dokumencie źródłowym, który odpowiada kontekst kodu. Program obsługi symbol mapuje kontekst kodu kontekst dokumentację, korzystając z informacji generowanych przez kompilator lub interpreter.  
  
-   Jest implementowany przez [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontekst kodu](../../extensibility/debugger/code-context.md)   
 [Dostawca — symbol](../../extensibility/debugger/symbol-provider.md)   
 [Symbol dostawcy interfejsów](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)