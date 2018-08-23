---
title: '&lt;Harmonogramy&gt; — Element (program inicjujący) | Dokumentacja firmy Microsoft'
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
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c72ee64bcc174bcd11d800bbc8dd0e1b9848b746
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680073"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Harmonogramy&gt; — Element (program inicjujący)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [ &lt;harmonogramy&gt; — Element (program inicjujący)](https://docs.microsoft.com/visualstudio/deployment/schedules-element-bootstrapper).  
  
`Schedules` Element zawiera `Schedule` elementów, które definiują określonych godzinach, w której polecenia zdefiniowane przez `Command` element powinien być uruchamiany.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `Schedules` Element jest elementem podrzędnym `Product` elementu. Każdy `Product` element może mieć co najwyżej jeden `Schedules` elementu. `Schedules` Element nie ma żadnych atrybutów.  
  
## <a name="schedule"></a>Harmonogram  
 `Schedule` Element jest elementem podrzędnym `Schedules` elementu. A `Schedules` element musi mieć co najmniej jeden `Schedule` elementu.  
  
 `Schedule` ma następujący atrybut.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagane. Nazwa elementu harmonogramu. Odpowiada to `ScheduleName` właściwość `Command` elementu. Gdy `Command` odwołuje się do harmonogramu o nazwie zostanie wykonana tylko o godzinie określonej przez to `Schedule` elementu. Harmonogramy, również mogą być skojarzone z `FailIf` i `BypassIf` elementów, które ograniczają tych testów warunkowych do wykonywania zgodnie z określonym harmonogramem. Aby uzyskać więcej informacji, zobacz [ \<polecenia > Element](../deployment/commands-element-bootstrapper.md).|  
  
 Biorąc pod uwagę `Schedule` element może mieć dokładnie jeden z następujących elementów podrzędnych.  
  
## <a name="buildlist"></a>BuildList  
 `BuildList` Element Instruuje Instalatora Aby wykonać polecenie natychmiast, po uruchomieniu bootstrapping aplikacji.  
  
## <a name="beforepackage"></a>BeforePackage  
 `BeforePackage` Element Instruuje Instalatora Aby wykonać polecenie przed zainstalowaniem określonego pakietu.  
  
## <a name="afterpackage"></a>AfterPackage  
 `AfterPackage` Element Instruuje Instalatora aby wykonywanie polecenia po zainstalowaniu określonego pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Produktu > Element](../deployment/product-element-bootstrapper.md)   
 [Produkt i pakiet — dokumentacja schematu](../deployment/product-and-package-schema-reference.md)



