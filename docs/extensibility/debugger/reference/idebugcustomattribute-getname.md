---
title: IDebugCustomAttribute::GetName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a33b4507cb54095a38671eaf310d87dae180be6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Pobiera nazwę atrybutu niestandardowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrName`  
 [out] Zwraca ciąg zawierający nazwę atrybutu niestandardowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zwracany przez tę metodę o nazwie odpowiada nazwie klasy użyć do zadeklarowania atrybutu. Może nie dokładnie odpowiadać nazwę klasy atrybutu niestandardowego sam jak C# pozwala sufiksem "Atrybutu", aby porzucić na podstawie nazwy atrybutów niestandardowych, gdy jest używany w deklaracji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)