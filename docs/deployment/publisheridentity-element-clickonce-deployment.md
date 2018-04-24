---
title: '&lt;publisheridentity —&gt; — Element (wdrażania ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ad10cae4ebd3aee6b65ad408ea3a3df3f82fd02
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisheridentity —&gt; — Element (wdrażania ClickOnce)
Zawiera informacje o wydawcy, który podpisał tego manifestu wdrożenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `publisherIdentity` Element jest wymagany dla podpisanych manifestów. W poniższej tabeli przedstawiono atrybuty `publisherIdentity` obsługuje elementu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Wymagana. Opisuje tożsamości strony, która wydała tej aplikacji.|  
|`issuerKeyHash`|Wymagana. Zawiera skrótu SHA-1 wystawcy certyfikatu klucza publicznego.|  
  
#### <a name="parameters"></a>Parametry  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="subhead"></a>Podnagłówek