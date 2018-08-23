---
title: Idiasymbol::findchildren — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60895193f1b32cb41adeb808034e3d7ca2e407e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676509"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiasymbol::findchildren —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-findchildren).  
  
Pobiera elementy podrzędne symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `symtag`  
 [in] Określa tagi symboli elementów podrzędnych, które mają zostać pobrane, zgodnie z definicją w [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md). Ustaw `SymTagNull` dla wszystkich elementów podrzędnych do pobrania.  
  
 `name`  
 [in] Określa nazwę elementy podrzędne, które mają zostać pobrane. Ustaw `NULL` dla wszystkich elementów podrzędnych do pobrania.  
  
 `compareFlags`  
 [in] Określa opcje porównywania stosowany do pasujących nazwy. Wartości z kolekcji [namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md) wyliczenia można samodzielnie lub w połączeniu.  
  
 `ppResult`  
 [out] Zwraca [idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md) pobrać obiekt, który zawiera listę symbolami podrzędnymi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` Jeśli co najmniej jeden element podrzędny symbol został znaleziony lub zwraca `S_FALSE` Jeśli żadne elementy podrzędne nie znaleziono; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Metoda ta jest identyczna z wywoływaniem [idiasession::findchildren —](../../debugger/debug-interface-access/idiasession-findchildren.md) metody za pomocą tego symbolu jako pierwszy parametr.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)   
 [Idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Idiasession::findchildren —](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md)



