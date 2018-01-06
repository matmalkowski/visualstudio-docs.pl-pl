---
title: IDebugProperty3::CreateObjectID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::CreateObjectID
helpviewer_keywords: IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 337e1a4025e71a637e73b258df41828b7ddf1f43
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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