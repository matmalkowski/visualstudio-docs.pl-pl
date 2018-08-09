---
title: Moduł wyliczający kod stanu katalogu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea8abd11f3af8be510e88579651fb0a7f92e075b
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638469"
---
# <a name="directory-status-code-enumerator"></a>Moduł wyliczający kod stanu katalogu
`SccDirStatus` Modułu wyliczającego zawiera nazwanych stałych, określające stan katalogu w systemie kontroli źródła. To wyliczenie jest używane przez [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). To została wprowadzona w wersji 1.2 API wtyczki kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 SCC_DIRSTATUS_INVALID  
 Nie można uzyskać stanu; nie należy polegać na niej.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Katalog nie jest pod kontrolą źródła.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Katalog jest pod kontrolą źródła.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Projekt odpowiadający ten katalog jest pusty.  
  
## <a name="see-also"></a>Zobacz także  
 [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)