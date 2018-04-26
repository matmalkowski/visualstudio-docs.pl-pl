---
title: Dostosowywanie kompilacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ea021decfc0940ecaaedde2ecfdde34db833b86
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="customize-your-build"></a>Dostosowywanie kompilacji

Proces kompilacji projektów MSBuild, które używają standardowego (importowanie `Microsoft.Common.props` i `Microsoft.Common.targets`) ma kilka punkty zaczepienia rozszerzeń, których można użyć w celu dostosowania procesu kompilacji.

## <a name="adding-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Dodanie argumentów do wiersza polecenia programu MSBuild wywołań dla projektu

A `Directory.Build.rsp` pliku w lub powyżej katalogu źródłowego zostaną zastosowane do kompilacji z wiersza polecenia projektu. Aby uzyskać więcej informacji, zobacz [pliki odpowiedzi MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props i Directory.Build.targets

W wersjach programu MSBuild przed wersji 15 Jeśli chcesz podać nowych, niestandardowych właściwości do projektów w rozwiązaniu, trzeba było ręcznie Dodaj odwołanie do tej właściwości do każdego pliku projektu w rozwiązaniu. Czy zdefiniować właściwości w *.props* pliku, a następnie zaimportować jawnie *.props* pliku w każdym projekcie w rozwiązaniu, między innymi.

Jednak teraz możesz dodać nową właściwość do każdego projektu w jednym kroku przez zdefiniowaniem go w jednego pliku o nazwie *Directory.Build.props* w folderze głównym, który zawiera źródła. Po uruchomieniu programu MSBuild *Microsoft.Common.props* wyszukuje struktury katalogów dla *Directory.Build.props* plików (i *Microsoft.Common.targets* szuka *Directory.Build.targets*). Jeśli zostanie znaleziony, importuje właściwości. *Directory.Build.props* plik użytkownika, który zawiera dostosowania do projektów w katalogu.

### <a name="directorybuildprops-example"></a>Przykład Directory.Build.props

Na przykład, jeśli chcesz włączyć wszystkie projektów dostęp do nowych Roslyn **/ deterministyczne** funkcji (która jest widoczna w Roslyn `CoreCompile` docelowego za pomocą właściwości `$(Deterministic)`), można wykonać następujące czynności.

1. Utwórz nowy plik w folderze głównym Twojego repozytorium o nazwie *Directory.Build.props*.
2. Dodaj następujący kod XML w pliku.

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. Uruchom program MSBuild. Importy istniejącego projektu *Microsoft.Common.props* i *Microsoft.Common.targets* Znajdź plik i zaimportuj go.

### <a name="search-scope"></a>Zakres wyszukiwania

Podczas wyszukiwania *Directory.Build.props* pliku, program MSBuild przeprowadzi struktura katalogów do góry z lokalizacji projektu (`$(MSBuildProjectFullPath)`), zatrzymywanie po klient zlokalizuje *Directory.Build.props* plik. Na przykład jeśli Twoje `$(MSBuildProjectFullPath)` został *c:\users\username\code\test\case1*, MSBuild zaczyna się wyszukiwanie istnieje i następnie wyszukiwania struktura katalogów w górę, dopóki znajduje się *Directory.Build.props* pliku, tak jak następującą strukturę katalogów.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Lokalizacja pliku rozwiązania nie ma znaczenia *Directory.Build.props*.

### <a name="import-order"></a>Kolejność importu

*Directory.Build.props* jest zaimportowana bardzo wczesnym *Microsoft.Common.props*, więc właściwości zdefiniowane później są niedostępne do niego. Tak należy unikać odwołujących się do właściwości, które nie zostały jeszcze zdefiniowane (i w związku z tym oszacuje pustą).

*Directory.Build.targets* została zaimportowana z *Microsoft.Common.targets* po zaimportowaniu *.targets* pliki z pakietami NuGet. Tak może służyć do zastępowania właściwości oraz zdefiniowanego w większości logiki kompilacji, ale w czasie może być konieczna dostosowań w pliku projektu po zaimportowaniu końcowego.

### <a name="use-case-multi-level-merging"></a>Przypadek użycia: scalanie wielu poziomów

Załóżmy, że ta struktura standardowego rozwiązania:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Może być pożądane mają wspólne właściwości wszystkich projektów *(1)*, typowe właściwości *src* projekty *(2-src)* i wspólnych właściwości  *Testowanie* projekty *(2 test)*.

Dla programu MSBuild poprawnie scalić pliki "wewnętrzna" (*2-src* i *2 test*) z pliku "zewnętrzna" (*1*), weź pod uwagę raz program MSBuild wyszukuje *Directory.Build.props* pliku przestaje dalsze skanowanie. Aby kontynuować skanowania i scalić z zewnętrznym plikiem, umieść to w oba pliki wewnętrzny:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Podsumowanie przez MSBuild ogólne podejście jest następujący:

- Dla żadnego danego projektu MSBuild wyszukuje pierwszy *Directory.Build.props* w górę w strukturze rozwiązania scala go przy użyciu ustawień domyślnych i zatrzymuje skanowanie, aby uzyskać więcej informacji
- Jeśli chcesz, aby wiele poziomów znaleziono i scalić następnie [ `<Import...>` ](../msbuild/property-functions.md#msbuild-getpathoffileabove) (należy pokazanym powyżej) "zewnętrzne" pliku z pliku "wewnętrzne"
- Jeśli plik "zewnętrzne" nie, nie również zaimportować coś powyżej, następnie skanowanie zatrzymuje
- Aby kontrolować proces skanowania scalanie, użyj `$(DirectoryBuildPropsPath)` i `$(ImportDirectoryBuildProps)`

Lub po prostu: pierwszy *Directory.Build.props* którego nie importuje niczego, jest gdzie zatrzymuje program MSBuild.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Domyślnie `Microsoft.Common.props` importuje `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` i `Microsoft.Common.targets` importuje `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. Wartość domyślna `MSBuildProjectExtensionsPath` jest `$(BaseIntermediateOutputPath)`, `obj/`. Jest to mechanizm, który używa NuGet do odwoływania się do tworzenia logiki oferowane przez pakiety, oznacza to, że w czasie przywracania tworzy `{project}.nuget.g.props` pliki, które odwołują się do zawartości pakietu.

Ten mechanizm rozszerzalności można wyłączyć, ustawiając właściwość `ImportProjectExtensionProps` do `false` w `Directory.Build.props` lub przed zaimportowaniem `Microsoft.Common.props`.

> [!NOTE]
> Wyłączenie importów MSBuildProjectExtensionsPath uniemożliwi logiki kompilacji dostarczone w pakietach NuGet z zastosowania do projektu. Niektóre pakiety NuGet wymagają logiki kompilacji do wykonywania ich funkcji i będzie renderowany bezużyteczne po to jest wyłączona.

## <a name="user-file"></a>plik .user

Importuje Microsoft.Common.CurrentVersion.targets `$(MSBuildProjectFullPath).user` Jeśli istnieje, dzięki czemu można tworzyć pliku obok projektu za pomocą tego dodatkowe rozszerzenia. Długoterminowej zmiany, które chcesz sprawdzić do kontroli źródła preferowane zmianę projektu, dzięki czemu nie trzeba wiedzieć o ten mechanizm rozszerzenia przyszłych maintainers.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath i MSBuildUserExtensionsPath

> [!WARNING]
> Korzystanie z tych mechanizmów rozszerzeń utrudnia uzyskanie powtarzalnych kompilacji na komputerach. Spróbuj użyć konfiguracji, które mogą być sprawdzane w systemie kontroli źródła i współdzielona przez wszystkich deweloperów baza kodu.

Według Konwencji wiele podstawowych importowanie plików logiki kompilacji

```
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

przed ich zawartość i

```
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

później. Dzięki temu zainstalowanych zestawów SDK rozszerzyć logiki kompilacji popularne typy projektu.

Tej samej struktury katalogów jest wyszukiwana w `$(MSBuildUserExtensionsPath)`, który jest folderem użytkownika `%LOCALAPPDATA%\Microsoft\MSBuild`. Pliki umieszczone w tym folderze zostaną zaimportowane dla wszystkich kompilacji odpowiedniego typu projektu działać w ramach poświadczeń użytkownika. Można wyłączyć rozszerzenia użytkownika przez ustawienie właściwości o nazwie po importowania pliku we wzorcu `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`. Na przykład ustawienie `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` do `false` uniemożliwiłyby importowanie `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`.

## <a name="customizing-the-solution-build"></a>Dostosowywanie kompilacji rozwiązania

> [!IMPORTANT]
> Dostosowywanie kompilacji rozwiązania w ten sposób ma zastosowanie tylko do narzędzia wiersza polecenia kompilacji z `MSBuild.exe`. On **nie** dotyczą kompilacji w programie Visual Studio.

Gdy MSBuild tworzy plik rozwiązania, najpierw tłumaczy go wewnętrznie w pliku projektu i następnie kompilacje które. Importuje plik wygenerowanego projektu `before.{solutionname}.sln.targets` przed zdefiniowaniem wszystkich obiektów docelowych i `after.{solutionname}.sln.targets` po zaimportowaniu elementów docelowych, tym cele, aby `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` i `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` katalogów.

Na przykład można zdefiniować nowy cel, aby zapisać dziennik niestandardowy komunikat po budynku `MyCustomizedSolution.sln` przez utworzenie pliku w tym samym katalogu o nazwie `after.MyCustomizedSolution.sln.targets` zawiera

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md) [odwołanie MSBuild](../msbuild/msbuild-reference.md)
