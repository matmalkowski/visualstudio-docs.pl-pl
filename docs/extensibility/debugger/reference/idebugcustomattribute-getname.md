---
title: IDebugCustomAttribute::GetName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetName
helpviewer_keywords: IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 165362ab03685a3acca457e4095778b9dcb182e8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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