---
title: Funkcje właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/21/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc1665b0b5a12f8e1719116e61f13ac915083c0d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31978222"
---
# <a name="property-functions"></a>Funkcje właściwości

W wersji systemu .NET Framework 4 i 4.5 funkcje właściwości może być użyta do oceny skrypty programu MSBuild. Funkcje właściwości można tam, gdzie są wyświetlane właściwości. W przeciwieństwie do zadań funkcje właściwości można używać poza elementów docelowych i są oceniane przed uruchomieniem żadnych docelowych.

 Bez przy użyciu zadań MSBuild, może odczytać czasu systemowego, porównywanie ciągów, dopasowanie wyrażeń regularnych i wykonywać inne akcje w skrypcie kompilacji. MSBuild spróbuje przekonwertować ciągu na liczbę i liczby na ciąg i wprowadzić inne konwersje zgodnie z potrzebami.

## <a name="property-function-syntax"></a>Właściwość Składnia funkcji

Oto trzy rodzaje funkcje właściwości; Każda funkcja ma inną składnię:

- Funkcje właściwości ciągu (wystąpieniem)
- Funkcje właściwości statycznej
- Funkcje właściwości programu MSBuild

### <a name="string-property-functions"></a>Funkcje właściwości ciągu

Wszystkie wartości właściwości kompilacji są tylko wartości ciągu. Można użyć metod ciągów (wystąpieniem) do działania na dowolną wartość właściwości. Na przykład można wyodrębnić nazwy dysku (pierwsze trzy znaki) z właściwości kompilacji, która reprezentuje pełną ścieżkę przy użyciu tego kodu:

