---
title: m_children pola | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 59848b177b4bfaccba2d5f2e5771a08ec0bc060a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mchildren-field"></a>m_children pola
Lista zadania podrzędne, które są zarejestrowane przy użyciu tego zadania.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z programu .NET Framework, następującej składni podano języka wspólnego pośredniego (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Uwagi  
 Po uruchomieniu zadania tylko wątek, który wykonuje zadanie powinien uzyskiwać dostęp do tej tablicy.  
  
 Jeśli zadanie zostało ukończone, inne wątki mają dostęp do tego pola tak długo, jak nie wszystko dodać do niego lub Usuń wszystko z niego.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)