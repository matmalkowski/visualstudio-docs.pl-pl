---
title: '&lt;customErrorReporting&gt; elementu (wdrażania ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41ade854a37127443735e1c197c080aad3d5bd93
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; elementu (wdrażania ClickOnce)
Określa identyfikator URI do wyświetlenia, gdy wystąpi błąd.  
  
## <a name="syntax"></a>Składnia  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten element jest opcjonalny. Bez tego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Wyświetla okno dialogowe błędu przedstawiający stosu wyjątku. Jeśli `customErrorReporting` element jest obecny, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zamiast tego zostanie wyświetlona wskazywanym przez identyfikator URI `uri` parametru. Docelowy identyfikator URI zawiera klasy Wyjątek zewnętrzny, wewnętrzny wyjątek klasy i komunikat wyjątku wewnętrznego jako parametry.  
  
 Ten element umożliwia dodawanie raportów o błędach funkcje do aplikacji. Ponieważ wygenerowany identyfikator URI zawiera informacje o typie błędu, witryny sieci Web można analizować tych informacji i wyświetlania, na przykład odpowiednie ekranu rozwiązywania problemów.  
  
## <a name="example"></a>Przykład  
 Poniższy fragment kodu przedstawia `customErrorReporting` element wraz z wygenerowanego identyfikatora URI może powodować generowanie.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)