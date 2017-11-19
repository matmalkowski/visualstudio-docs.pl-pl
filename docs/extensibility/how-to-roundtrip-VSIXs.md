---
title: "Porady: komunikacja dwukierunkowa rozszerzeń dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
caps.latest.revision: "1"
author: willbrown
ms.author: willbrown
manager: justinclareburt
ms.openlocfilehash: 99bdd5a0f31b9cbccd84a7c05f6d3cdcc0c267f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Porady: dzięki rozszerzenia zgodny z programu Visual Studio 2017 i programu Visual Studio 2015

Tym dokumencie opisano sposób wprowadzania projektów rozszerzalności obustronne między Visual Studio 2015 i Visual Studio 2017 r. Po zakończeniu uaktualnienia, projekt będzie można otworzyć, kompilacji, zainstalować i uruchomić w Visual Studio 2015 i Visual Studio 2017 r.  Jako odwołanie, można znaleźć niektórych rozszerzeń, które można przesyłania danych między Visual Studio 2015 i Visual Studio 2017 [tutaj](https://github.com/Microsoft/VSSDK-Extensibility-Samples) w przykładach rozszerzalności firmy Microsoft.

Jeśli planujesz kompilacji w programie Visual Studio 2017, ale ma wyjściowego pliku VSIX do uruchamiania w Visual Studio 2015 i Visual Studio 2017, odwoływać się do [dokumentu migracji rozszerzenia](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

>**Uwaga:** z powodu zmian w programie Visual Studio między wersjami, kilka rzeczy, które działały w jednej wersji nie będzie działać innego. Upewnij się, że próbujesz uzyskać dostęp do funkcji dostępnych w obu wersjach lub będzie miał rozszerzenie nieoczekiwane wyniki.

Poniżej przedstawiono omówienie poszczególnych czynności, które będzie ukończyć w tym dokumencie VSIX przesyłania danych:

1. Zaimportuj poprawną pakietów NuGet.
2. Aktualizowanie manifestu rozszerzenia:
    * Docelowy instalacji
    * Wymagania wstępne
3. CSProj aktualizacji:
    * Aktualizacja `<MinimumVisualStudioVersion>`.
    * Dodaj `<VsixType>` właściwości.
    * Dodaj właściwość debugowania `($DevEnvDir)` 3 razy.
    * Dodawanie warunków do importowania elementów docelowych i narzędzia kompilacji.

4. Tworzenie i testowanie

## <a name="environment-setup"></a>Konfigurowanie środowiska

Tym dokumencie przyjęto założenie, że mają zainstalowane na tym komputerze następujące elementy:

* Visual Studio 2015 z zainstalowany zestaw SDK programu VS
* Visual Studio 2017 z obciążeniem rozszerzalności zainstalowany

## <a name="recommended-approach"></a>Zalecane podejście

Zdecydowanie zaleca się uruchomić uaktualnienie z programu Visual Studio 2015, zamiast programu Visual Studio 2017 r. Największą zaletą tworzenia w programie Visual Studio 2015 jest zapewnienie odwołuje zestawy, które nie są dostępne w programie Visual Studio 2015. Jeśli zrobisz Programowanie w Visual Studio 2017, istnieje ryzyko, że może powodować zależności zestawu, który istnieje tylko w programie Visual Studio 2017 r.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Upewnij się, że nie ma odwołania do pliku project.json

W dalszej części tego dokumentu firma Microsoft powoduje wstawienie instrukcje importu warunkowe w pliku *.csproj.  To nie będzie działać, jeśli Twoje odwołań NuGet są przechowywane w pliku project.json. Tak zaleca się przenieść wszystkich odwołań NuGet do pliku packages.config.
Jeśli projekt zawiera plik project.json:

* Zanotuj odwołań w pliku project.json.
* W Eksploratorze rozwiązań Usuń plik project.json z projektu.
    * Spowoduje to usunięcie pliku project.json i usuń go z projektu.
* Dodaj ponownie odwołań NuGet do projektu.
    * Kliknij prawym przyciskiem myszy w ramach rozwiązania i wybierz polecenie **Zarządzaj pakietami NuGet rozwiązania...**
    * Visual Studio automatycznie tworzy w pliku packages.config w

>**Uwaga:** Jeśli projekt zawiera pakiety EnvDTE, ich może być konieczne można dodać, klikając prawym przyciskiem myszy **odwołania** wybranie **Dodaj odwołanie** i dodać odpowiednie odwołanie.  Za pomocą pakietów NuGet może utworzyć błędy podczas próby skompilowanie projektu.

## <a name="adding-appropriate-build-tools"></a>Dodawanie narzędzia odpowiednie kompilacji

Aby upewnić się, że należy dodać narzędzia kompilacji, które pozwoli nam kompilowanie i debugowanie odpowiednio. Firma Microsoft opracowała zestawu dla tego Microsoft.VisualStudio.Sdk.BuildTasks wywołana.

Do tworzenia i wdrażania VSIXv3 w programie Visual Studio 2015 i 2017, potrzebujesz następujących pakietów NuGet:

Wersja | Narzędzia wbudowanych
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Aby to zrobić:

* Dodaj pakiet NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 do projektu.
* Jeśli projekt nie zawiera Microsoft.VSSDK.BuildTools, należy go dodać.
* Upewnij się, wersja Microsoft.VSSDK.BuildTools jest 15.x lub nowszej.

## <a name="update-extension-manifest"></a>Aktualizowanie manifestu rozszerzenia

### <a name="1-installation-targets"></a>1. Instalacji elementów docelowych

Musimy Przekaż programowi Visual Studio, które wersje pod kątem tworzenia pliku VSIX.  Zazwyczaj te odwołania są zarówno do wersji 14.0 (Visual Studio 2015) lub 15.0 (Visual Studio 2017).  W tym przypadku chcemy VSIX, które zainstaluje rozszerzenie dla obu, więc musimy korzystać z obu wersji kompilacji.  Jeśli chcesz, aby Twoje VSIX, aby skompilować i zainstalować w wersjach starszych niż 14.0, można to zrobić przez ustawienie numer wcześniejszej wersji; Jednak w wersji 10.0 i starsze nie są już obsługiwane.

* Otwórz plik Source.Extension.vsixmanifest,a w programie Visual Studio.
* Otwórz **zainstalować obiekty docelowe** kartę.
* Zmień **zakres wersji** do [14,0, 16,0).  "[" Informuje Visual Studio, aby obejmują wersje 14,0 i wszystkie poza go.  ")" Informuje Visual Studio, aby uwzględnić wszystkie wersje 15.0 do, z wyjątkiem wersji 16.0.
* Zapisz wszystkie zmiany i zamknij wszystkie wystąpienia programu Visual Studio.

![Obraz przedstawiający elementy docelowe instalacji](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Dodawanie wymagań wstępnych do pliku extension.vsixmanifest

Wymagania wstępne są nową funkcją z programu Visual Studio 2017 r.  W takim przypadku należy edytorze programu Visual Studio Core jako warunek wstępny. Ponieważ projektanta programu Visual Studio 2015 VSIX nie obsługuje nowe `Prerequisites` sekcji, należy edytować tej części ręcznie w kodzie XML.  Alternatywnie można otworzyć programu Visual Studio 2017 i użyj projektanta manifestu zaktualizowane, aby wstawić wymagań wstępnych.

Aby to zrobić ręcznie:

* Przejdź do katalogu projektu w Eksploratorze plików.
* Otwórz `extension.vsixmanifest` plik w edytorze tekstów.
* Dodaj następujący tag:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Zapisz i zamknij plik.

>**Uwaga:** Jeśli chcesz to zrobić za pomocą projektanta VSIX w Visual Studio 2017, musisz ręcznie edytować wymagań wstępnych wersję, aby upewnić się, jest zgodny ze wszystkimi wersjami programu Visual Studio 2017 r.  Jest to spowodowane projektanta powoduje wstawienie minimalna wersja jako bieżącej wersji programu Visual Studio (na przykład 15.0.26208.0).  Jednak ponieważ inni użytkownicy mogą mieć starszej wersji, można ręcznie edytować tej do 15.0.

W tym momencie plik manifestu powinien wyglądać następująco:

![Przykładowe wymagania wstępne](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modyfikowanie pliku projektu (myproject.csproj)

Zdecydowanie zaleca się zawierają odwołanie do modyfikacji .csproj otwarte podczas wykonywania tego kroku.  Kilka przykładów można znaleźć [tutaj](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Wybierz wszystkie próbki rozszerzalności, Znajdź pliku .csproj dla odwołania i wykonaj następujące czynności:

* Przejdź do katalogu projektu w Eksploratorze plików.
* Otwórz plik myproject.csproj za pomocą edytora tekstu.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Aktualizacja MinimumVisualStudioVersion

* Ustaw wersję programu visual studio minimalna do `$(VisualStudioVersion)` i Dodaj dla niego instrukcji warunkowej.  Dodaj znaczniki, jeśli nie istnieją.  Upewnij się, że tagi są ustawione zgodnie z poniższymi instrukcjami:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Dodaj właściwość VsixType

* Dodaj następujący tag `<VsixType>v3</VsixType>` do grupy właściwości.

>**Uwaga:** zalecane jest dodawanie to poniżej `<OutputType></OutputType>` tagu.

### <a name="3-add-the-debugging-properties"></a>3. Dodaj właściwości debugowania

* Dodaj grupę następujące właściwości:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Usuń wszystkie wystąpienia następujące z pliku .csproj oraz innych. csproj.user plików:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Dodawanie warunków do importowania narzędzia kompilacji

* Dodać dodatkowe instrukcje warunkowego `<import>` tagi, które zawierają odwołanie Microsoft.VSSDK.BuildTools.  W tym celu wstawianie `'$(VisualStudioVersion)' != '14.0' And` z przodu instrukcja warunku.  Instrukcje te będą wyświetlane w nagłówku i stopce plik csproj.

Na przykład:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201… Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…/>
```

* Dodać dodatkowe instrukcje warunkowego `<import>` tagi, które mają Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  W tym celu wstawianie `'$(VisualStudioVersion)' == '14.0' And` z przodu instrukcja warunku. Instrukcje te będą wyświetlane w nagłówku i stopce plik csproj.

Na przykład:

```xml
<Import Project="packages\ Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0… Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…/>
```

* Dodać dodatkowe instrukcje warunkowego `<Error>` tagi, które zawierają odwołanie Microsoft.VSSDK.BuildTools.  W tym celu wstawianie `'$(VisualStudioVersion)' != '14.0' And` z przodu instrukcja warunku. Instrukcje te będą wyświetlane w stopce plik csproj.

Na przykład:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…/>
```

* Dodać dodatkowe instrukcje warunkowego `<Error>` tagi, które mają Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  W tym celu wstawianie `'$(VisualStudioVersion)' == '14.0' And` z przodu instrukcja warunku. Instrukcje te będą wyświetlane w stopce plik csproj.

Na przykład:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\ Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…/>
```

* Zapisz plik csproj i zamknij go.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Testowanie instaluje rozszerzenia w Visual Studio 2015 i Visual Studio 2017 r.

W tym momencie projektu należy rozpocząć tworzenie VSIXv3, który można zainstalować na Visual Studio 2015 i Visual Studio 2017 r.

* Otwórz projekt w programie Visual Studio 2015
* Tworzenie projektu i upewnij się, w danych wyjściowych, która VSIX tworzy poprawnie
* Przejdź do katalogu projektu
* Otwórz pojemnika -> folderu debugowania
* Kliknij dwukrotnie plik VSIX i zainstaluj rozszerzenie w Visual Studio 2015 i Visual Studio 2017 r.
* Upewnij się, że rozszerzenie w narzędzia -> rozszerzenia i aktualizacje w sekcji "Installed".
* Próba użycia uruchomić rozszerzenia, aby sprawdzić, czy działa

![Znajdowanie VSIX](media/finding-a-VSIX-example.png)

>**Uwaga:** Jeśli projekt zawiesza się. Zamknij program Visual Studio "otwierania pliku" force wiadomości, przejdź do katalogu projektu, Pokaż ukryte foldery i usuń folder VS.
