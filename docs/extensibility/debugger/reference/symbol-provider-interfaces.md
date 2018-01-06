---
title: Symbol interfejsy dostawcy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f2b3ec92ce76a3218c646c51ccb28d99322baf93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="symbol-provider-interfaces"></a>Symbol dostawcy interfejsów
Poniżej przedstawiono interfejsy obsługi symboli dla [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Omówienie  
 Te interfejsy są używane do oceny zmiennych w stosie wywołań w trybie przerwania. Są one wykonywane tylko dla wspólnego języka środowiska uruchomieniowego symbol dostawców (SP).  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Reprezentuje adres elementu.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Reprezentuje adres elementu zapewnianie dostępu do identyfikatora procesu.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Reprezentuje symbol tablicy lub typu tablicy.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Reprezentuje symbol klasy lub typu klasy.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Reprezentuje dostawcę symbol modelu COM + z metod, które są specyficzne dla kodu zarządzanego.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Reprezentuje dostawcę symbol modelu COM + z metod, które są specyficzne dla kodu zarządzanego i rozszerza **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Reprezentuje symbol lub typu, który jest kontenerem dla innych symboli lub typów.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Reprezentuje atrybut niestandardowy, który można dołączyć do symbolu.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Reprezentuje zapytania dla atrybutów niestandardowych dla metody lub typu.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Umożliwia dostęp do atrybutów niestandardowych symbolu.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Podstawowy interfejs dla dowolnego typu, który można określić w czasie wykonywania.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Reprezentuje dynamiczne pole dla [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obiektu.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Reprezentuje typ wyliczenia.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Rozszerza typy dostępnych pól do obsługi kodu zarządzanego ogólne.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Klasa podstawowa dla wszystkich pól; reprezentuje opis symbolu lub typu.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Reprezentuje definicję pola dla kodu zarządzanego typu ogólnego.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Reprezentuje wystąpienie pola dla kodu zarządzanego typu ogólnego.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Reprezentuje parametr dla typu ogólnego kodu zarządzanego.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Reprezentuje metodę.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Reprezentuje modyfikujący opcjonalne debugowania.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Reprezentuje wskaźnik.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Reprezentuje wartość wyliczenia typu pierwotnego z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Reprezentuje właściwość klasy kodu zarządzanego, który można get lub ustawić.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Reprezentuje dostawcę symbol, który zawiera symbole i typy.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Reprezentuje dostawcę symbol bezpośredni dostęp do metadanych i podstawowe interfejsów symbolu.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Reprezentuje możliwość tworzenia reprezentujący typ pola.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Rozszerza **IDebugTypeFieldBuilder** aby można było utworzyć typy tablic.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Reprezentuje kolekcję [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektów.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Reprezentuje kolekcję [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) obiektów.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Reprezentuje kolekcję [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)