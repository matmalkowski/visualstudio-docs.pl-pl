---
title: Interfejs IDebugHelper | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f0f70ecb8ead264d0d4b074f8fc1d9e3a6091eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelper-interface"></a>Interfejs IDebugHelper
Służy jako fabryki dla obiekt przeglądarki i punkty połączenia proste. Menedżer debugowania procesu (PDM) implementuje ten interfejs, który jest używany przez aparaty skryptów.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugHelper` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Zwraca właściwości przeglądarki, która opakowuje VARIANT.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Zwraca przeglądarki właściwość, która opakowuje wariant i umożliwia konwersji niestandardowej wartości z WARIANTU lub typów VARTYPE na ciągi.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Zwraca interfejs zdarzeń, który opakowuje danego `IDispatch` obiektu.|