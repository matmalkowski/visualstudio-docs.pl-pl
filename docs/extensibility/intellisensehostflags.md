---
title: IntelliSenseHostFlags | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8e00768e544dbd6bb37a4de70e0f730fe967a70
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Określa flagi hosta IntelliSense.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Elementy członkowskie|Opis|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Kontekst bufor jest tylko do odczytu.|  
|`IHF_NOSEPARATESUBJECT`|Brak tekstu podmiotu. Buforu kontekstu zawiera IntelliSense docelowego (oznacza `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Tekst tematu nie jest kilku-wiersza funkcją.|  
|`IHF_FORCECOMMITTOCONTEXT`|Taki sam jak `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Edytowanie (w temacie lub w kontekście) powinno być wykonywane w trybie zastępowania.|  
  
## <a name="requirements"></a>Wymagania  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop>