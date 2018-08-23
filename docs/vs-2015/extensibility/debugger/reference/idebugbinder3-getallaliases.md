---
title: IDebugBinder3::GetAllAliases | Dokumentacja firmy Microsoft
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
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e88ed8a93d77910d76cefefc0ee97c01f88de15b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684694"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugBinder3::GetAllAliases](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder3-getallaliases).  
  
Ta metoda pobiera listę aliasów w ramach programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `uRequest`  
 [in] Maksymalną liczbę aliasów do zwrócenia (określa długość tablicy przekazane do `ppAliases`).  
  
 `ppAliases`  
 [out w] Tablica do wypełnienia przy użyciu aliasów (jeśli jest to wartość null i `uRequest` wynosi 0, liczba aliasy, które mogą zostać zwrócone zostaną zwrócone przez `puFetched`).  
  
 `puFetched`  
 [out] Zwraca liczbę aliasów uzyskany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)

