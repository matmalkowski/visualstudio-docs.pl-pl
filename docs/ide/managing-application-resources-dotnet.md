---
title: "Zarządzanie zasobami aplikacji (.NET) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b599a919911fcc5d2833cfe69b75f7b32cced858
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="managing-application-resources-net"></a>Zarządzanie zasobami aplikacji (.NET)
Pliki zasobów to pliki, które są częścią aplikacji, ale nie są kompilowane, na przykład pliki ikon lub plików audio. Ponieważ te pliki nie są częścią procesu kompilacji, trzeba je zmienić bez konieczności ponownego kompilowania Twoje pliki binarne. Jeśli planujesz do zlokalizowania aplikacji, należy użyć plików zasobów dla wszystkich ciągów i innych zasobów, które muszą zostać zmienione po lokalizowanie aplikacji.  
  
Aby uzyskać więcej informacji o zasobach w aplikacjach klasycznych .NET, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index). Aby uzyskać więcej informacji o zasobach w aplikacjach klasycznych C++, zobacz [Praca z plikami zasobów](/cpp/windows/working-with-resource-files).  
  
Aplikacji platformy uniwersalnej systemu Windows korzystają z modelu innego zasobu z aplikacji klasycznych. Aby uzyskać informacje o zasobach w aplikacji Windows 8.x, zobacz [Definiowanie zasobów aplikacji (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx).  
  
## <a name="working-with-resources"></a>Praca z zasobów  
W projekcie kodu zarządzanego Otwórz okno właściwości projektu. Można otworzyć okno właściwości przez:

- prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierając **właściwości**
- wpisywanie **właściwości projektu** w **Szybkie uruchamianie** okna
- Wybieranie **Alt + Enter** w **Eksploratora rozwiązań** okna

Wybierz **zasobów** kartę. Można dodać plik .resx, jeśli projektu nie zawierają jedną już, dodać i usunąć różnych rodzajów zasobów i modyfikowanie istniejących zasobów.  
  
Aby dowiedzieć się, jak pracować z zasobów w projektach C++, zobacz [porady: tworzenie zasobu](/cpp/windows/how-to-create-a-resource).