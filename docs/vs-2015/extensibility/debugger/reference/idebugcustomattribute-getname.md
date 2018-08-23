---
title: IDebugCustomAttribute::GetName | Dokumentacja firmy Microsoft
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
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b2ffd2c4159962369fb2883321015065421bce1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678607"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugCustomAttribute::GetName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcustomattribute-getname).  
  
Pobiera nazwę atrybutu niestandardowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zwracany przez tę metodę o nazwie odpowiada nazwie klasy używane do deklarowania atrybutu. Może nie dokładnie odpowiadać Nazwa klasy atrybutów niestandardowych, sama jak C# umożliwia sufiks "Atrybutu", który będzie można usunąć z nazwy atrybutu niestandardowego, gdy jest używany w deklaracji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

