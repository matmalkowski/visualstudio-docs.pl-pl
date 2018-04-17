---
title: Polecenie DslTextTransform | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 11fb12f3716fe9f8b5fee13a7eecd88ee107ff45
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform — Polecenie
DslTextTransform.cmd to skrypt, który wywołuje TextTransform.exe i uruchamia go z typowych opcji. Można zautomatyzować co noc kompilacji DslTextTransformation.cmd Twojego [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projektów. Aby uzyskać więcej informacji, zobacz [generowania plików narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd znajduje się w następującym katalogu:  
  
 **\<Ścieżka instalacji programu Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**  
  
 Jako dane wejściowe DslTextTransform.cmd można określić następujące argumenty:  
  
-   Katalog wyjściowy projektu modelu domeny.  
  
-   Katalog wyjściowy projektu Projektanta definicji.  
  
-   Lokalizacja pliku szablonu tekstowego.  
  
 DslTextTransform.cmd przetwarza pliku szablonu określony tekst przy użyciu domyślnego procesory dyrektywy i zestawów. W przypadku utworzenia niestandardowego procesory dyrektywy, można utworzyć własny plik wsadowy, który wywołuje TextTransform.exe. W tym pliku wsadowego można określić ponownie zestawy i skojarzone niestandardowego procesory dyrektywy.