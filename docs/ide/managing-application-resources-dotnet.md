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
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6645a1147b2ee5f5d5ba0b85a7f8999008f5ae19
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="managing-application-resources-net"></a>Zarządzanie zasobami aplikacji (.NET)

Pliki zasobów to pliki, które są częścią aplikacji, ale nie są kompilowane, na przykład pliki ikon lub plików audio. Ponieważ te pliki nie są częścią procesu kompilacji, trzeba je zmienić bez konieczności ponownego kompilowania Twoje pliki binarne. Jeśli planujesz do zlokalizowania aplikacji, należy użyć plików zasobów dla wszystkich ciągów i innych zasobów, które muszą zostać zmienione po lokalizowanie aplikacji.

Aby uzyskać więcej informacji o zasobach w aplikacjach klasycznych .NET, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index).

## <a name="working-with-resources"></a>Praca z zasobów

W projekcie kodu zarządzanego Otwórz okno właściwości projektu. Można otworzyć okno właściwości przez:

- prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierając **właściwości**
- Wpisz "właściwości projektu" w **Szybkie uruchamianie** okna
- Wybieranie **Alt**+**Enter** w **Eksploratora rozwiązań** okna

Wybierz **zasobów** kartę. Można dodać plik .resx, jeśli projektu nie zawierają jedną już, dodać i usunąć różnych rodzajów zasobów i modyfikowanie istniejących zasobów.

## <a name="resources-in-other-project-types"></a>Zasoby w innych typów projektów

Zasoby są zarządzane w różny sposób w projektach platformy .NET niż w innych typów projektów. Aby uzyskać więcej informacji o zasobach w:

- Uniwersalnych aplikacji platformy systemu Windows (UWP), zobacz [zasobów aplikacji i systemu zarządzania zasobów](/windows/uwp/app-resources/)
- Zobacz aplikacji Windows 8.x, [Definiowanie zasobów aplikacji (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx)
- Projekty C++, zobacz [Praca z plikami zasobów](/cpp/windows/working-with-resource-files) i [porady: tworzenie zasobu](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Zobacz także

[Zasoby w aplikacjach klasycznych (.NET Framework)](/dotnet/framework/resources/index)