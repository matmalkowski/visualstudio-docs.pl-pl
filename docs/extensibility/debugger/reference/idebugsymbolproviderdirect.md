---
title: IDebugSymbolProviderDirect | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65a4a2f0f0823b9a723414247e1e1d6eb263d7a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121589"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Reprezentuje dostawcę symbol, który ma bezpośredni dostęp do metadanych i podstawowe interfejsy symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Pobiera identyfikator domeny aplikacji, podanych adresów debugowania.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Pobiera informacje o modułach w grupie symboli.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Pobiera informacje o dostawcy symbol jest członkiem grupy symbolu.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Pobiera informacje o importu metadanych.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Pobiera informacje o metodzie pod adresem określonym debugowania.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Pobiera czytnika symboli dla niezarządzanego kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs może służyć zamiast większość inne interfejsy dostawcy symbolu. Zapewnia bezpośredni dostęp do metadanych i `CorSym` interfejsów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll