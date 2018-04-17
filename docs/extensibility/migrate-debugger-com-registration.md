---
title: Migrowanie debugera 64-bitowych modelu COM klasy rejestracji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/10/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: douge
ms.workload:
- greggm
ms.openlocfilehash: 28516038170dd34028d11bf9a070cf265ecfd830
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
