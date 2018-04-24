---
title: IDiaSession::findAcceleratorInlineesByName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9e95193b361dcfe0935d209bf1fc3687914e1c4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Zwraca wyliczenie symboli dla ramki wbudowane odpowiadający wbudowanego określonej nazwy funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 [in] Nazwa funkcji przed wstawianiem do treści do wyszukania.  
  
 `option`  
 [in] Nazwa opcji wyszukiwania, aby używane podczas wyszukiwania dla wbudowanego ramkach, które odpowiadają `name`. Aby uzyskać więcej informacji, zobacz [namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 [out] Wskaźnik do `IDiaEnumSymbols` wskaźnika interfejsu, który został zainicjowany z wynikiem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja wyszukuje wersji śródwierszowych tylko w funkcjach stub akceleratora. Ignoruje natywnych języka C++ procedury rekordów.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)