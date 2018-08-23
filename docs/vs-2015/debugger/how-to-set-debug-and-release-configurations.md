---
title: 'Porady: Ustaw wartość Debug i Release konfiguracje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 137c85f5433343327cf677ef76c1116bd6ef6821
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42633692"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Porady: ustawienia konfiguracji Debug i Release
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Ustawianie debugowania i konfiguracje wydania](https://docs.microsoft.com/visualstudio/debugger/how-to-set-debug-and-release-configurations).  
  
Projektów programu Visual Studio mają oddzielnych wersji i konfiguracji programu do debugowania. Jak sugerują nazwy kompilujesz wersję debugera do debugowania i wersję zwolnienia do ostatecznej dystrybucji zwolnienia.  
  
 Konfiguracja debugowania programu została skompilowana z informacji pełnego symbolicznego debugowania i bez optymalizacji. Optymalizacja komplikuje debugowanie, ponieważ relacja między kodem źródłowym i wygenerowanymi instrukcjami jest bardziej złożona.  
  
 Konfiguracja wydania programu nie zawiera żadnych informacji symbolicznego debugowania i jest w pełni zoptymalizowana. Debugowanie informacje mogą być generowane w plikach PDB, w zależności od opcji kompilatora, które są używane. Tworzenie plików PDB może być bardzo przydatne, jeśli później trzeba debugować swoje wersje.  
  
 Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md).  
  
 Możesz zmienić konfigurację kompilacji z **kompilacji** menu na pasku narzędzi lub na stronach właściwości projektu. Strony właściwości projektu są specyficzne dla języka. Poniższa procedura pokazuje, jak zmienić konfigurację kompilacji w menu i paska narzędzi. Aby uzyskać więcej informacji o tym, jak zmienić konfigurację kompilacji w projektach w różnych językach, zobacz sekcję Tematy pokrewne poniżej.  
  
### <a name="to-change-the-build-configuration"></a>Aby zmienić konfigurację kompilacji  
  
1.  W menu kompilacja: kliknij **kompilacji / programu Configuration Manager**, a następnie wybierz **debugowania** lub **wersji**.  
  
2.  Na pasku narzędzi wybierz **debugowania** lub **wersji** z **konfiguracje rozwiązania** pola listy.  
  
     ![Konfiguracja kompilacji narzędzi](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Ten pasek narzędzi nie jest dostępny w wersji Express. Możesz użyć **Kompiluj rozwiązanie F6** i **Rozpocznij debugowanie F5** elementy menu, aby wybrać konfigurację.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Ustawienia projektu dla języka C# konfiguracji debugowania](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Porady: tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md)   
 [Konfiguracji Debug i Release projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)



