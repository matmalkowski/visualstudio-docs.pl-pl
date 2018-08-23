---
title: '&lt;customErrorReporting&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 422ccaf8e82a2b1813bc876c76a6ff5a7c96f43c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682467"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; — Element (wdrażanie ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ &lt;customErrorReporting&gt; — Element (wdrażanie ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/customerrorreporting-element-clickonce-deployment).  
  
Określa identyfikator URI do wyświetlenia, gdy wystąpi błąd.  
  
## <a name="syntax"></a>Składnia  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten element jest opcjonalny. Bez tego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Wyświetla okno dialogowe błędu przedstawiający stos wyjątków. Jeśli `customErrorReporting` element jest obecny, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zamiast tego wyświetli wskazywanym przez identyfikator URI `uri` parametru. Docelowy identyfikator URI będzie zawierać klasy wewnętrzny wyjątek, komunikat wyjątku wewnętrznego i klasy wyjątków zewnętrzne jako parametry.  
  
 Ten element umożliwia dodawanie raportów o błędach funkcji do aplikacji. Ponieważ wygenerowanego identyfikatora URI zawiera informacje o typie błędu, witryny sieci Web można analizować tych informacji i ekran, na przykład odpowiednie ekranu rozwiązywania problemów.  
  
## <a name="example"></a>Przykład  
 Poniższy fragment kodu przedstawia `customErrorReporting` elementu, wraz z wygenerowanego identyfikatora URI może powodować generowanie.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)



