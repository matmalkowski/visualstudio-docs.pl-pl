---
title: ButtonText, Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8ba4667a34594c764a57788ee468d32733ded8e
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232016"
---
# <a name="buttontext-element"></a>ButtonText, element
To pole pozwala określić tekst, który pojawia się w różnych menu. Domyślnie `ButtonText` element jest wyświetlany w menu kontrolerów. `ButtonText` Element staje się również wartość domyślna Jeśli inne pola tekstowe są puste. `ButtonText` Element nie może być pusta, nawet jeśli inne pola tekstowe są określone.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Strings, element](../extensibility/strings-element.md)|Grupuje elementy tekstu, takie jak `ButtonText` i `CommandName`.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa elementu `ButtonText` element zawiera tekst, który jest wyświetlany dla elementów menu, combos i inne elementy interfejsu użytkownika, które mają widocznego tekstu.  
  
## <a name="see-also"></a>Zobacz także  
 [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)