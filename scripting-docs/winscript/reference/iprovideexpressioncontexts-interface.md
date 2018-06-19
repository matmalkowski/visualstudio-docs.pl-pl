---
title: Interfejs IProvideExpressionContexts | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 402b439da6f1fa369accacb27f987ac77119e343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794584"
---
# <a name="iprovideexpressioncontexts-interface"></a>Interfejs IProvideExpressionContexts
Umożliwia wyliczenie znane przez składnik niektórych kontekstach wyrażenia. Liczba aparatów skryptów zwykle implementuje ten interfejs.  
  
 Menedżer debugowania procesu używa tego interfejsu można znaleźć wszystkie konteksty wyrażenia globalnego skojarzone z danym wątku.  
  
> [!NOTE]
>  Ten interfejs jest wywoływana z w wątku zainteresowań. Jest czynności, aby zidentyfikować bieżącego wątku i zwraca moduł wyliczający odpowiednie.  
  
## <a name="methods"></a>Metody  
 Oprócz dziedziczone z metody `IUnknown`, `IProvideExpressionContexts` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Zwraca moduł wyliczający kontekstów wyrażenie znane przez ten składnik.|