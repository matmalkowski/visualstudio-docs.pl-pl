---
title: IDebugProgram2::WriteDump | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8708751820ca70386e6c9927105384eee9a96a15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678085"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugProgram2::WriteDump](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-writedump).  
  
Zapisuje plik zrzutu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [in] Wartość z zakresu od [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) wyliczenie, które określa typ zrzutu, na przykład, w skrócie lub long.  
  
 `pszDumpUrl`  
 [in] Adres URL zrzutu do zapisu. Zazwyczaj jest to w formie `file://c:\path\filename.ext`, ale może być dowolny prawidłowy adres URL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zrzut program zwykle obejmuje bieżącej ramki stosu, sam stos, Lista wątków, uruchomiony w programie i prawdopodobnie wszystkie pamięci, który jest właścicielem program.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

