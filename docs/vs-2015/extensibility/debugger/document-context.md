---
title: Kontekst dokumentu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a9e92976af5e098dca0d1a4bb81c777eb38a9f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679223"
---
# <a name="document-context"></a>Kontekst dokumentu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [kontekstu dokumentu](https://docs.microsoft.com/visualstudio/extensibility/debugger/document-context).  
  
W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowania **kontekstu dokumentu**:  
  
-   Reprezentuje pozycji w pliku źródłowym. W przypadku języków, gdzie plik źródłowy nie może być obecny kontekstu dokumentu identyfikuje pozycji w dokumencie, zwykle generowane przez środowisko wykonawcze. Na przykład aparat skryptów może generować dokumentu ze skryptu. Aby uzyskać więcej informacji, zobacz [położenie dokumentu](../../extensibility/debugger/document-position.md).  
  
-   W tym artykule opisano pozycji w dokumencie źródłowym, który odnosi się do kontekstu kodu. Procedury obsługi symboli mapuje kontekst kodu kontekst dokumentację, korzystając z informacji generowanych przez kompilator lub interpretera.  
  
-   Jest implementowana przez [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontekst kodu](../../extensibility/debugger/code-context.md)   
 [Dostawca symboli](../../extensibility/debugger/symbol-provider.md)   
 [Interfejsy dostawca symboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)

