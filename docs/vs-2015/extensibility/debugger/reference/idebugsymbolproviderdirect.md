---
title: IDebugSymbolProviderDirect | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c0d8ea7a4d01b3fe18eccab67adfadb1a62cd75
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677139"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugSymbolProviderDirect](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsymbolproviderdirect).  
  
Reprezentuje dostawcę symbol, który ma bezpośredni dostęp do metadanych i podstawowych interfejsów symboli.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Pobiera identyfikator domeny aplikacji, mając adres debugowania.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Pobiera informacje o modułach w grupie symboli.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Pobiera informacje o grupie symbol dostawca symboli jest elementem członkowskim.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Pobiera informacje o Importowanie metadanych.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Pobiera informacje o metodzie pod adresem określonym debugowania.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Pobiera czytnik symbolu dla niezarządzanego kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs można używać zamiast większość inne interfejsy dostawcy symboli. Zapewnia bezpośredni dostęp do metadanych i `CorSym` interfejsów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

