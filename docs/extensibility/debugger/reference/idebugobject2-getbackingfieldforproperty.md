---
title: IDebugObject2::GetBackingFieldForProperty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords: IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f8833e3d2b686e1c350e1094aaa9bdfe925586a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Pobiera pola lub zmiennej (jeśli istnieją) mogą który kopii właściwości reprezentowany przez ten obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) Obiekt opisujący pola zapasowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) obiekt reprezentuje właściwość klasy kodu zarządzanego, czyli metody pobieranie i/lub akcesor zestawu. Takie właściwości wymagają zmiennej, aby zawierał wartość manipulować przez właściwość. Ta zmienna jest określany jako pola zapasowego. Jeśli nie żadne pole zapasowe dla obiekt, następnie upewnij się zwrócić wartość null: niektóre obiekty wywołujące nie może zwrócić uwagę na wartość zwrotną, ale zamiast tego będzie wyglądać aby zobaczyć, jeśli wartość null została zwrócona w `ppObject`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)