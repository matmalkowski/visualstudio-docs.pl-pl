---
title: IDebugDocumentHelper::Init | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45cd57e4ba9e86bf84f927f487c637d61aa5339b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794050"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init` Metoda inicjuje pomocnika dokumentu debugowania z nazwą i atrybuty początkowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 [in] Debugowanie aplikacji skojarzony z tym dokumentem.  
  
 `pszShortName`  
 [in] Zerem ciągu zawierającego krótką nazwę dokumentu.  
  
 `pszLongName`  
 [in] Ciąg zakończony zerem, zawierający długa nazwa dokumentu.  
  
 `docAttr`  
 [in] Określa atrybuty dokumentu tekstowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda inicjuje pomocnika dokumentu debugowania z nazwą i atrybuty początkowej.  
  
 Ten dokument nie pojawia się w drzewie do `IDebugDocumentHelper::Attach` jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Stałe TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)