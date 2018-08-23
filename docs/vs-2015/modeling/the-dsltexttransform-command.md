---
title: Polecenie DslTextTransform | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8a565fa6226348a1fe1b6dcfcbb67f704e74abc8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680096"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform — Polecenie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [polecenie DslTextTransform](https://docs.microsoft.com/visualstudio/modeling/the-dsltexttransform-command).  
  
DslTextTransform.cmd to skrypt, który wywołuje TextTransform.exe i uruchamia je przy użyciu typowe opcje. DslTextTransformation.cmd można użyć do zautomatyzowania nocna kompilacja z Twojej [!INCLUDE[dsl](../includes/dsl-md.md)] projektów. Aby uzyskać więcej informacji, zobacz [Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd znajduje się w następującym katalogu:  
  
 **\<Ścieżka instalacji zestawu SDK programu Visual Studio > \VisualStudioIntegration\Tools\Bin**  
  
 Jako dane wejściowe DslTextTransform.cmd, należy określić następujące argumenty:  
  
-   Katalog wyjściowy projektu modelu domeny.  
  
-   Katalog wyjściowy projektu Projektanta definicji.  
  
-   Lokalizacja pliku szablonu tekstu.  
  
 DslTextTransform.cmd przetwarza plik szablonu określony tekst przy użyciu domyślnego procesorów dyrektyw i zestawów. Jeśli utworzono niestandardowe procesory dyrektyw, można utworzyć własny plik wsadowy, który wywołuje TextTransform.exe. W tym pliku wsadowego można określić zestawy i skojarzone niestandardowe procesory dyrektyw.



