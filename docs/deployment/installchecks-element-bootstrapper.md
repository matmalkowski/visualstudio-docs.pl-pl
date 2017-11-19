---
title: "&lt;InstallChecks&gt; elementu (programu inicjującego) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 2a731c504355cbd3869790720af1f67f6c6bf0eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; elementu (programu inicjującego)
`InstallChecks` Elementu obsługuje uruchamianie różnych testów w komputerze lokalnym, aby upewnić się, że wszystkie odpowiednie wymagania wstępne dla aplikacji zostały zainstalowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## <a name="assemblycheck"></a>AssemblyCheck  
 Ten element jest elementem podrzędnym opcjonalne `InstallChecks`. Dla każdego wystąpienia `AssemblyCheck`, inicjujący będzie upewnij się, że zestawu zidentyfikowane przez element istnieje w globalnej pamięci podręcznej zestawów (GAC). Nie zawiera żadnych elementów i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Property`|Wymagany. Nazwa właściwości do przechowywania wyniku. Ta właściwość może być przywoływany testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > elementu](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Wymagany. Pełna nazwa zestawu do sprawdzenia.|  
|`PublicKeyToken`|Wymagany. Formie skróconej klucza publicznego skojarzony z tym silnej nazwy zestawu. Wszystkie zestawy przechowywane w pamięci podręcznej GAC musi mieć nazwę, wersję i klucz publiczny.|  
|`Version`|Wymagany. Wersja zestawu.<br /><br /> Numer wersji ma format \< *wersji głównej*>.\< *wersja pomocnicza*>.\< *Wersja kompilacji*>.\< *wersja poprawki*>.|  
|`Language`|Opcjonalny. Język zlokalizowanej zestawu. Wartość domyślna to `neutral`.|  
|`ProcessorArchitecture`|Opcjonalny. Procesor komputera celem tej instalacji. Wartość domyślna to `msil`.|  
  
## <a name="externalcheck"></a>ExternalCheck  
 Ten element jest elementem podrzędnym opcjonalne `InstallChecks`. Dla każdego wystąpienia `ExternalCheck`, inicjujący wykonania nazwanego programu zewnętrznego w oddzielnych procesach i przechowywać we właściwości wskazywanym przez jego kod zakończenia `Property`. `ExternalCheck`przydaje się wdrażanie złożonych zależności lub gdy jest jedynym sposobem, aby sprawdzić obecność składnika można go utworzyć.  
  
 `ExternalCheck`nie zawiera żadnych elementów i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Property`|Wymagany. Nazwa właściwości do przechowywania wyniku. Ta właściwość może być przywoływany testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > elementu](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Wymagany. Zewnętrzny program do wykonania. Program musi być częścią pakietu dystrybucji Instalatora.|  
|`Arguments`|Opcjonalny. Dostarcza argumenty wiersza polecenia do pliku wykonywalnego o nazwie `PackageFile`.|  
  
## <a name="filecheck"></a>FileCheck  
 Ten element jest elementem podrzędnym opcjonalne `InstallChecks`. Dla każdego wystąpienia `FileCheck`, inicjujący określi, czy istnieje wskazanego pliku i zwraca numer wersji pliku. Jeśli plik nie ma numer wersji, inicjujący ustawia właściwość o nazwie `Property` na 0. Jeśli plik nie istnieje, `Property` nie jest ustawiony na żadnej wartości.  
  
 `FileCheck`nie zawiera żadnych elementów i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Property`|Wymagany. Nazwa właściwości do przechowywania wyniku. Ta właściwość może być przywoływany testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > elementu](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Wymagany. Nazwa znajduje się w pliku.|  
|`SearchPath`|Wymagany. Dysku lub folder, w którym można wyszukać plik. Musi to być ścieżką względną, jeśli `SpecialFolder` przypisano; w przeciwnym razie musi być ścieżką bezwzględną.|  
|`SpecialFolder`|Opcjonalny. Folder, który ma specjalne znaczenie do systemu Windows lub do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Wartość domyślna to interpretować `SearchPath` jako ścieżkę bezwzględną. Prawidłowe wartości są następujące:<br /><br /> `AppDataFolder`. Folder dane aplikacji dla tego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji; specyficzne dla bieżącego użytkownika.<br /><br /> `CommonAppDataFolder`. Folder dane aplikacji, używane przez wszystkich użytkowników.<br /><br /> `CommonFilesFolder`. Folder plików wspólnych dla bieżącego użytkownika.<br /><br /> `LocalDataAppFolder`. Folder dane aplikacji z systemem innym niż roamingu.<br /><br /> `ProgramFilesFolder`. Standardowa folderu Program Files aplikacje 32-bitowe.<br /><br /> `StartUpFolder`. Folder, który zawiera wszystkie aplikacje uruchamiane podczas uruchamiania systemu.<br /><br /> `SystemFolder`. Folder zawierający system 32-bitowych bibliotek DLL.<br /><br /> `WindowsFolder`. Folder zawierający instalacji systemu Windows.<br /><br /> `WindowsVolume`. Dysk lub partycję, która zawiera instalacji systemu Windows.|  
|`SearchDepth`|Opcjonalny. Głębokość w do wyszukania podfoldery dla wskazanego pliku. Wyszukiwanie jest pierwszy głębokość. Wartość domyślna to 0, co ogranicza wyszukiwanie do folderu najwyższego poziomu, określony przez `SpecialFolder` i **SearchPath**.|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 Ten element jest elementem podrzędnym opcjonalne `InstallChecks`. Dla każdego wystąpienia `MsiProductCheck`, inicjujący sprawdza, czy określony instalacji Instalator systemu Microsoft Windows zostało uruchomione, dopóki zostanie zakończona. Wartość właściwości jest ustawiana w zależności od stanu tego zainstalowany produkt. Wskazuje wartość dodatnią produkt jest zainstalowany, 0 lub wartość -1 wskazuje, nie jest zainstalowany. (Zobacz funkcji zestawu SDK Instalatora Windows MsiQueryFeatureState, aby uzyskać więcej informacji.) . Jeśli Instalator Windows nie jest zainstalowany na komputerze, `Property` nie jest ustawiona.  
  
 `MsiProductCheck`nie zawiera żadnych elementów i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Property`|Wymagany. Nazwa właściwości do przechowywania wyniku. Ta właściwość może być przywoływany testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > elementu](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Wymagany. Identyfikator GUID zainstalowany produkt.|  
|`Feature`|Opcjonalny. Identyfikator GUID dla określonych funkcji zainstalowanych aplikacji.|  
  
## <a name="registrycheck"></a>RegistryCheck  
 Ten element jest elementem podrzędnym opcjonalne `InstallChecks`. Dla każdego wystąpienia `RegistryCheck`, inicjujący sprawdza, czy określony klucz rejestru istnieje, i czy ma określoną wartość.  
  
 `RegistryCheck`nie zawiera żadnych elementów i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Property`|Wymagany. Nazwa właściwości do przechowywania wyniku. Ta właściwość może być przywoływany testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > elementu](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Wymagany. Nazwa klucza rejestru.|  
|`Value`|Opcjonalny. Nazwa wartości rejestru do pobrania. Wartość domyślna to aby zwrócić tekst wartości domyślnej. `Value`musi być ciągiem lub wartością DWORD.|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 Ten element jest elementem podrzędnym opcjonalne `InstallChecks`. Dla każdego wystąpienia `RegistryFileCheck`, inicjujący pobiera wersję określony plik, najpierw próby pobrania ścieżki do pliku z określonym kluczu rejestru. Jest to szczególnie przydatne, jeśli chcesz odszukać pliku w katalogu określonym jako wartości w rejestrze.  
  
 `RegistryFileCheck`nie zawiera żadnych elementów i ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Property`|Wymagany. Nazwa właściwości do przechowywania wyniku. Ta właściwość może być przywoływany testu poniżej `InstallConditions` element, który jest elementem podrzędnym elementu `Command` elementu. Aby uzyskać więcej informacji, zobacz [ \<polecenia > elementu](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Wymagany. Nazwa klucza rejestru. Jego wartość jest interpretowana jako ścieżka do pliku, chyba że `File` ustawiono atrybut. Jeśli ten klucz nie istnieje, `Property` nie jest ustawiona.|  
|`Value`|Opcjonalny. Nazwa wartości rejestru do pobrania. Wartość domyślna to aby zwrócić tekst wartości domyślnej. `Value`musi być ciągiem.|  
|`FileName`|Opcjonalny. Nazwa pliku. Jeśli jest określony, wartość uzyskane z klucza rejestru jest założono, że to ścieżka katalogu, a ta nazwa jest dołączany do niego. Jeśli nie zostanie określony, wartość zwracana z rejestru jest założono, że to pełna ścieżka do pliku.|  
|`SearchDepth`|Opcjonalny. Głębokość w do wyszukania podfoldery dla wskazanego pliku. Wyszukiwanie jest pierwszy głębokość. Wartość domyślna to 0, co ogranicza wyszukiwanie do folderu najwyższego poziomu, określonym przez wartość klucza rejestru.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas elementy poniżej `InstallChecks` zdefiniować testy do uruchomienia, nie wykonują je. Aby wykonać testów, należy utworzyć `Command` elementy poniżej `Commands` elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `InstallChecks` elementu, ponieważ jest używany w pliku produktu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 Gdy `InstallChecks` są oceniane, tworzy właściwości. Właściwości są następnie używane przez `InstallConditions` czy pakietu należy zainstalować, pominąć czy zakończyć się niepowodzeniem. W poniższej tabeli wymieniono `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|Jeśli istnieją `FailIf` warunek jest spełniony, pakietu zakończy się niepowodzeniem. Pozostałych warunków nie zostanie obliczone.|  
|`BypassIf`|Jeśli istnieją `BypassIf` warunek jest spełniony, pakietu będą pomijane. Pozostałych warunków nie zostanie obliczone.|  
  
## <a name="predefined-properties"></a>Wstępnie zdefiniowane właściwości  
 W poniższej tabeli wymieniono `BypassIf` i `FailIf` elementy:  
  
|Właściwość|Uwagi|Możliwe wartości|  
|--------------|-----------|---------------------|  
|`Version9X`|Numer wersji systemu operacyjnego Windows 9 X.|4.10 = Windows 98|  
|`VersionNT`|Numer wersji systemu operacyjnego Windows NT.|Major.Minor.ServicePack<br /><br /> 5.0 = Windows 2000<br /><br /> Pakiet 5.1.0 = systemu Windows XP<br /><br /> 5.1.2 = Windows XP Professional z dodatkiem SP2<br /><br /> 5.2.0 = systemu Windows Server 2003|  
|`VersionNT64`|Numer wersji 64-bitowego systemu operacyjnego systemu Windows NT.|Wartość taka sama jak wspomniano wcześniej.|  
|`VersionMsi`|Numer wersji usługi Instalator Windows.|2.0 = Instalatora systemu Windows w wersji 2.0|  
|`AdminUser`|Określa, czy użytkownik ma uprawnienia administratora w systemie operacyjnym systemu Windows NT.|0 = nie uprawnień administratora<br /><br /> 1 = uprawnień administratora|  
  
 Na przykład aby zablokować instalacji na komputerze z systemem Windows 95, należy użyć kodu podobne do poniższych:  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Polecenia > — Element](../deployment/commands-element-bootstrapper.md)   
 [Produkt i pakiet — odwołanie do schematu](../deployment/product-and-package-schema-reference.md)