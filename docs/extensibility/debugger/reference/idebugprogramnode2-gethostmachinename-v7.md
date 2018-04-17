---
title: IDebugProgramNode2::GetHostMachineName_V7 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2adc7125c79afc6b9ebc16b6c4b36f5c147bcdfb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> PRZESTARZAŁE. NIE UŻYWAJ.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

#### <a name="parameters"></a>Parametry

`pbstrHostMachineName`  
[out] Zwraca nazwę komputera, w którym jest uruchomiony program.

## <a name="return-value"></a>Wartość zwracana

Implementacja zawsze powinna zwrócić `E_NOTIMPL`.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Począwszy od programu Visual Studio 2005, ta metoda nie jest już używany i powinien zawsze zwracają `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz też

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)