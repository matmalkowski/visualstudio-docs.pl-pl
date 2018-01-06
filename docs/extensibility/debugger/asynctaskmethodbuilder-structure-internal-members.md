---
title: "Struktura AsyncTaskMethodBuilder — wewnętrzne elementy członkowskie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 763f06d03eff79d82096bc2b5eb3046fe05f7aca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Struktura AsyncTaskMethodBuilder — wewnętrzne elementy członkowskie
W tym temacie opisano wewnętrzne elementy członkowskie <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> klasy. Aby uzyskać ogólne informacje o tej klasy, zobacz <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> temat referencyjny.  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z programu .NET Framework, następującej składni podano języka wspólnego pośredniego (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Wewnętrzne elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Właściwość ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Pobiera obiekt, który może być używany do jednoznacznego identyfikowania tego konstruktora do debugera.|  
|[pole m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Reprezentuje obiekt ogólnego konstruktora, do którego deleguje tego wystąpienia inny niż ogólny.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)