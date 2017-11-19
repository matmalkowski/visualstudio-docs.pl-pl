---
title: IDebugProgramNodeAttach2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNodeAttach2
helpviewer_keywords: IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 604518d30b2bf03c357787e1bfad1f9c90c6766c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Umożliwia węzła program ma być powiadamiany o podjęto próbę dołączenia do skojarzonego programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest wdrażany na tej samej klasy, która implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu, aby otrzymać powiadomienie o operacji dołączania i aby zapewnić możliwość anulowania operacji dołączania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskanie przez wywołanie metody tego interfejsu `QueryInterface` metody w [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiektu. [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metoda musi zostać wywołana przed [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody na umożliwieniu węzła programu można zatrzymać procesu dołączania.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Dołącza do skojarzonego programu lub różni się proces attach [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest preferowanym zamiast przestarzałych [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) metody. Wszelkie aparatami debugowania zawsze są ładowane z `CoCreateInstance` działać, oznacza to, czy wystąpienia poza przestrzeni adresowej debugowany program.  
  
 Jeśli poprzedniej implementacji `IDebugProgramNode2::Attach_V7` metoda po prostu ustawiał `GUID` programu debugowany, następnie tylko [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) — metoda musi zostać wdrożone.  
  
 Jeśli poprzedniej implementacji `IDebugProgramNode2::Attach_V7` metodę interfejsu wywołania zwrotnego, który został dostarczony, a następnie funkcja musi być przeniesiona do wykonania [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) — metoda i `IDebugProgramNodeAttach2` nie obsługuje interfejsu muszą być wykonywane.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)