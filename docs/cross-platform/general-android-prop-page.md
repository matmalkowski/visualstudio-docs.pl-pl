---
title: Ogólne właściwości projektu (Android C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 6e4f7da0c8d1727446c23ad25db2bf64228cbc9a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="general-project-properties-android-c"></a>Ogólne właściwości projektu (Android C++)

Właściwość | Opis | Opcje
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Nazwa obiektu docelowego | Określa nazwę pliku, który zostanie wygenerowany przez projekt.
Rozszerzenie docelowego | Określa rozszerzenie pliku, który zostanie wygenerowany przez projekt. (Przykład: .exe lub .dll)
Rozszerzenia do usunięcia podczas oczyszczania | Rozdzielana średnikami Specyfikacja symboli wieloznacznych określająca jakie pliki w katalogu pośrednim mają zostać usunięte podczas oczyszczania lub Odbuduj.
Tworzenie pliku dziennika | Określa plik dziennika kompilacji do zapisu, gdy rejestrowanie kompilacji jest włączona.
Zestaw narzędzi platformy | Określa zestaw narzędzi używanych do kompilowania bieżącej konfiguracji. Jeśli nie jest używany zestaw, do domyślnego zestawu narzędzi
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Dynamicznymi (.so)** -dynamicznymi (.so)<br>**Biblioteka statyczna (.a)** — biblioteka statyczna (tj.)<br>**Narzędzie** — narzędzie<br>**Pliku reguł programu make** -pliku reguł programu make<br>
Docelowy poziom interfejsu API | Celem tej konfiguracji systemu android poziom interfejsu API zestawu NDK.
Użyj STL | Określa, która standardowa biblioteka C++ do użycia dla tej konfiguracji. | **Minimalny Biblioteka środowiska uruchomieniowego języka C++ (system)**<br>**Biblioteka statyczna środowiska uruchomieniowego języka C++ (gabi ++ _statyczny adres)**<br>**Biblioteka udostępniona środowiska uruchomieniowego języka C++ (gabi ++ _shared)**<br>**Biblioteka statyczna środowiska uruchomieniowego STLport (stlport_static)**<br>**Biblioteka udostępniona środowiska uruchomieniowego STLport (stlport_shared)**<br>**Biblioteka statyczna GNU STL (gnustl_static)**<br>**Biblioteka udostępniona GNU STL (gnustl_shared)**<br>**LLVM libc ++ biblioteka statyczna (_statyczny adres c ++)**<br>**LLVM libc ++ biblioteki udostępnionej (_shared c ++)**<br>
Tryb przycisku przewijania | Generuj kod wykonujący dla mikroarchitektury thumb. Dotyczy tylko architektury arm. | **Thumb**<br>**ARM**<br>**wyłączone**<br>
