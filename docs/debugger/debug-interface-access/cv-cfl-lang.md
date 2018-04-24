---
title: CV_CFL_LANG — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c383fd188c035dfacf41cdf86a84b4afe8dfa40d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="cvcfllang"></a>CV_CFL_LANG
Określa język kodu źródłowego aplikacji lub połączonych modułu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## <a name="elements"></a>Elementy  
 CV_CFL_C  
 Język aplikacji jest C.  
  
 CV_CFL_CXX  
 Język aplikacji jest C++.  
  
 CV_CFL_FORTRAN  
 Język aplikacji jest FORTRAN.  
  
 CV_CFL_MASM  
 Język aplikacji jest Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 Język aplikacji jest Pascal.  
  
 CV_CFL_BASIC  
 Język aplikacji jest BASIC.  
  
 CV_CFL_COBOL  
 Język aplikacji jest COBOL.  
  
 CV_CFL_LINK  
 Aplikacja jest modułem generowanych przez konsolidator.  
  
 CV_CFL_CVTRES  
 Aplikacja jest konwertowane za pomocą narzędzia CVTRES modułu zasobów.  
  
 CV_CFL_CVTPGD  
 Aplikacja jest modułem POGO zoptymalizowanych pod kątem wygenerowane za pomocą narzędzia CVTPGD.  
  
 CV_CFL_CSHARP  
 Język aplikacji jest C#.  
  
 CV_CFL_VB  
 Język aplikacji jest Visual Basic.  
  
 CV_CFL_ILASM  
 Język aplikacji jest zestawem język pośredni (to znaczy zestawów środowiska uruchomieniowego języka wspólnego (CLR)).  
  
 CV_CFL_JAVA  
 Język aplikacji jest Java.  
  
 CV_CFL_JSCRIPT  
 Język aplikacji jest Jscript.  
  
 CV_CFL_MSIL  
 Język aplikacji jest nieznany Microsoft pośredniego Language (MSIL), prawdopodobnie wynik przy użyciu [opcję/LTCG (Generowanie kodu w czasie Link)](/cpp/build/reference/ltcg-link-time-code-generation) przełącznika.  
  
 CV_CFL_HLSL  
 Aplikacja język jest wysoki poziom programu do cieniowania.  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie wartości są zwracane przez wywołanie do [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)