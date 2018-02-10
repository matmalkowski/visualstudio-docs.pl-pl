---
title: Polecenie DslTextTransform | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 24a3f292633b915678bad232a4a671c7906e15cb
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform — Polecenie
DslTextTransform.cmd to skrypt, który wywołuje TextTransform.exe i uruchamia go z typowych opcji. Można zautomatyzować co noc kompilacji DslTextTransformation.cmd Twojego [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projektów. Aby uzyskać więcej informacji, zobacz [generowania plików narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd znajduje się w następującym katalogu:  
  
 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**  
  
 Jako dane wejściowe DslTextTransform.cmd można określić następujące argumenty:  
  
-   Katalog wyjściowy projektu modelu domeny.  
  
-   Katalog wyjściowy projektu Projektanta definicji.  
  
-   Lokalizacja pliku szablonu tekstowego.  
  
 DslTextTransform.cmd przetwarza pliku szablonu określony tekst przy użyciu domyślnego procesory dyrektywy i zestawów. W przypadku utworzenia niestandardowego procesory dyrektywy, można utworzyć własny plik wsadowy, który wywołuje TextTransform.exe. W tym pliku wsadowego można określić ponownie zestawy i skojarzone niestandardowego procesory dyrektywy.