---
title: "Obraz podglądu biblioteki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b699233d0b0ddf14079240da3bd831a172641fba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="image-library-viewer"></a>Podgląd biblioteki obrazów
Narzędzia Visual Studio Image Viewer biblioteki można załadować i wyszukiwać manifestów obrazu, dzięki czemu użytkownik do manipulowania je w taki sam sposób, czy program Visual Studio. Użytkownik może zmienić tła, rozmiarów DPI, duży kontrast i inne ustawienia. Narzędzie również Wyświetla informacje ładowania dla manifest każdego obrazu oraz źródła informacji dla każdego obrazu w manifeście obrazu. To narzędzie jest przydatne w przypadku:  
  
1.  Diagnozowanie błędów  
  
2.  Zapewnienie atrybuty są poprawnie ustawione w manifestach niestandardowego obrazu  
  
3.  Wyszukiwanie obrazów w katalogu obrazów programu Visual Studio, dzięki czemu rozszerzenia programu Visual Studio może używać obrazów, które pasują do stylu programu Visual Studio  
  
 ![Obraz biblioteki podglądu bohater](../../extensibility/internals/media/image-library-viewer-hero.png "bohater podglądu biblioteki obrazów")  
  
 **Moniker obrazu**  
  
 Moniker obrazu (lub krótkiej nazwy w skrócie) jest para GUID:ID unikatowo identyfikujący zasób obrazu lub obraz listy zasobów w bibliotece obrazów.  
  
 **Pliki manifestu obrazu**  
  
 Pliki manifestu (.imagemanifest) obrazu są plików XML, które definiują zestaw zasobów obrazu, krótkie, reprezentujących tych zasobów i rzeczywistego obrazu lub obrazów, które reprezentują każdego zasobu. Manifesty obrazu można zdefiniować obrazy autonomicznej lub listy obrazów do obsługi starszych wersji interfejsu użytkownika. Ponadto są atrybuty, które można ustawić elementu zawartości lub na poszczególnych obrazów za każdego zasobu do zmiany czasu i sposób wyświetlania tych zasobów.  
  
 **Schematu manifestu obrazu**  
  
 Manifest pełny obraz wygląda następująco:  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  
  
 **Symbole**  
  
 Jak zwiększyć czytelność, a obsługa pomocy, manifestu obrazu można użyć symboli dla wartości atrybutu. Symbole są zdefiniowane następująco:  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|||  
|-|-|  
|**Podelement**|**Definicja**|  
|Import|Importuje symbole dany plik manifestu do użycia w bieżącym manifestu.|  
|Identyfikator GUID|Symbol reprezentuje identyfikator GUID i muszą być zgodne, formatowanie identyfikatora GUID.|  
|ID|Symbol reprezentuje identyfikator i musi być nieujemną liczbą całkowitą.|  
|String|Symbol reprezentuje wartość dowolnego ciągu.|  
  
 Symbole jest rozróżniana wielkość liter i do którego istnieje odwołanie przy użyciu składni $(symbol-name):  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Niektóre symbole są wstępnie zdefiniowane dla wszystkich manifestów. Mogą być one używane w atrybucie Uri \<źródło > lub \<Import > elementu do ścieżek odwołania na komputerze lokalnym.  
  
