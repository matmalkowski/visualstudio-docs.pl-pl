---
title: Getvstosolutionmetadata — funkcja
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
ms.openlocfilehash: e6289a0d19bc6621d98edfc974ad265791876a70
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677605"
---
# <a name="getvstosolutionmetadata-function"></a>Getvstosolutionmetadata — funkcja
  Ten interfejs API obsługuje infrastrukturę pakietu Office i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|Nie należy używać.|  
|*ppSolutionInfo*|Nie należy używać.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja się powiedzie, zwraca **S_OK**. Jeśli funkcja zawiedzie, zwraca kod błędu.  
  
  