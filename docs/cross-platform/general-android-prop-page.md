---
title: "Ogólne właściwości projektu (Android C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: ghogen
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
ms.openlocfilehash: f564ca09b3a19848ae95128ba8b529b8a84c2210
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
Tryb przycisku przewijania | Generuj kod wykonujący dla mikroarchitektury thumb. Dotyczy tylko architektury arm. | **Thumb**<br>**ARM**<br>**Wyłączone**<br>