|||  
|-|-|  
|**Symbol**|**Opis**|  
|CommonProgramFiles|Wartość zmiennej środowiskowej % CommonProgramFiles %|  
|LocalAppData|Wartość zmiennej środowiskowej % LocalAppData %|  
|ManifestFolder|Folder zawierający plik manifestu|  
|Moje dokumenty|Pełna ścieżka do folderu Moje dokumenty bieżącego użytkownika|  
|ProgramFiles|Wartość zmiennej środowiskowej % ProgramFiles %|  
|System|Do folderu Windows\System32|  
|WinDir|Wartość zmiennej środowiskowej % WinDir %|  
  
 **Obraz**  
  
 \<Obrazu > element definiuje obrazu, który może odwoływać się krótkiej nazwy. Identyfikator GUID i identyfikator razem tworzą krótką nazwę obrazu. Moniker obrazu musi być unikatowa w bibliotece całego obrazu. Jeśli więcej niż jeden obraz ma danego krótkiej nazwy, pierwsza z nich podczas tworzenia biblioteki jest ten, który jest przechowywany.  
  
 Musi zawierać co najmniej jedno źródło. Mimo że niezależny od rozmiaru źródeł zapewni najlepsze wyniki tożsamość w szerokiej gamie rozmiary, nie są wymagane. Jeśli usługa monitu dla obrazu o rozmiarze nie jest zdefiniowany w \<obrazu > element i nie istnieje źródło niezależny od rozmiaru, usługa Wybierz najlepsze źródło określonego rozmiaru i skalować ją do żądany rozmiar.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Identyfikator GUID|[Wymagane] Identyfikator GUID część moniker obrazu|  
