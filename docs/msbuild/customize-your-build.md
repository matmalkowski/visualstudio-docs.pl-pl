---
title: Dostosowywanie kompilacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 06/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5b11acd4360aa86d4727a4c697a56eaa753d522c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="customize-your-build"></a>Dostosowywanie kompilacji
W wersjach programu MSBuild przed wersji 15 Jeśli chcesz podać nowych, niestandardowych właściwości do projektów w rozwiązaniu, trzeba było ręcznie Dodaj odwołanie do tej właściwości do każdego pliku projektu w rozwiązaniu. Czy zdefiniować właściwości w *.props* pliku, a następnie zaimportować jawnie *.props* pliku w każdym projekcie w rozwiązaniu, między innymi.

Jednak teraz możesz dodać nową właściwość do każdego projektu w jednym kroku przez zdefiniowaniem go w jednego pliku o nazwie *Directory.Build.props* w katalogu głównym Twojego repozytorium. Po uruchomieniu programu MSBuild *Microsoft.Common.props* wyszukuje struktury katalogów dla *Directory.Build.props* plików (i *Microsoft.Common.targets* szuka *Directory.Build.targets*). Jeśli zostanie znaleziony, importuje właściwości. *Directory.Build.props* plik użytkownika, który zawiera dostosowania do projektów w katalogu.

## <a name="directorybuildprops-example"></a>Przykład Directory.Build.props
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
3. Run MSBuild. Importy istniejącego projektu *Microsoft.Common.props* i *Microsoft.Common.targets* Znajdź plik i zaimportuj go.

## <a name="search-scope"></a>Zakres wyszukiwania
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

## <a name="import-order"></a>Kolejność importu

*Directory.Build.props* jest zaimportowana bardzo wczesnym *Microsoft.Common.props*, więc właściwości zdefiniowane później są niedostępne do niego. Tak należy unikać odwołujących się do właściwości, które nie zostały jeszcze zdefiniowane (i w związku z tym oszacuje pustą).

*Directory.Build.targets* została zaimportowana z *Microsoft.Common.targets* po zaimportowaniu *.targets* pliki z pakietami NuGet. Tak może służyć do zastępowania właściwości oraz zdefiniowanego w większości logiki kompilacji, ale w czasie może być konieczna dostosowań w pliku projektu po zaimportowaniu końcowego.

## <a name="use-case-multi-level-merging"></a>Przypadek użycia: scalanie wielu poziomów

Załóżmy, że ta struktura standardowego rozwiązania:

````
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
````

Może być pożądane mają wspólne właściwości wszystkich projektów *(1)*, typowe właściwości *src* projekty *(2-src)*i wspólnych właściwości  *Testowanie* projekty *(2 test)*.

Dla programu MSBuild poprawnie scalić pliki "wewnętrzna" (*2-src* i *2 test*) z pliku "zewnętrzna" (*1*), weź pod uwagę raz program MSBuild wyszukuje *Directory.Build.props* pliku przestaje dalsze skanowanie. Aby kontynuować skanowania i scalić z zewnętrznym plikiem, umieść to w oba pliki wewnętrzny:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Podsumowanie przez MSBuild ogólne podejście jest następujący:

- Dla żadnego danego projektu MSBuild wyszukuje pierwszy *Directory.Build.props* w górę w strukturze rozwiązania scala go przy użyciu ustawień domyślnych i zatrzymuje skanowanie, aby uzyskać więcej informacji
- Jeśli chcesz, aby wiele poziomów znaleziono i scalić następnie [ `<Import...>` ](../msbuild/property-functions.md#msbuild-getpathoffileabove) (należy pokazanym powyżej) "zewnętrzne" pliku z pliku "wewnętrzne"
- Jeśli plik "zewnętrzne" nie, nie również zaimportować coś powyżej, następnie skanowanie zatrzymuje
- Aby kontrolować proces skanowania scalanie, użyj `$(DirectoryBuildPropsPath)` i`$(ImportDirectoryBuildProps)`

Lub po prostu: pierwszy *Directory.Build.props* którego nie importuje niczego, jest gdzie zatrzymuje program MSBuild.

## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
