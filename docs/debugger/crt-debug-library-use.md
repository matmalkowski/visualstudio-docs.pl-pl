---
title: Korzystanie z biblioteki debugowania CRT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e550a5fa705f3c85b3464046cd3c92d96bc47ca
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31467959"
---
# <a name="crt-debug-library-use"></a>Korzystanie z biblioteki debugowania CRT
Biblioteki wykonawcze języka C zapewnia zaawansowaną obsługę debugowania. Aby użyć jednej z bibliotek debugowania CRT, należy połączyć z [/DEBUG](/cpp/build/reference/debug-generate-debug-info) i skompiluj z **/mdd**, **/MTd**, lub **/LDd**.  
  
## <a name="remarks"></a>Uwagi  
 Definicje głównego i makra debugowania CRT znajdują się w pliku nagłówka CRTDBG.h.  
  
 Funkcje bibliotek debugowania CRT z są kompilowane przy użyciu informacji o debugowaniu ([/Zd/z7, / zi, /ZI (Format informacji debugowania)](/cpp/build/reference/z7-zi-zi-debug-information-format)) i bez optymalizacji. Niektóre funkcje zawierają potwierdzenia do Sprawdź parametry przekazywane do nich, i kod źródłowy jest dostępne. Z tego kodu źródłowego można wkraczać do funkcji CRT, aby potwierdzić oczekiwać i sprawdź, czy złych parametrów lub pamięci stanów pracy funkcji. (Niektóre technologii CRT jest zastrzeżone i nie ma kodu źródłowego dla obsługi wyjątków, zmiennoprzecinkowych i kilka innych procedur).  
  
 Po zainstalowaniu programu Visual C++, istnieje możliwość instalowania kodu źródłowego C biblioteki wykonawczej na dysku twardym. Kod źródłowy nie zostanie zainstalowany, należy najpierw CD-ROM Aby wkraczać do funkcji CRT.  
  
 Aby uzyskać więcej informacji na różnych biblioteki wykonawczej można użyć, zobacz [biblioteki wykonawcze języka C](/cpp/c-runtime-library/crt-library-features).  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)](/cpp/build/reference/md-mt-ld-use-run-time-library)