---
title: Interfejs IDebugDocumentTextExternalAuthor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor interface
ms.assetid: 0b04de1b-f922-4526-af4e-c0af2b7c1ce4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f85ef798a6507c92130cbddae98de87a9924415
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794263"
---
# <a name="idebugdocumenttextexternalauthor-interface"></a>Interfejs IDebugDocumentTextExternalAuthor
Zezwala na zewnętrzne edytory bezpiecznie edycji dokumentów na podstawie pliku debugera za powiadamianie dokumentu zostanie zmieniony plik źródłowy.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugDocumentTextExternalAuthor` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentTextExternalAuthor::GetPathName](../../winscript/reference/idebugdocumenttextexternalauthor-getpathname.md)|Zwraca pełną ścieżkę i nazwę dokumentu.|  
|[IDebugDocumentTextExternalAuthor::GetFileName](../../winscript/reference/idebugdocumenttextexternalauthor-getfilename.md)|Zwraca nazwę dokumentu bez informacji o ścieżce.|  
|[IDebugDocumentTextExternalAuthor::NotifyChanged](../../winscript/reference/idebugdocumenttextexternalauthor-notifychanged.md)|Powiadamia hosta, że dokument źródłowy został zmieniony.|