---
title: IDebugProgramNodeAttach2::OnAttach | Dokumentacja firmy Microsoft
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
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73e81537ce73a5b7677174d4694ece16a2a823b7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678172"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugProgramNodeAttach2::OnAttach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnodeattach2-onattach).  
  
Dołącza do skojarzonego programu lub procesu dołączania do odracza [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidProgramId`  
 [in] `GUID` można przypisać do skojarzonego programu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) nie powinna być wywoływana metoda. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana podczas procesu dołączania przed [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metoda jest wywoływana. `OnAttach` Metodę można wykonać sam proces attach (w którym to przypadku ta metoda zwraca `S_FALSE`) lub Odrocz procesu dołączania do `IDebugEngine2::Attach` — metoda ( `OnAttach` metoda zwraca `S_OK`). W obu przypadkach `OnAttach` metody można ustawić `GUID` programu debugowania do danego `GUID`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)

