---
title: "Właściwości debugera systemu android (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: a296ea142b13b9bdcda888a7f382de9eeb17a40a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
