---
title: Kontekst dokumentów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f97df9bc3c0a40a44379ba37f1b36d79cffb74e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098748"
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