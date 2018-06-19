---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed73821021d3a993507db9925c512119fbb98ca1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119253"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Aparat debugowania (DE) umożliwia wysyłanie to opcjonalne zdarzenie do menedżera sesji debugowania (SDM), jeśli zostało zatrzymane.

## <a name="syntax"></a>Składnia

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji

Ten interfejs wprowadzono w programie Visual Studio 2005. Wcześniejsze wersje nie obsługują zatrzymywania asynchronicznego.

[Zatrzymaj](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) jest wywoływana przez SDM w scenariuszach wieloprocesowa lub wielu programów. Gdy program wysyła zdarzeniem zatrzymującym SDM, SDM żądań inne programy, aby zatrzymać zbyt.

Zatrzymaj służy do asynchronicznie powiadamia SDM, która przestała programu. Informuje o dostępności SDM jest przydatne w przypadku interpreter aparat debugowania, gdzie czasami żaden kod nie działa w debugowanym programu, to [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nie można zakończyć synchronicznie. Jeśli aparat debugowania chce zastosować asynchroniczne odbieranie tego powiadomienia, musi zwracać `S_ASYNC_STOP` z [zatrzymać](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Wymagania

Nagłówek: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll