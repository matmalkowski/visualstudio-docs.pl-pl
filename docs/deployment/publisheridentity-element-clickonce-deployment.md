---
title: "&lt;publisheridentity —&gt; — Element (wdrażania ClickOnce) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 9a59b97b3260beaf39ae20b62a44903add13e622
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
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
|`name`|Wymagany. Opisuje tożsamości strony, która wydała tej aplikacji.|  
|`issuerKeyHash`|Wymagany. Zawiera skrótu SHA-1 wystawcy certyfikatu klucza publicznego.|  
  
#### <a name="parameters"></a>Parametry  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="subhead"></a>Podnagłówek