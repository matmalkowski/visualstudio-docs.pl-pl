---
title: "Klasa ContingentProperties — wewnętrzne elementy członkowskie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e1bd9c94b99b4881167d7ae434691ffd08666ced
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="contingentproperties-class---internal-members"></a>Klasa ContingentProperties — wewnętrzne elementy członkowskie
Zawiera dodatkowe właściwości <xref:System.Threading.Tasks.Task> obiektu.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tych wewnętrznych elementów członkowskich z programu .NET Framework, następującej składni podano języka wspólnego pośredniego (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="fields"></a>Pola  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|Lista zadania podrzędne, które są zarejestrowane przy użyciu tego zadania.|  
  
## <a name="remarks"></a>Uwagi  
 .NET Framework inicjuje pola tej klasy, tylko wtedy, gdy są potrzebne.  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)