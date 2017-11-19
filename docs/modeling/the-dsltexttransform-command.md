---
title: Polecenie DslTextTransform | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: "30"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: fd45a33b421e889b05fd78eceddc0b05126e4a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
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