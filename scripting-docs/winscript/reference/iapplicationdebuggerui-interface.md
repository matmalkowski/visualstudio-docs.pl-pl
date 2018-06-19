---
title: Interfejs IApplicationDebuggerUI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbaa04f6790ffc4d80447a6745ca82cc8dba6802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793669"
---
# <a name="iapplicationdebuggerui-interface"></a>Interfejs IApplicationDebuggerUI
Implementowany przez debuger zintegrowane środowisko programistyczne (IDE) (oprócz `IApplicationDebugger`) umożliwiają składnik zewnętrzny większą kontrolę nad interfejsu użytkownika (UI) debugera.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IApplicationDebuggerUI` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Udostępnia interfejs użytkownika okna zawierającego dokument określony debugowania do góry w debugerze.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Wywołuje okno zawierające kontekst danego dokumentu do góry w interfejsie użytkownika debugera i przewijania okna w kontekście.|