---
title: Migrowanie debugera 64-bitowych modelu COM klasy rejestracji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: "1"
author: gregg-miskelly
ms.author: greggm
manager: ghogen
ms.workload: greggm
ms.openlocfilehash: 737c970555fce8f3cdac118421eddb09f52d7c53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrowanie debugera 64-bitowych rejestracji klasy COM

Debuger rozszerzeń, które zarejestrować klasy COM w wpisów z HKEY_CLASSES_ROOT (za pomocą polecenia regasm, regsvr32, lub bezpośrednio zapisywanie do rejestru) i ładowane do msvsmon.exe (debugera zdalnego) jest teraz możliwe zapewnienie tej rejestracji do polecenia msvsmon bez konieczności Aby zapisać wpisów z HKEY_CLASSES_ROOT. Ma to wpływ na starszych ewaluatorów wyrażeń debugera platformy .NET lub aparatami debugowania, skonfigurowanych załadować w procesie msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>polecenie msvsmon-comclass-def

Aby użyć tej metody, Dodaj plik *.msvsmon-comclass-def.json obok polecenia msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Poniżej przedstawiono przykładowy plik polecenia msvsmon-comclass-def, który rejestruje jedną zarządzane i jedną klasę native:

Nazwa pliku: MyCompany.MyExample.msvsmon-comclass-def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
