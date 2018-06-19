---
title: JsRuntimeHandle — Typedef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3c0344e203c58691048c55ba4080c6c86c1c643
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788512"
---
# <a name="jsruntimehandle-typedef"></a>JsRuntimeHandle — Typedef
Dojście do obsługi Chakra.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## <a name="remarks"></a>Uwagi  
 Każdego środowiska uruchomieniowego Chakra ma swoją własną aparat niezależne wykonywania, kompilator JIT i pamięci sterty zebrane. W efekcie każdego środowiska uruchomieniowego jest całkowicie odizolowane od innych środowisk uruchomieniowych.  
  
 Środowisk uruchomieniowych mogą być używane w którymkolwiek wątku, ale tylko jeden wątek można wywołać w środowisku uruchomieniowym w dowolnym momencie.  
  
> [!WARNING]
>  JsRuntimeHandle, w przeciwieństwie do innych odwołań do obiektów w Chakra hosting interfejsu API, nie jest bezużytecznych, ponieważ zawiera ona pamięci sterty zebranych sam. Środowisko wykonawcze będzie istnieć do momentu jsdisposeruntime — jest wywoływana.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)