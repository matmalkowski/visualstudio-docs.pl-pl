---
title: "&lt;Harmonogramy&gt; elementu (programu inicjującego) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: "5"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 104c187d373113e8e5dafe589af3995bef5c8cdc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Harmonogramy&gt; elementu (programu inicjującego)
`Schedules` Element zawiera `Schedule` elementów, które definiują określonych godzinach, na które polecenia zdefiniowane przez `Command` element powinien zostać uruchomiony.  
  
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
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `Schedules` Element jest elementem podrzędnym `Product` elementu. Każdy `Product` element może mieć co najwyżej jeden `Schedules` elementu. `Schedules` Element nie ma żadnych atrybutów.  
  
## <a name="schedule"></a>Harmonogram  
 `Schedule` Element jest elementem podrzędnym `Schedules` elementu. A `Schedules` element musi mieć co najmniej jeden `Schedule` elementu.  
  
 `Schedule`ma następującego atrybutu.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Nazwa elementu harmonogramu. Odpowiada to `ScheduleName` właściwość `Command` elementu. Gdy `Command` odwołuje się do nazwanych harmonogramu, będą wykonywane tylko o godzinie określonej przez tę `Schedule` elementu. Harmonogramy również mogą być skojarzone z `FailIf` i `BypassIf` elementów, które ograniczyć te testy warunkowe do wykonywania zgodnie z określonym harmonogramem. Aby uzyskać więcej informacji, zobacz [ \<polecenia > elementu](../deployment/commands-element-bootstrapper.md).|  
  
 Biorąc pod uwagę `Schedule` element może mieć dokładnie jeden z następujących elementów podrzędnych.  
  
## <a name="buildlist"></a>BuildList  
 `BuildList` Elementu powoduje, że Instalator do wykonania polecenia, natychmiast po uruchomieniu aplikacji bootstrapping.  
  
## <a name="beforepackage"></a>BeforePackage  
 `BeforePackage` Elementu powoduje, że Instalator do wykonania polecenia, przed zainstalowaniem określonego pakietu.  
  
## <a name="afterpackage"></a>AfterPackage  
 `AfterPackage` Elementu powoduje, że Instalator do wykonania polecenia, po zainstalowaniu określonego pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Produktu > — Element](../deployment/product-element-bootstrapper.md)   
 [Produkt i pakiet — odwołanie do schematu](../deployment/product-and-package-schema-reference.md)