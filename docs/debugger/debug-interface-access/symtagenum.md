---
title: Symtagenum — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0268b6e46787e772f7343e5306713554687e869a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="symtagenum"></a>SymTagEnum
Określa typ symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## <a name="elements"></a>Elementy  
 `SymTagNull`  
 Wskazuje, czy symbol nie ma typu.  
  
 `SymTagExe`  
 Wskazuje, czy symbol jest pliku .exe. Istnieje tylko jeden `SymTagExe` symbol na magazynie symboli. On służy jako zakres globalny i nie ma nadrzędnego leksykalne.  
  
 `SymTagCompiland`  
 Wskazuje compiland — symbol dla każdego składnika compiland w magazynie symboli. Dla natywnych aplikacji `SymTagCompiland` symbole odpowiadają plików obiektów połączone w obrazie. Dla niektórych typów obrazów Microsoft języka pośredniego (MSIL) istnieje jeden compiland dla klasy.  
  
 `SymTagCompilandDetails`  
 Wskazuje, czy symbol zawiera rozszerzonych atrybutów compiland. Podczas pobierania właściwości te mogą wymagać ładowanie symboli compiland.  
  
 `SymTagCompilandEnv`  
 Wskazuje, że symbol jest środowisko zdefiniowany compiland.  
  
 `SymTagFunction`  
 Wskazuje, czy symbol jest funkcją.  
  
 `SymTagBlock`  
 Wskazuje, czy symbol jest zagnieżdżony blok.  
  
 `SymTagData`  
 Wskazuje, czy symbol jest danych.  
  
 `SymTagAnnotation`  
 Wskazuje, czy symbol jest dla adnotacji kodu. Elementy podrzędne tego symbolu są dane stałej ciągów (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Większość klientów zignorować ten symbol.  
  
 `SymTagLabel`  
 Wskazuje, czy symbol jest etykiety.  
  
 `SymTagPublicSymbol`  
 Wskazuje, czy symbol jest symboli publicznych. Dla natywnych aplikacji ten symbol jest COFF zewnętrzny symbol podczas łączenia obrazu.  
  
 `SymTagUDT`  
 Wskazuje, czy symbol jest typem zdefiniowane przez użytkownika (struktury, klasy lub union).  
  
 `SymTagEnum`  
 Wskazuje, czy symbol jest wyliczenie.  
  
 `SymTagFunctionType`  
 Wskazuje, czy symbol jest typem podpisu funkcji.  
  
 `SymTagPointerType`  
 Wskazuje, czy symbol jest typem wskaźnika.  
  
 `SymTagArrayType`  
 Wskazuje, czy symbol jest typem tablicy.  
  
 `SymTagBaseType`  
 Wskazuje, czy symbol jest typem bazowym.  
  
 `SymTagTypedef`  
 Wskazuje, czy symbol jest `typedef`, czyli aliasu dla innego typu.  
  
 `SymTagBaseClass`  
 Wskazuje, czy symbol jest klasą bazową typu zdefiniowanego przez użytkownika.  
  
 `SymTagFriend`  
 Wskazuje, że symbol jest znajomego typu zdefiniowanego przez użytkownika.  
  
 `SymTagFunctionArgType`  
 Wskazuje, czy symbol jest argument funkcji.  
  
 `SymTagFuncDebugStart`  
 Wskazuje, czy symbol jest lokalizacji końcowej kodu prologu funkcji.  
  
 `SymTagFuncDebugEnd`  
 Wskazuje, że symbol jest położenie początku funkcji epilogu kodu.  
  
 `SymTagUsingNamespace`  
 Wskazuje, czy symbol jest nazwą obszaru nazw, aktywne w bieżącym zakresie.  
  
 `SymTagVTableShape`  
 Wskazuje, czy symbol jest opis tabeli wirtualnej.  
  
 `SymTagVTable`  
 Wskazuje, czy symbol jest wskaźnik tabeli wirtualnej.  
  
 `SymTagCustom`  
 Wskazuje, że symbol jest symbolem niestandardowe i nie będzie interpretowany przez pakietu DIA.  
  
 `SymTagThunk`  
 Wskazuje, że symbol jest sekcją thunk używane do udostępniania danych między 16 i 32-bitowego.  
  
 `SymTagCustomType`  
 Wskazuje, że symbol jest symbol kompilatora niestandardowych.  
  
 `SymTagManagedType`  
 Wskazuje, czy symbol jest w metadanych.  
  
 `SymTagDimension`  
 Wskazuje, czy symbol jest FORTRAN tablicy wielowymiarowej.  
  
 `SymTagCallSite`  
 Wskazuje, że symbol reprezentuje miejsce wywołania.  
  
 `SymTagInlineSite`  
 Wskazuje, że symbol reprezentuje wbudowane witrynę.  
  
 `SymTagBaseInterface`  
 Wskazuje, czy symbol jest interfejs podstawowy.  
  
 `SymTagVectorType`  
 Wskazuje, czy symbol jest typem wektora.  
  
 `SymTagMatrixType`  
 Wskazuje, czy symbol jest typem macierzy.  
  
 `SymTagHLSLType`  
 Wskazuje, czy symbol jest typem wysokiego poziomu programu do cieniowania języka.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie symbole w pliku debugowania ma identyfikujące tag, który określa typ symbolu.  
  
 To wyliczenie wartości są zwracane przez wywołanie do [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metody.  
  
 Wartości w tym wyliczeniu są przekazywane do następujących metod można ograniczyć wyszukiwanie do typu określony symbol:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)