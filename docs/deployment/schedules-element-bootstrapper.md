---
title: '&lt;Harmonogramy&gt; elementu (programu inicjującego) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c551bc9335dc41f82800e2c3435d8508967a6db
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815473"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Harmonogramy&gt; elementu (programu inicjującego)
`Schedules` Element zawiera `Schedule` elementów, które definiują określonych godzinach, na które polecenia zdefiniowane przez `Command` element powinien zostać uruchomiony.  
  
## <a name="syntax"></a>Składnia  
  
```xml
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
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `Schedules` Element jest elementem podrzędnym `Product` elementu. Każdy `Product` element może mieć co najwyżej jeden `Schedules` elementu. `Schedules` Element nie ma żadnych atrybutów.  
  
## <a name="schedule"></a>Harmonogram  
 `Schedule` Element jest elementem podrzędnym `Schedules` elementu. A `Schedules` element musi mieć co najmniej jeden `Schedule` elementu.  
  
 `Schedule` ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagana. Nazwa elementu harmonogramu. Odpowiada to `ScheduleName` właściwość `Command` elementu. Gdy `Command` odwołuje się do nazwanych harmonogramu, będą wykonywane tylko o godzinie określonej przez tę `Schedule` elementu. Harmonogramy również mogą być skojarzone z `FailIf` i `BypassIf` elementów, które ograniczyć te testy warunkowe do wykonywania zgodnie z określonym harmonogramem. Aby uzyskać więcej informacji, zobacz [ \<polecenia > elementu](../deployment/commands-element-bootstrapper.md).|  
  
 Biorąc pod uwagę `Schedule` element może mieć dokładnie jeden z następujących elementów podrzędnych.  
  
## <a name="buildlist"></a>BuildList  
 `BuildList` Elementu powoduje, że Instalator do wykonania polecenia, natychmiast po uruchomieniu aplikacji bootstrapping.  
  
## <a name="beforepackage"></a>BeforePackage  
 `BeforePackage` Elementu powoduje, że Instalator do wykonania polecenia, przed zainstalowaniem określonego pakietu.  
  
## <a name="afterpackage"></a>AfterPackage  
 `AfterPackage` Elementu powoduje, że Instalator do wykonania polecenia, po zainstalowaniu określonego pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Produktu > — Element](../deployment/product-element-bootstrapper.md)   
 [Produkt i pakiet — dokumentacja schematu](../deployment/product-and-package-schema-reference.md)