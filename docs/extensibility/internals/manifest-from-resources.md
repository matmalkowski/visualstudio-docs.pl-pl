---
title: Manifestu z zasobów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 514135e5c6ba932d7b3b4319dd39c1df4e8cb212
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134290"
---
# <a name="manifest-from-resources"></a>Manifestu z zasobów
Plik manifestu z narzędzia zasobów to aplikacja konsolowa, która przyjmuje listę zasobów obrazu (pliki PNG lub .xaml) i generuje plik .imagemanifest, który umożliwia tych obrazów do użycia z usługą obrazów programu Visual Studio. Ponadto to narzędzie można dodać obrazy do istniejących .imagemanifest. To narzędzie jest przydatne w przypadku dodawania obsługę wysokiej rozdzielczości i motywów dla obrazów do rozszerzenia programu Visual Studio. .Imagemanifest wygenerowanego pliku należy objęte i wdrożone w ramach rozszerzenia programu Visual Studio (.vsix).  
  
## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia  
 **Składnia**  
  
 ManifestFromResources /resources:\<katalog1 >;\< Img1 >/Assembly:\<AssemblyName > \<opcjonalnych argumentów >  
  
 **Argumenty**  
  
||||  
|-|-|-|  
|**Nazwa przełącznika**|**Uwagi**|**Wymagany lub opcjonalny**|  
|/Resources|Rozdzielana średnikami lista obrazów lub katalogów. Ta lista zawsze powinna zawierać pełnej listy obrazów, które będą w manifeście. Jeśli tylko częściowej listy wpisów nieuwzględnionych zostaną utracone.<br /><br /> Jeśli plik zasobu paska obrazu, narzędzie będzie podziel go na oddzielne obrazy przed dodaniem każdego subimage do manifestu.<br /><br /> Jeśli obraz jest PNG, zaleca się format nazwy, jak to, aby narzędzie można wypełnić prawo atrybuty dla obrazu: \<Name >.\< Szerokość >. \<Wysokość > PNG.|Wymagane|  
|/ Assembly|Nazwa zestaw zarządzany (nie w tym rozszerzenia), lub ścieżką środowiska uruchomieniowego zestawu macierzystego, który obsługuje zasoby (względem lokalizacji środowiska uruchomieniowego dla manifest).|Wymagane|  
|/ manifestu|Nazwa ma zostać przypisany do .imagemanifest wygenerowanego pliku. Mogą również obejmować ścieżką bezwzględną ani względną, aby utworzyć plik w innej lokalizacji. Domyślna nazwa jest zgodna z nazwą zestawu.<br /><br /> Wartość domyślna: \<bieżący katalog >\\< zestawu\>.imagemanifest|Optional|  
|/guidName|Nazwa ma zostać przypisany do symbolu identyfikatora GUID dla wszystkich obrazów w wygenerowanego manifestu.<br /><br /> Domyślne: AssetsGuid|Optional|  
|/rootPath|Ścieżka katalogu głównego, który musi być odłączony przed utworzeniem zasobu zarządzanego identyfikatorów URI. (Ta flaga jest pomagające w przypadkach, w którym narzędzie pobiera ścieżkę względną identyfikatora URI błąd, co powoduje zasobów, aby nie można załadować).<br /><br /> Wartość domyślna: \<bieżącego katalogu >|Optional|  
|/ Recursive|Ustawienie tej flagi informuje narzędzie rekursywnie Wyszukaj wszystkie katalogi w argumencie /resources. Pominięcie tej flagi spowoduje top-poziomu tylko wyszukiwania katalogów.|Optional|  
|/isNative|Ustawienia tej flagi, gdy argument zestawu jest ścieżką do zestawu macierzystego. Ta flaga należy pominąć w przypadku argumentu zestawu jest nazwą zestawu zarządzanego. (Zobacz sekcja uwagi dodatkowe informacje dotyczące tej flagi).|Optional|  
|/newGuids|Ustawienie tej flagi informuje narzędzie w celu utworzenia nowej wartości dla symbolu identyfikator GUID zawiera obrazy zamiast scalanie jeden z istniejących manifestu.|Optional|  
|/newIds|Ustawienie tej flagi informuje narzędzie do tworzenia nowych wartości symbolu identyfikator dla każdego obrazu zamiast scalanie wartości z istniejących manifestu.|Optional|  
|/ nologo|Ustawienie tej flagi zatrzymuje produktu i prawa autorskie informacje z drukowania.|Optional|  
|/?|Wydrukuj informacji pomocy.|Optional|  
|/help|Wydrukuj informacji pomocy.|Optional|  
  
 **Przykłady**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Uwagi  
  
-   Narzędzie obsługuje tylko pliki PNG i .xaml. Inne typy obraz lub plik zostanie zignorowany. Ostrzeżenie jest generowany dla wszystkich typów nieobsługiwany podczas analizy zasobów. Jeśli nie obsługuje obrazy znajdują się po zakończeniu działania narzędzia analizy zasobów, zostanie wygenerowany błąd  
  
-   Wykonując sugerowanego formatu obrazów PNG, narzędzie ustawi wartość rozmiaru/wymiaru .png rozmiar określony format, nawet jeśli różni się od rozmiaru rzeczywistego obrazu.  
  
-   Format szerokość i wysokość można pominąć w przypadku obrazów PNG, ale narzędzie odczytać rzeczywistej szerokość/wysokość obrazu i ich użyć do wartości rozmiaru/wymiaru obrazu.  
  
-   Uruchomienie tego narzędzia na tym samym paska obrazu wiele razy dla tego samego .imagemanifest spowoduje zduplikowane wpisy manifestu, ponieważ narzędzie próbuje podzielić paska obrazu na autonomicznych obrazów i dodaj je na istniejący manifest.  
  
-   Scalanie (z pominięciem /newGuids lub /newIds) powinien można wykonać tylko dla manifestów wygenerowany przez narzędzie. Manifestów, które zostały dostosowane lub generowane w inny sposób nie może poprawnie scalone.  
  
-   Manifestów, które są generowane dla zestawów natywnych może być konieczne można edytowane ręcznie po generowaniu sprawia, że symbole identyfikator niezgodny z zasobem identyfikatory z plik .rc natywny zestaw.  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 **Manifest proste obrazu**  
  
 Manifest obraz powinien być podobny do tego pliku XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImage" Value="0" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">  
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />  
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```  
  
 **Manifestu obrazu dla paska obrazu**  
  
 Manifestu obrazu dla paska obrazu będzie podobny do tego pliku XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImageStrip_0" Value="1" />  
    <ID Name="MyImageStrip_1" Value="2" />  
    <ID Name="MyImageStrip" Value="3" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">  
      <Source Uri="$(Resources)/MyImageStrip_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">  
      <Source Uri="$(Resources)/MyImageStrip_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists>  
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />  
    </ImageList>  
  </ImageLists>  
</ImageManifest>  
```  
  
 **Manifest obraz natywny zestaw zasobów obrazu**  
  
 Manifestu obrazu dla obrazów natywnych powinien być podobny do tego pliku XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15198 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />  
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />  
    <ID Name="MyImage1" Value="0" />  
    <ID Name="MyImage2" Value="1" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage1)" Type="PNG" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage2)" Type="PNG" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```