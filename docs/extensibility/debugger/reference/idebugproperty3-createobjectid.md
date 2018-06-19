---
title: IDebugProperty3::CreateObjectID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df4e45c442745652b3305fd91146bd31ffe79e4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120978"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Tworzy unikatowy identyfikator dla tej właściwości, aby upewnić się, że jest unikatowa wśród innych właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana, gdy chce upewnij się, że ta właściwość jest unikatowo identyfikowana wśród innych właściwości Menedżera sesji debugowania. Aparat debugowania (DE) obsługuje tę metodę, chyba że właściwości, który zajmuje się są już unikatowo identyfikowane. Jeśli DE nie obsługuje tej metody, zwraca `E_NOTIMPL`.  
  
 Wszelkie Unikatowy identyfikator utworzone za pomocą `CreateObjectID` zostanie zniszczony po [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) metoda jest wywoływana; to również sygnalizuje koniec potrzebę jednoznacznego zidentyfikowania tej właściwości.  
  
> [!NOTE]
>  Nie istnieje metoda pobierze ten unikatowy identyfikator, tak więc DE można zrobić, niezależnie od chce unikatowych identyfikatorów podczas `CreateObjectID` metoda jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)