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
ms.workload: multiple
ms.openlocfilehash: 527ab7ae43790f7e824ead33fb601f0f8dee2bf0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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