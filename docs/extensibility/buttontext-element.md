---
title: ButtonText Element | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b17492b0cc8531ac892bf8ead1c309f403d1da48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="buttontext-element"></a>ButtonText Element
To pole umożliwia określenie tekstu wyświetlanego w różnych menu. Domyślnie `ButtonText` element jest wyświetlany w menu kontrolerów. `ButtonText` Element staje się również domyślnie Jeśli pola tekstowe są puste. `ButtonText` Element nie może być pusta, nawet jeśli nie określono innych pól tekstowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|[Element ciągów](../extensibility/strings-element.md)|Grupuje elementy tekstu, takich jak `ButtonText` i `CommandName`.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstu `ButtonText` element zawiera tekst, który jest wyświetlany dla elementów menu, kombinacje i inne elementy interfejsu użytkownika, zawierających tekst wyświetlany.  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)