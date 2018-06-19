---
title: Idiastackwalkframe — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f16d6f824b3b150406c23cce87e186fe9b120999
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465632"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Przechowuje stosu kontekstu między wywołań [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaStackWalkFrame`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Pobiera wartość rejestru.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Ustawia wartość rejestru.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Odczytuje pamięci z obrazu.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Wyszukuje ramka określonej wartości atrybutu stosu dla najbliższej adres zwrotny funkcji.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Wyszukuje ramka stosu określony dla adres zwrotny lub prawie określony adres.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest używany podczas wykonywania programu do odczytu i zapisu rejestrów, a także uzyskiwać dostęp do pamięci i znaleźć adres zwrotny.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Aplikacja kliencka implementuje ten interfejs i przekazuje wystąpienie interfejsu do [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) metody. To samo wystąpienie elementu ten interfejs jest używany wielokrotnie w celu zachowania stanu rejestrów podczas każdego wywołania elementu `execute` metody. `execute` Metody również używa tego interfejsu w celu określenia adres zwrotny.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)