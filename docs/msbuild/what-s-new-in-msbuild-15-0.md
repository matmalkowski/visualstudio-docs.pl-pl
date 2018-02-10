---
title: Jaki &#39; s nowe w programie MSBuild 15 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 19b7c821f708267d4827d06858b63128ce747ac3
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="whats-new-in-msbuild-15"></a>What's New in 15 MSBuild
MSBuild jest teraz dostępna jako część [.NET Core SDK](https://www.microsoft.com/net/download/core) i można tworzyć projektów .NET Core w systemie Windows, macOS i Linux.  

## <a name="changed-path"></a>Zmieniona ścieżka
 Program MSBuild został zainstalowany w folderze w każdej wersji programu Visual Studio. Na przykład `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild`. Można również użyć następujące modułu programu PowerShell, aby zlokalizować MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 Program MSBuild nie jest już zainstalowane w globalnej pamięci podręcznej zestawów. Aby odwołać MSBuild programowo, należy użyć pakietów NuGet.

## <a name="changed-properties"></a>Zmiany właściwości  
 Następujące właściwości programu MSBuild zostały zaktualizowane z powodu nowego numeru wersji.  

-   `MSBuildToolsVersion`w tej wersji narzędzi jest 15.0. Wersja zestawu jest 15.1.0.0.

-   `MSBuildToolsPath`nie ma położenie ustalone. Domyślnie znajduje się w folderze MSBuild\15.0\Bin względną wobec lokalizacji instalacji programu Visual Studio, ale godzina instalacji programu Visual Studio można zmienić lokalizacji instalacji.

-   `ToolsVersion`Nie ustawiono wartości w rejestrze.  

-   `SDK35ToolsPath` i `SDK40ToolsPath` właściwości wskaż zestawu .NET Framework SDK, który jest spakowany w tej wersji programu Visual Studio (na przykład 10.0A dla narzędzi 4.X).  

## <a name="updates"></a>Aktualizacje
- [Element projektu](../msbuild/project-element-msbuild.md) ma nową `SDK` atrybutu. Również `Xmlns` atrybut teraz jest opcjonalne.
- [Pozycja elementu](../msbuild/item-element-msbuild.md) poza cele ma nową `Update` atrybutu. Ponadto ograniczenie `Remove` atrybut został wyeliminowany.
- `Directory.Build.props`to zapewnia dostosowań do projektów w katalogu plik zdefiniowane przez użytkownika. Ten plik jest automatycznie importowany z Microsoft.Common.props, chyba że właściwość `ImportDirectoryBuildTargets` ustawiono **false**. `Directory.Build.targets`zostaną zaimportowane przez Microsoft.Common.targets.
- Opcjonalnie można wyrazić wszystkich metadanych o nazwie, która nie koliduje to z bieżącą listę atrybutów jako atrybut. Aby uzyskać więcej informacji, zobacz [elementu](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nowe funkcje właściwości

- `EnsureTrailingSlash`dodaje ukośnika w ścieżce, jeśli jeszcze nie istnieje.
- `NormalizePath`łączy elementy ścieżki i zapewnia, że ciągu wyjściowego ma poprawny katalog znaków separatora dla bieżącego systemu operacyjnego.
- `NormalizeDirectory`łączy elementy ścieżki, zapewnia ukośnika i zapewnia, że ciągu wyjściowego ma poprawny katalog znaków separatora dla bieżącego systemu operacyjnego.
- `GetPathOfFileAbove`zwraca ścieżkę pliku bezpośrednio po tym. Jest funkcjonalnym odpowiednikiem wywołania`<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Zobacz też
[MSBuild](../msbuild/msbuild.md)
