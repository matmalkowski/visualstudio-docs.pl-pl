---
title: IDebugPortSupplier3::CanPersistPorts | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f3799e4003edca0ce2722ad1365777f6be7e43c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684983"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugPortSupplier3::CanPersistPorts](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplier3-canpersistports).  
  
Ta metoda określa, czy dostawca portu można utrwalić portów (zapisując je na dysku) między wywołań debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli porty mogą zostać utrwalone, lub `S_FALSE` do wskazania, czy porty nie może zostać utrwalona.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli dostawcy portu można utrwalić portów, należy to zrobić, kiedy niszczony jest i ponownie załadować, gdy zostanie uruchomiony ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

