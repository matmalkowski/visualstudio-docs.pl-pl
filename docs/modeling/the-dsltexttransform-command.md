---
title: DslTextTransform — Polecenie
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
ms.openlocfilehash: a3605dd3d6cd7615a2afd4dba18bf2f7bed994f4
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
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