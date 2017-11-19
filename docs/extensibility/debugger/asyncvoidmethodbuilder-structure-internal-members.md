---
title: "Struktura AsyncVoidMethodBuilder — wewnętrzne elementy członkowskie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e2a8b9f7e287ccf8bc63a8d7392cba0d58cb9bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Struktura AsyncVoidMethodBuilder — wewnętrzne elementy członkowskie
W tym temacie opisano wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> klasy. Aby uzyskać ogólne informacje o tej klasy, zobacz <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> temat referencyjny.  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z programu .NET Framework, następującej składni podano języka wspólnego pośredniego (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Wewnętrzne elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Właściwość ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Pobiera obiekt, który może być używany do jednoznacznego identyfikowania tego konstruktora do debugera.|  
|[pole m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Reprezentuje obiekt opóźnieniem zainicjowane używany przez debuger do jednoznacznego identyfikowania tego konstruktora.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Wewnętrzne rozszerzenia równoległe dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)