```fundamental
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Funkcje właściwości statycznej

W skrypcie kompilacji można uzyskać dostępu do właściwości i metod statycznych wielu klas systemowych. Można pobrać wartości właściwości statycznej, użyj następującej składni, gdzie *klasy* jest nazwa klasy systemu i *właściwość* jest nazwą właściwości.

```fundamental
$([Class]::Property)
```

Na przykład służy następujący kod ustawiający właściwość kompilacji do bieżącej daty i godziny.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Wywołanie metody statycznej, należy użyć następującej składni, gdzie *klasy* jest nazwa klasy systemu *— metoda* jest nazwa metody, i *(parametry)* jest lista parametrów dla metody:

```fundamental
$([Class]::Method(Parameters))
```

Na przykład aby ustawić właściwości kompilacji nowego identyfikatora GUID, możesz użyć tego skryptu:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

W przypadku funkcji statycznej właściwości można użyć dowolnego statycznej metody lub właściwości tych klas systemu:

- System.Byte
- System.Char
- System.Convert
- System.DateTime
- System.Decimal
- System.Double
- System.Enum
- System.Guid
- System.Int16
- System.Int32
- System.Int64
- System.IO.Path
- System.Math
- System.Runtime.InteropServices.OSPlatform
- System.Runtime.InteropServices.RuntimeInformation
- System.UInt16
- System.UInt32
- System.UInt64
- System.SByte
- System.Single
- System.String
- System.StringComparer
- System.TimeSpan
- System.Text.RegularExpressions.Regex
- System.UriBuilder
- System.Version
- Microsoft.Build.Utilities.ToolLocationHelper

Ponadto można użyć następujących metod statycznych i właściwości:

- System.Environment::CommandLine
- System.Environment::ExpandEnvironmentVariables
- System.Environment::GetEnvironmentVariable
- System.Environment::GetEnvironmentVariables
- System.Environment::GetFolderPath
- System.Environment::GetLogicalDrives
- System.IO.Directory::GetDirectories
- System.IO.Directory::GetFiles
- System.IO.Directory::GetLastAccessTime
- System.IO.Directory::GetLastWriteTime
- System.IO.Directory::GetParent
- System.IO.File::Exists
- System.IO.File::GetCreationTime
- System.IO.File::GetAttributes
- System.IO.File::GetLastAccessTime
- System.IO.File::GetLastWriteTime
- System.IO.File::ReadAllText

### <a name="calling-instance-methods-on-static-properties"></a>Wywołanie metody wystąpienia właściwości statyczne

Jeśli dostęp do właściwości statycznej, która zwraca wystąpienie obiektu można wywołać metody wystąpienia tego obiektu. Wywołanie metody wystąpienia, należy użyć następującej składni, gdzie *klasy* jest nazwa klasy systemu *właściwości* jest nazwą właściwości, *— metoda* jest nazwą Metoda, i *(parametry)* jest lista parametrów dla metody:

```fundamental
$([Class]::Property.Method(Parameters))
```

Nazwa klasy musi być w pełni kwalifikowana z przestrzenią nazw.

Na przykład służy następujący kod do ustawienia właściwości kompilacji do bieżącej daty dzisiaj.

```xml
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>
```

### <a name="msbuild-property-functions"></a>Funkcje właściwości programu MSBuild

Kilka metod statycznych w kompilacji jest możliwy do zapewnienia arytmetyczny, bitowy logicznych i obsługa znaków ucieczki. Dostęp do tych metod przy użyciu następującej składni, gdzie *— metoda* jest nazwą metody i *parametry* jest lista parametrów metody.

```fundamental
$([MSBuild]::Method(Parameters))
```

Na przykład aby dodać ze sobą dwie właściwości, które mają wartości liczbowych, należy użyć poniższego kodu.

```fundamental
$([MSBuild]::Add($(NumberOne), $(NumberTwo))
```

Poniżej przedstawiono listę funkcji właściwości programu MSBuild:

|Podpis funkcji|Opis|
|------------------------|-----------------|
|Dodaj Double (double, wartość podwójnej precyzji b)|Dodaj dwa symulacyjnych.|
|Dodaj długi (długo, długi b)|Dodaj dwa wyroby długie.|
|Podwójna odejmowania (double, wartość podwójnej precyzji b)|Odjąć na symulacyjnych dwa.|
|Long odejmowania (długo, długi b)|Odejmowanie dwóch wyroby długie.|
|Podwójna mnożenia (double, wartość podwójnej precyzji b)|Należy pomnożyć symulacyjnych dwa.|
|Long mnożenia (długo, długi b)|Należy pomnożyć dwa wyroby długie.|
|Podwójna dzielenia (double, wartość podwójnej precyzji b)|Podzielić na symulacyjnych dwa.|
|Long dzielenia (długo, długi b)|Dzieli dwie wyroby długie.|
|podwójne Modulo (double, wartość podwójnej precyzji b)|Modulo symulacyjnych dwa.|
|Long Modulo (długo, długi b)|Modulo dwa wyroby długie.|
|ciąg Escape(string unescaped)|Wyjścia ciągu zgodnie z regułami ucieczki w MSBuild.|
|ciąg Unescape (ciąg o znaczeniu zmienionym)|Unescape ciągu zgodnie z regułami ucieczki w MSBuild.|
|int BitwiseOr (int, int pierwszy, sekundy)|Wykonaj bitowej `OR` pierwszego i drugiego (pierwszy &#124; drugi).|
|int BitwiseAnd (int, int pierwszy, sekundy)|Wykonaj bitowej `AND` pierwszego i drugiego (pierwszy i drugi).|
|int BitwiseXor (int, int pierwszy, sekundy)|Wykonaj bitowej `XOR` pierwszego i drugiego (pierwszy ^ drugi).|
|int BitwiseNot(int first)|Wykonaj bitowej `NOT` (~ pierwszy).|
|wartość logiczna IsOsPlatform (ciąg platformString)|Określ, czy bieżąca Platforma systemu operacyjnego jest `platformString`. `platformString` musi być członkiem <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSUnixLike|Wartość true, jeśli bieżący system operacyjny jest systemu Unix.|
|ciąg NormalizePath (ścieżka params ciąg [])|Pobiera pełną ścieżkę postaci kanonicznej podana ścieżka i gwarantuje, że zawiera on znaków separatora katalogu prawidłowe w bieżącym systemie operacyjnym.|
|ciąg NormalizeDirectory (ścieżka params ciąg [])|Pobiera postaci kanonicznej pełną ścieżkę udostępnionego katalogu i zapewnia zawiera znak separatora właściwą dla bieżącego systemu operacyjnego, przy jednoczesnym zapewnieniu jej posiada na końcu ukośnik.|
|ciąg EnsureTrailingSlash(string path)|Jeśli w podanej ścieżce nie ma ukośników, dodać go. Jeśli ścieżka jest pustym ciągiem, nie zostanie zmodyfikowana.|
|ciąg GetPathOfFileAbove (plik ciąg, ciąg startingDirectory)|Wyszukuje plik na podstawie lokalizacji bieżącego pliku kompilacji lub na podstawie `startingDirectory`, jeśli określony.|
|GetDirectoryNameOfFileAbove (startingDirectory ciąg, ciąg fileName)|Lokalizuje plik w katalogu określonym lub lokalizacji w strukturze katalogów powyżej tego katalogu.|
|ciąg MakeRelative (nieistniejący ciąg, ciąg ścieżki)|Sprawia, że `path` względem `basePath`. `basePath` musi być bezwzględną katalogu. Jeśli `path` nie może być wykonane względną, jest zwracany dosłownego wyrażenia. Podobnie jak `Uri.MakeRelativeUri`.|
|ciąg ValueOrDefault (conditionValue ciąg, ciąg defaultValue)|Zwraca ciąg w parametrze "defaultValue" tylko wtedy, gdy parametr "conditionValue" jest pusta, w przeciwnym razie, zwraca wartość conditionValue.|

##  <a name="nested-property-functions"></a>Funkcje zagnieżdżone właściwości

Można łączyć właściwości funkcje do bardziej złożone funkcje, jak w poniższym przykładzie przedstawiono formularz.

```fundamental
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

W tym przykładzie zwraca wartość <xref:System.IO.FileAttributes> `Archive` bitowych (32 lub 0) podane przez ścieżkę pliku `tempFile`. Należy zauważyć, że wartości wyliczenia danych nie może występować według nazwy w funkcjach właściwości. Zamiast tego należy użyć wartości liczbowej (32).

Metadane mogą być umieszczane właściwości zagnieżdżonych funkcji. Aby uzyskać więcej informacji, zobacz [wsadowe](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

`DoesTaskHostExist` Funkcja właściwości w programie MSBuild zwraca, czy host zadań aktualnie jest zainstalowana dla określonych wartości środowiska uruchomieniowego i architektury.

Funkcja ta właściwość ma następującą składnię:

```fundamental
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

`EnsureTrailingSlash` Funkcja właściwości w programie MSBuild dodaje ukośnika, jeśli jeszcze nie istnieje.

Funkcja ta właściwość ma następującą składnię:

```fundamental
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

MSBuild `GetDirectoryNameOfFileAbove` funkcja właściwości szuka pliku w katalogach powyżej bieżącego katalogu w ścieżce.

 Funkcja ta właściwość ma następującą składnię:

```fundamental
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Następujący kod jest przykładem tej składni.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

`GetPathOfFileAbove` Funkcja właściwości w programie MSBuild zwraca ścieżkę pliku bezpośrednio po tym. Jest funkcjonalnym odpowiednikiem wywołania

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Funkcja ta właściwość ma następującą składnię:

```fundamental
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` właściwości funkcja zwraca wartość klucza rejestru. Ta funkcja przyjmuje dwa argumenty, nazwę klucza i wartość name i zwraca wartość z rejestru. Jeśli nie określisz nazwy wartości jest zwracana wartość domyślną.

W poniższych przykładach pokazano, jak ta funkcja jest używana:

```fundamental
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

MSBuild `GetRegistryValueFromView` funkcja właściwości pobiera dane rejestru systemu podanej klucz rejestru, wartości oraz jeden lub więcej uporządkowane widoków rejestru. Klucz i wartość są przeszukiwane w każdym widoku rejestru w kolejności, dopóki nie zostały znalezione.

Składnia dla tej właściwości funkcji jest następująca:

```fundamental
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Windows 64-bitowym systemie operacyjnym przechowuje klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node, który przedstawia widok rejestru klucza HKEY_LOCAL_MACHINE\SOFTWARE aplikacji 32-bitowych.

Domyślnie 32-bitowej aplikacji uruchomionych na WOW64 uzyskuje dostęp do widoku rejestru w 32-bitowych i 64-bitowej aplikacji uzyskuje dostęp do widoku 64-bitowego rejestru.

Dostępne są następujące widoki rejestru:

|Widok rejestru|Definicja|
|-------------------|----------------|
|RegistryView.Registry32|Widok rejestru 32-bitowej aplikacji.|
|RegistryView.Registry64|Widok rejestru 64-bitowej aplikacji.|
|RegistryView.Default|Widok rejestru zgodny proces, który aplikacja jest uruchomiona na.|

Poniżej przedstawiono przykład.

 ```fundamental
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

pobiera dane SLRuntimeInstallPath klucz elemencie ReferenceAssemblies wyszukiwania pierwszy w widoku 64-bitowego rejestru, a następnie w widoku 32-bitowego rejestru.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

MSBuild `MakeRelative` właściwości funkcja zwraca ścieżkę względną drugi ścieżkę względem ścieżki pierwszy. Każda ścieżka może być pliku lub folderu.

Funkcja ta właściwość ma następującą składnię:

```fundamental
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

Następujący kod jest przykładem tej składni.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault

MSBuild `ValueOrDefault` właściwości funkcja zwraca pierwszy argument, o ile nie jest zerowa lub pusta. Jeśli pierwszy argument ma wartość null lub pusta, funkcja zwraca drugi argument.

W poniższym przykładzie pokazano, jak ta funkcja jest używana.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="see-also"></a>Zobacz też

[Właściwości programu MSBuild](../msbuild/msbuild-properties.md)
[Przegląd MSBuild](../msbuild/msbuild.md)
