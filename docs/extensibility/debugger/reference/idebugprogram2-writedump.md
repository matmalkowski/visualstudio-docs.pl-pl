---
title: IDebugProgram2::WriteDump | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::WriteDump
helpviewer_keywords: IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 40fcd345a2a07a0ebdcf9e984b060cc81e946fc3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Zapisuje plik zrzutu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `DumpType`  
 [in] Wartość z zakresu od [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) wyliczenie określający typ zrzut, na przykład, czyli lub long.  
  
 `pszDumpUrl`  
 [in] Adres URL zrzutu do zapisu. Zazwyczaj jest to w formie `file://c:\path\filename.ext`, ale może być dowolny prawidłowy adres URL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zrzut program zwykle obejmuje bieżącej ramki stosu, sam stos, listę wątki uruchomione w programie i prawdopodobnie wszystkie pamięci, który jest właścicielem program.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)