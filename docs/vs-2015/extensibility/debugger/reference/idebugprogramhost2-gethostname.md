---
title: IDebugProgramHost2::GetHostName | Dokumentacja firmy Microsoft
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
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 420a25be81a124c89bc4139d80ae881b1f519726
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681878"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugProgramHost2::GetHostName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramhost2-gethostname).  
  
Pobiera tytuł, przyjazną nazwę lub nazwę pliku procesu hostingu tego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwType`  
 [in] Wartość z zakresu od [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) wyliczenia.  
  
 `pbstrHostName`  
 [out] Zwraca nazwę żądanej procesu hostingu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 W Typowa implementacja tej metody `dwType` parametr jest ignorowany i zwracany jest przyjazną nazwę komputera hosta. Inną możliwą implementację służy do przekazywania `dwType` parametr do wywołania [gethostname —](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) metodę, aby uzyskać nazwę.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [Gethostname —](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

