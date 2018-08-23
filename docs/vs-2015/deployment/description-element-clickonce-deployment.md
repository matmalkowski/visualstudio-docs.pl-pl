---
title: '&lt;Opis&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 473ebf814ab65c34ee99cab0cf2cc239e0d013eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42627730"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Opis&gt; — Element (wdrażanie ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ &lt;opis&gt; — Element (wdrażanie ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/description-element-clickonce-deployment).  
  
Określa informacje o aplikacji, które pozwala utworzyć obecności powłoki i **apletu Dodaj lub usuń programy** w Panelu sterowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `description` Element jest wymagany i znajduje się w `urn:schemas-microsoft-com:asm.v1` przestrzeni nazw. Go nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`publisher`|Wymagane. Określa nazwę firmy, używane do umieszczenia ikony w Windows **Start** menu i **apletu Dodaj lub usuń programy** w Panelu sterowania, gdy wdrożenie jest skonfigurowane do instalacji.|  
|`product`|Wymagane. Identyfikuje Pełna nazwa produktu. Używane jako tytuł na ikonę zainstalowane w Windows **Start** menu.|  
|`suiteName`|Opcjonalna. Identyfikuje podfolder w `publisher` folderu w Windows **Start** menu.|  
|`supportUrl`|Opcjonalna. Określa adres URL pomocy technicznej, która jest wyświetlana w **apletu Dodaj lub usuń programy** w Panelu sterowania. Skrót do tego adresu URL tworzona jest również obsługę aplikacji w Windows **Start** menu, gdy wdrożenie jest skonfigurowane do instalacji.|  
  
## <a name="remarks"></a>Uwagi  
 Opis elementu jest wymagany we wszystkich konfiguracjach wdrażania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano `description` element [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest wdrożenia. Ten przykład kodu jest częścią większego przykładu przewidzianego dla [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) tematu.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)



