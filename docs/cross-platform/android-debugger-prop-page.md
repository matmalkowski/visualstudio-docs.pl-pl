---
title: Właściwości debugera systemu android (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 7d18125c6666a8eb68becd828da36ecdab077507
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="android-debugger-properties"></a>Właściwości debugera systemu android

Właściwość | Opis | Opcje
--- | ---| ---
Typ debugera | Określa typ kodu do debugowania. | **Tylko kod natywny**<br>**Tylko w języku Java**<br>
Docelowy debugowania | Określa emulator lub urządzenie używane do debugowania. Jeśli nie uruchomiono żadnych emulatorów, następnie użyj "Android Virtual Device (AVD) Manager" Uruchom urządzenie.
Pakiet do uruchomienia | Określa lokalizację pliku apk, który będzie debugowany. Wybierz tę opcję, aby określić, że określony pakiet (APK) powinna być uruchamiana podczas debugowania aplikacji.
Uruchamianie działania | Działanie systemu Android używane do uruchamiania aplikacji, musi być zgodne z działaniem używanym w manifeście. Naciśnij przycisk Zastosuj, aby pobrać listę z pliku AndroidManifest.xml i wypełnić ją dynamicznie.
Dodatkowa ścieżka wyszukiwania symboli | Dodatkowa ścieżka wyszukiwania dla symboli debugowania.
Ścieżki wyszukiwania źródła Java dodatkowe | Dodatkowe ścieżki wyszukiwania plików źródłowych Java. (Dotyczy tylko gdy typ debugera jest tylko Java).
