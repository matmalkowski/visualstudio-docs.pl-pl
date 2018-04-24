# <a name="updating-an-existing-application-for-msbuild-15"></a>Aktualizowanie istniejącej aplikacji 15 MSBuild

W wersjach programu MSBuild przed 15.0 MSBuild został załadowany z globalnej pamięci podręcznej zestawów (GAC) i rozszerzenia programu MSBuild zostały zainstalowane w rejestrze. To zapewnić, że wszystkie aplikacje używana ta sama wersja programu MSBuild i ma dostęp do tej samej procesami, ale uniemożliwił side-by-side instalacji różnych wersji programu Visual Studio.

Aby zapewnić obsługę szybszych instalacji mniejszy, a side-by-side, Visual Studio 2017 r z już miejsca w pamięci GAC MSBuild lub modyfikuje rejestr. Niestety oznacza to, że aplikacje, które chcesz ocenić lub tworzenie projektów za pomocą interfejsu API programu MSBuild nie można niejawnie polegać na instalację programu Visual Studio.

## <a name="using-msbuild-from-visual-studio"></a>Przy użyciu programu MSBuild w programie Visual Studio

Aby upewnić się, że programowe kompilacji z aplikacji zgodne z tymi zrobić w programie Visual Studio lub MSBuild.exe, ładowanie zestawów programu MSBuild w programie Visual Studio i korzystaj z zestawów SDK dostępnych w programie Visual Studio. Pakiet Microsoft.Build.Locator NuGet usprawnia to.

## <a name="using-microsoftbuildlocator"></a>Przy użyciu Microsoft.Build.Locator

Jeśli wszystkie `Microsoft.Build.Locator.dll` z aplikacją, nie należy do dystrybucji innych zestawów programu MSBuild.

Aktualizowanie projektu do MSBuild 15 i locator interfejsu API wymaga kilka zmian w projekcie, opisane poniżej. Aby zapoznać się przykładem zmiany wymagana w celu zaktualizowania projektu, zobacz [zatwierdzeń do repozytorium MSBuildLocator przykładowy projekt](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Zmienianie odwołań MSBuild

W celu zapewnienia, że program MSBuild są ładowane z centralnej lokalizacji, nie należy rozesłać jej zestawy z aplikacją.

Mechanizm zmianę projektu w taki sposób, aby uniknąć obciążania MSBuild z centralnej lokalizacji zależy od tego, jak możesz odwoływać się do programu MSBuild.

#### <a name="using-nuget-packages-preferred"></a>Za pomocą pakietów NuGet (preferowane)

W poniższych instrukcjach przyjęto, że używasz [ `PackageReference`-stylu odwołań NuGet](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files).

Zmień Twoje pliki projektu do odwołania zestawów MSBuild z pakietów NuGet. Określ `ExcludeAssets=runtime` NuGet stwierdzić, że są wymagane tylko w czasie kompilacji zestawy, a nie powinien zostać skopiowany do katalogu wyjściowego.

Wersji głównej i pomocniczej pakietów MSBuild musi być mniejsza lub równa minimalnej wersji programu Visual Studio do obsługi. Jeśli chcesz obsługiwać dowolnej wersji programu Visual Studio 2017 r, odwołania wersja pakietu `15.1.548`.

Na przykład można użyć tego kodu XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="using-extension-assemblies"></a>Używanie zestawów rozszerzenia

Jeśli nie możesz użyć pakietów NuGet, można odwoływać się MSBuild zestawy, które są dystrybuowane za pomocą programu Visual Studio. Jeśli bezpośrednie odwołanie MSBuild upewnij się, że jej nie zostaną skopiowane do katalogu wyjściowego przez ustawienie `Copy Local` do `False`. W pliku projektu to będzie wyglądać następująco:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Przekierowania powiązań

Odwołanie do pakietu Microsoft.Build.Locator automatycznie zapewnia, że aplikacja używa przekierowania wymaganego powiązania wszystkich wersji programu MSBuild zestawów do wersji `15.1.0.0`.

### <a name="ensure-output-clean"></a>Upewnij się, dane wyjściowe czyste

Skompilowanie projektu i kontroli do katalogu wyjściowego, aby upewnić się, że nie zawiera żadnych `Microsoft.Build.*.dll` zestawy (inne niż `Microsoft.Build.Locator.dll`, dodane w następnym kroku).

### <a name="add-package-reference"></a>Dodaj odwołanie do pakietu

Dodaj odwołanie pakiet NuGet do [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.0.7-preview-ge60d679b53</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>Zarejestruj wystąpienie przed wywołaniem MSBuild

Dodaj wywołanie interfejsu API lokalizatora przed wywołaniem dowolnej metody, która używa programu MSBuild.

Najprostszym sposobem, aby to zrobić, jest dodanie wywołania

```c#
MSBuildLocator.RegisterDefaults();
```

w kodzie uruchomienia aplikacji.

Jeśli chcesz dopasowanymi bardziej precyzyjną kontrolę nad ładowanie MSBuild, możesz wybrać wyniku `MSBuildLocator.QueryVisualStudioInstances()` do przekazania do `MSBuildLocator.RegisterInstance()` ręcznie, ale nie jest to zazwyczaj konieczne.
