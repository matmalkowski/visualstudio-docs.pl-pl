---
title: Interfejs ISetNextStatement | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdd71a427a8ef2c57684eef75a044d0cedf42415
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796240"
---
# <a name="isetnextstatement-interface"></a>Interfejs ISetNextStatement
Ten interfejs jest implementowany przez tłumacza, aby umożliwić debugowanie Menedżera procesu aktualizacji bieżącej instrukcji. Jest implementowany z obiektu ramki stosu, a ten interfejs, za pomocą funkcji QueryInterface uzyskuje PDM.  
  
 Interfejs udostępnia metody, które są przydatne do ustawiania punkcie wykonanie, które określa następną instrukcję do wykonania.  
  
 Oprócz dziedziczone z metody `IUnknown`, `ISetNextStatement` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Określa, czy punkt wykonywania można ustawić w określonej lokalizacji.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Ustawia punkt wykonywania w określonej lokalizacji.|