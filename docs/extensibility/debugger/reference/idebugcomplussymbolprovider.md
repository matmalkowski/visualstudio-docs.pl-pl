---
title: IDebugComPlusSymbolProvider | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c6d356274998d07975dfce3cb3ba367c62c72ffb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Reprezentuje dostawcę symbol modelu COM + z metod, które są specyficzne dla kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Nie ma żadnych rozdzielenie interfejsów, które są przydatne do ewaluatora wyrażeń (EE) i tymi, które mają być używane przez aparat debugowania (DE), ale następujących metod będzie prawdopodobnie odsetek tylko deweloperzy DE: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols i UpdateSymbols.  
  
## <a name="methods"></a>Metody  
 Oprócz metod na [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interfejsu, tego interfejsu implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Określa, czy załadowano symbole debugowania dla określony moduł podany identyfikator domeny aplikacji.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Tworzy typ na podstawie określonego typu pierwotnego.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mapuje pozycji dokumentu w określonym module tablicę adresów debugowania.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Pobiera typ informacji o określonej podstawie jego adresu debugowania tablicy.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Pobiera nazwę zestawu podane swojej domeny modułu i aplikacji.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Pobiera klasy przy użyciu określonego atrybutu, które zostały wdrożone w danym języku programowania.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Pobiera klasy przy użyciu określonego atrybutu w danym module.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Pobiera punkt wejścia aplikacji.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Pobiera adres w funkcję, która reprezentuje przesunięcie danego wiersza.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Pobiera układ zmienne lokalne dla zestawu metod.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Zwraca nazwy skojarzonej z określony token podany obiekt jego metadanych.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Pobiera symbole debugowania z atrybutem danego nadrzędnego dla określonego modułu.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Pobiera czytnika symboli, który będzie używany przez kod niezarządzany.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Pobiera typ symbolu, podany adres debugowania.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Określa, w przypadku funkcji pod adresem określonym debugowania zostaną usunięte.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Określa, czy funkcja pod adresem określonym debugowania jest uznawane za przestarzałe.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Określa, czy kod pod adresem określonym debugera jest ukryty.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Ładuje symbole debugowania określony w pamięci.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Ładunki debugowania symbole otrzymał strumienia danych.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Zamienia bieżące symboli debugowania w strumieniu określone dane.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Zwalnia symboli debugowania dla określonego modułu z pamięci.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualizuje symboli debugowania w pamięci z tymi strumienia określone dane.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll