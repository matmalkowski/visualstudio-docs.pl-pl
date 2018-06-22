---
title: Co&#39;s nowe w programie MSBuild 15 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd8c5100158b5761047d38e10f953fc832e0ce2b
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302887"
---
# <a name="whats-new-in-msbuild-15"></a>What's New in 15 MSBuild

MSBuild jest teraz dostępna jako część [.NET Core SDK](https://www.microsoft.com/net/download/core) i można tworzyć projektów .NET Core w systemie Windows, macOS i Linux.

## <a name="changed-path"></a>Zmieniona ścieżka

 Program MSBuild został zainstalowany w folderze w każdej wersji programu Visual Studio. Na przykład `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild`. Można również użyć następujące modułu programu PowerShell, aby zlokalizować MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 Program MSBuild nie jest już zainstalowane w globalnej pamięci podręcznej zestawów. Aby odwołać MSBuild programowo, należy użyć pakietów NuGet.

## <a name="changed-properties"></a>Zmiany właściwości

 Następujące właściwości programu MSBuild zostały zaktualizowane z powodu nowego numeru wersji.

- `MSBuildToolsVersion` w tej wersji narzędzi jest 15.0. Wersja zestawu jest 15.1.0.0.

- `MSBuildToolsPath` nie ma położenie ustalone. Domyślnie znajduje się w folderze MSBuild\15.0\Bin względną wobec lokalizacji instalacji programu Visual Studio, ale godzina instalacji programu Visual Studio można zmienić lokalizacji instalacji.

- `ToolsVersion` Nie ustawiono wartości w rejestrze.

- `SDK35ToolsPath` i `SDK40ToolsPath` właściwości wskaż zestawu .NET Framework SDK, który jest spakowany w tej wersji programu Visual Studio (na przykład 10.0A dla narzędzi 4.X).

## <a name="updates"></a>Aktualizacje

- [Element projektu](../msbuild/project-element-msbuild.md) ma nową `SDK` atrybutu. Również `Xmlns` atrybut teraz jest opcjonalne. Aby uzyskać więcej informacji, zobacz [jak: zestawy SDK projektu MSBuild użyj](../msbuild/how-to-use-project-sdk.md), a także [pakietów, metadane i platform](/dotnet/core/packages) i [dodatki do csproj format .NET Core](/dotnet/core/tools/csproj).
- [Pozycja elementu](../msbuild/item-element-msbuild.md) poza cele ma nową `Update` atrybutu. Ponadto ograniczenie `Remove` atrybut został wyeliminowany.
- `Directory.Build.props` to zapewnia dostosowań do projektów w katalogu plik zdefiniowane przez użytkownika. Ten plik jest automatycznie importowany z Microsoft.Common.props, chyba że właściwość `ImportDirectoryBuildTargets` ustawiono **false**. `Directory.Build.targets` zostaną zaimportowane przez Microsoft.Common.targets.
- Opcjonalnie można wyrazić wszystkich metadanych o nazwie, która nie koliduje to z bieżącą listę atrybutów jako atrybut. Aby uzyskać więcej informacji, zobacz [elementu](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nowe funkcje właściwości

- `EnsureTrailingSlash` dodaje ukośnika w ścieżce, jeśli jeszcze nie istnieje.
- `NormalizePath` łączy elementy ścieżki i zapewnia, że ciągu wyjściowego ma poprawny katalog znaków separatora dla bieżącego systemu operacyjnego.
- `NormalizeDirectory` łączy elementy ścieżki, zapewnia ukośnika i zapewnia, że ciągu wyjściowego ma poprawny katalog znaków separatora dla bieżącego systemu operacyjnego.
- `GetPathOfFileAbove` zwraca ścieżkę pliku bezpośrednio po tym. Jest funkcjonalnym odpowiednikiem wywołania `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Zobacz też
[MSBuild](../msbuild/msbuild.md)
