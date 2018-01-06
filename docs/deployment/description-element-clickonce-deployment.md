---
title: "&lt;Opis elementu&gt; elementu (wdrażania ClickOnce) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: "19"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: f5045f9203d5413efdd6d192d2667e94d0119220
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Opis elementu&gt; elementu (wdrażania ClickOnce)
Określa informacje o aplikacji, które pozwala utworzyć obecności powłoki i **Dodaj lub usuń programy** w Panelu sterowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `description` Element jest wymagany i znajduje się w `urn:schemas-microsoft-com:asm.v1` przestrzeni nazw. Nie zawiera żadnych elementów podrzędnych i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`publisher`|Wymagany. Określa nazwę firmy, użyty do umieszczenia ikonę w oknach **Start** menu i **Dodaj lub usuń programy** w Panelu sterowania, gdy wdrożenie jest skonfigurowane do instalacji.|  
|`product`|Wymagany. Identyfikuje Pełna nazwa produktu. Używane jako tytuł ikony zainstalowane w systemie Windows **Start** menu.|  
|`suiteName`|Opcjonalny. Identyfikuje podfolder w `publisher` folderu w oknach **Start** menu.|  
|`supportUrl`|Opcjonalny. Określa adres URL pomocy technicznej, który jest wyświetlany w obszarze **Dodaj lub usuń programy** w Panelu sterowania. Skrót do tego adresu URL tworzona jest również obsługę aplikacji w oknach **Start** menu, gdy wdrożenie jest skonfigurowane do instalacji.|  
  
## <a name="remarks"></a>Uwagi  
 Opis elementu jest wymagany w wszystkie konfiguracje wdrożenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `description` element [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest wdrażania. Ten przykładowy kod jest częścią większego przykładu udostępnionego dla [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) tematu.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)