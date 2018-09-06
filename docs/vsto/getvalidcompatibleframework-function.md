---
title: Getvalidcompatibleframework — funkcja
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 18ef1d61d0e203744cc6436d884c37339a4a1ef0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676160"
---
# <a name="getvalidcompatibleframework-function"></a>Getvalidcompatibleframework — funkcja
  Ten interfejs API obsługuje infrastrukturę pakietu Office i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```csharp 
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
### <a name="parameters"></a>Parametry  
|Parametr|Opis|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Nie należy używać.|  
|*pbstrValidFrameworkTag*|Nie należy używać.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja się powiedzie, zwraca **S_OK**. Jeśli funkcja zawiedzie, zwraca kod błędu.  
  
  