|ID|[Wymagane] Część Identyfikatora moniker obrazu|  
|AllowColorInversion|[Opcjonalne, domyślne true] Wskazuje, czy obraz mogą mieć jego kolorów programowo odwrócony, gdy jest używany w tle ciemny.|  
  
 **Źródło**  
  
 \<Źródło > element definiuje pojedynczy źródła zasób obrazu (XAML i PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Identyfikator URI|[Wymagane] Identyfikator URI, który określa, gdzie można załadować obrazu z. Może być jedną z następujących czynności:<br /><br /> -A [identyfikatora URI elementu Pack](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx) przy użyciu aplikacji: / / / urzędu<br /><br /> -Odwołania zasobu składnika bezwzględne<br /><br /> Ścieżka do pliku zawierającego zasób macierzysty|  
|Tło|[Opcjonalnie] Wskazuje, co na rodzaj tła, którego źródłem jest przeznaczona do użycia.<br /><br /> Może być jedną z następujących czynności:<br /><br /> - *Jasny*: źródło może być używane na jasnym.<br /><br /> - *Ciemny*: źródło może być używany na ciemny tła.<br /><br /> - *HighContrast*: źródło można używać na dowolnym tła w trybie dużego kontrastu.<br /><br /> - *HighContrastLight*: źródło może być używane na jasnym w trybie dużego kontrastu.<br /><br /> -*HighContrastDark*: źródło może być używany na ciemny tła w trybie dużego kontrastu.<br /><br /> Jeśli **tła** atrybut nie jest określony, źródło może być używany na dowolnym tła.<br /><br /> Jeśli **tła** jest *światła*, *ciemny*, *HighContrastLight*, lub *HighContrastDark*, nigdy nie są odwrócone kolory źródła. Jeśli **tła** jest pominięty, lub wartość *HighContrast*, odwracanie kolorów źródło jest kontrolowane przez obrazu **AllowColorInversion** atrybutu.|  
  
 A \<źródło > element może mieć dokładnie jeden opcjonalny następujące elementy podrzędne:  
  
||||  
|-|-|-|  
|**Element**|**Atrybuty (wszystkie wymagane)**|**Definicja**|  
|\<Rozmiar >|Wartość|Źródło będzie używany na potrzeby obrazów dany rozmiar (w jednostkach urządzenia). Obraz będzie kwadratowych.|  
|\<SizeRange >|MinSize, MaxSize|Źródło będzie używany dla obrazów z MinSize MaxSize (w jednostkach urządzenia) włącznie. Obraz będzie kwadratowych.|  
|\<Wymiary >|Szerokość, wysokość|Źródło będzie używany dla obrazów o danym szerokość i wysokość (w jednostkach urządzenia).|  
|\<DimensionRange >|Wartości elementu MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Źródło będzie służyć do obrazów z szerokość/wysokość minimalna szerokość/wysokość maksymalna (w jednostkach urządzenia) włącznie.|  
  
 A \<źródło > element może być również opcjonalne \<NativeResource > podelement, który definiuje \<źródło > który został załadowany z natywny zestaw zamiast zarządzanego zestawu.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Typ|[Wymagane] Typ zasobu natywnego XAML lub PNG|  
|ID|[Wymagane] Część Identyfikatora całkowitą zasobów natywnych|  
  
 **Listy obrazów**  
  
 \<ImageList > element definiuje kolekcją obrazów, które mogą być zwracane w jednej taśmy. Pasek jest oparty na żądanie, zgodnie z potrzebami.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Identyfikator GUID|[Wymagane] Identyfikator GUID część moniker obrazu|  
|ID|[Wymagane] Część Identyfikatora moniker obrazu|  
|Zewnętrzna|[Opcjonalne, wartość domyślna to false] Wskazuje, czy moniker obrazu odwołuje się do obrazu w manifeście bieżącej.|  
  
 Moniker obrazu zawartych w niej ma odwołania zdefiniowane w manifeście bieżącego obrazu. Jeśli nie można odnaleźć obrazu zawartych w bibliotece obrazów, obraz pusty symbol zastępczy będzie używany w jego miejscu.  
  
## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia  
 **Sprawdzanie poprawności manifestu niestandardowego obrazu**  
  
 Aby utworzyć niestandardowy manifest, zaleca się użycie narzędzia ManifestFromResources na automatyczne generowanie manifestu. Aby sprawdzić poprawność niestandardowy manifest, uruchom Image Viewer biblioteki i wybierz Plik > Ustaw ścieżki... Aby otworzyć okno dialogowe z katalogów wyszukiwania. Narzędzie będzie używać katalogów wyszukiwania można załadować obrazu manifestów, ale również użyje on je, aby znaleźć plików .dll, które zawierają obrazów w manifeście, dlatego upewnij się, że obejmują manifestu i katalogi bibliotek DLL w tym oknie dialogowym.  
  
 ![Obraz wyszukiwania podglądu biblioteki](../../extensibility/internals/media/image-library-viewer-search.png "obrazu biblioteki podglądu wyszukiwania")  
  
 Kliknij przycisk **Dodaj...**  wybierz nowe katalogi wyszukiwania do wyszukiwania manifestów oraz ich odpowiednich biblioteki dll. Narzędzie zapamiętuje te katalogi wyszukiwania, a ich można włączyć lub wyłączyć przez zaznaczenie lub usunięcie zaznaczenia katalogu.  
  
 Domyślnie narzędzie spróbuje znaleźć katalogu instalacyjnego programu Visual Studio i dodać tych katalogów do listy katalogów wyszukiwania. Można ręcznie dodać katalogów, które nie może znaleźć narzędzia.  
  
 Po załadowaniu wszystkich manifestów, narzędzie może służyć do przełączania się między **tła** kolory, **DPI**, **duży kontrast**, lub **odcieni szarości** dla obrazy, aby użytkownik wizualnie sprawdzić zasoby obrazu, aby sprawdzić były są wyświetlane poprawnie dla różnych ustawień.  
  
 ![Obraz tła podglądu biblioteki](../../extensibility/internals/media/image-library-viewer-background.png "obrazu tła podglądu biblioteki")  
  
 Jasny, ciemny lub niestandardową wartość można ustawić kolor tła. Wybieranie "Niestandardowego koloru" Otwórz okno dialogowe Wybieranie koloru i Dodawanie niestandardowego koloru u dołu pola kombi tła dla później łatwo odwołania.  
  
 ![Obraz biblioteki podglądu niestandardowego koloru](../../extensibility/internals/media/image-library-viewer-custom-color.png "obrazu biblioteki podglądu niestandardowego koloru")  
  
 Wybieranie krótką nazwę obrazu Wyświetla informacje dla każdego rzeczywistego obrazu za tym krótkiej nazwy w okienku szczegółów obraz po prawej stronie. Okienko umożliwia także użytkownikom kopiowania krótka nazwa według nazwy lub GUID:ID nieprzetworzonej wartości.  
  
 ![Szczegóły obrazu podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-image-details.png "szczegóły obrazu podglądu biblioteki obrazów")  
  
 Informacje wyświetlane dla każdego źródła obrazu zawiera jakiego rodzaju tła, aby go wyświetlić, czy można zastosować motyw lub obsługuje duży kontrast, jakie rozmiary jest nieprawidłowa dla lub czy jest niezależny od rozmiaru i określa, czy obraz pochodzi z natywny zestaw.  
  
 ![Image Viewer biblioteki można motywu](../../extensibility/internals/media/image-library-viewer-can-theme.png "Image Viewer biblioteki można motywu")  
  
 Podczas sprawdzania poprawności manifestu obrazu, zaleca się wdrożenie manifestu i biblioteki DLL w lokalizacjach rzeczywistych obrazu. To sprawdzi, czy wszystkie ścieżki względne są poprawne i Biblioteka obrazów może odnaleźć i załadować manifestu i obrazu biblioteki DLL.  
  
 **Wyszukiwanie w katalogu obrazu KnownMonikers**  
  
 Aby lepiej dopasować stylów programu Visual Studio, rozszerzenie programu Visual Studio można użyć obrazów w Visual Studio obraz katalogu zamiast tworzenia i używania własnych. Rozwiązanie nie muszą obsługiwać te obrazy i gwarantuje obraz ma obrazu zapasowy wysokiej rozdzielczości, powinien wyglądać w wszystkie ustawienia DPI obsługiwanych przez program Visual Studio.  
  
 Podgląd biblioteki obraz umożliwia manifestu ma zostać wyszukany, dzięki czemu użytkownik może odnaleźć krótkiej nazwy, która reprezentuje zasób obrazu i używać tego krótkiej nazwy w kodzie. Aby wyszukać obrazy, wprowadź żądane wyszukiwany termin w polu wyszukiwania, a następnie naciśnij klawisz Enter. Pasek stanu w dolnej części będą wyświetlane, ile dopasowań znaleziono poza całkowita obrazów we wszystkich manifestów.  
  
 ![Obraz biblioteki Podgląd filtru](../../extensibility/internals/media/image-library-viewer-filter.png "obrazu biblioteki Podgląd filtru")  
  
 Podczas wyszukiwania monikerów obrazu w manifestach istniejących, firma Microsoft zaleca Wyszukaj, a następnie użyj tylko monikerów Visual Studio obraz katalogu, inne celowo publicznie monikerów lub własne monikerów. Jeśli używasz monikerów niepubliczne, niestandardowego interfejsu użytkownika może być uszkodzony lub obrazy lub zostały zmienione w nieoczekiwany sposób Jeśli po zmianie lub zaktualizować te niepubliczne monikerów i obrazów.  
  
 Ponadto wyszukiwanie według identyfikatora GUID jest możliwe. Tego typu wyszukiwania przydaje się do filtrowania pozycji listy do pojedynczego manifestu lub pojedynczy podsekcji manifestu manifestu, jeśli zawiera wiele identyfikatorów GUID.  
  
 ![Obraz biblioteki Podgląd filtru GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "obrazu biblioteki Podgląd filtru identyfikatora GUID")  
  
 Na koniec wyszukiwanie według Identyfikatora możliwe jest również.  
  
 ![Identyfikator filtru podglądu biblioteki obrazów](../../extensibility/internals/media/image-library-viewer-filter-id.png "identyfikator filtru podglądu biblioteki obrazów")  
  
## <a name="notes"></a>Uwagi  
  
-   Domyślnie narzędzie będzie pobierać w kilku manifestów obrazu w katalogu instalacji programu Visual Studio. Jest tylko jedno z nich ma publicznie dostępne monikerów **Microsoft.VisualStudio.ImageCatalog** manifestu. Identyfikator GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (czy **nie** zastąpienie tego identyfikatora GUID w niestandardowy manifest) typu: KnownMonikers  
  
-   Narzędzie podejmuje uruchamiania, aby załadować wszystkich manifestów obrazu, który odnajdzie, więc może potrwać kilka sekund dla aplikacji, aby pojawia się. Podczas ładowania manifesty również może być wolne lub nieodpowiadający.  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 To narzędzie nie generuje żadnego wyniku.