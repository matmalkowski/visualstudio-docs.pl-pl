---
title: IPropertyProxyEESide::InPlaceUpdateObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords: IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 723a24a0a0ce21c7817b5dfcef2680808f9319a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aktualizuje dane obiektu z danych danego obiektu i zwraca obiekt danych reprezentujący danych nowego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dataIn`  
 [in] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiektu zawierającego nowe dane.  
  
 `dataOut`  
 [out] Zwraca nowy `IEEDataStorage` obiektu zawierającego dane zastąpiona.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda aktualizacji faktycznie danych obiektu. Dane w zwróconym [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiektu musi być taka sama, jak dane w przychodzącej `IEEDataStorage` obiekt, ale zwracany obiekt musi odpowiadać bieżącej wartości właściwości.  
  
 Przychodzące obiekt danych nie jest zwykle implementowany przez EE. Jednak obiektu zwróconego przez tę metodę zawsze jest implementowany przez EE, który umożliwia wdrożenie EE `IEEDataStorage` interfejs na potrzeby niezależnie od klasy.  
  
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) metoda tworzy obiekt danych oparte na obiekt danych przychodzących, ale nie ma wpływu na właściwości oryginalnych danych.  
  
## <a name="see-also"></a>Zobacz też  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)