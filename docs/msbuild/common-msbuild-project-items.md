---
title: "Elementy projektu MSBuild wspólnego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords: MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: "17"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 82d4687a72cb0f13291aa01ff37b91afbcc254e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="common-msbuild-project-items"></a>Wspólne elementy projektów MSBuild
W [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], element nazwany odnosi się do jednego lub więcej plików. Elementy zawierają metadane, takie jak nazwy plików, ścieżki i numery wersji. Wszystkie typy w projektów [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] są wspólne dla kilku elementów. Te elementy są definiowane w microsoft.build.commontypes.xsd pliku.  
  
## <a name="common-items"></a>Wspólne elementy  
 Poniżej znajduje się lista wszystkich wspólne elementy projektów.  
  
### <a name="reference"></a>Tematy pomocy  
 Reprezentuje odwołanie do zestawu (zarządzane) w projekcie.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|HintPath|Opcjonalny ciąg. Względna lub bezwzględna ścieżka zestawu.|  
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana zestawu, na przykład "System.Windows.Forms".|  
|FusionName|Opcjonalny ciąg. Określa nazwę fusion prostą, jak i silne dla elementu.<br /><br /> Jeśli ten atrybut jest obecny, można zaoszczędzić czas, ponieważ plik zestawu nie ma zostać otwarty można uzyskać nazwy fusion.|  
|SpecificVersion|Opcjonalna wartość logiczna. Określa, czy należy odwoływać się tylko do wersji w nazwie połączenia.|  
|Aliasy|Opcjonalny ciąg. Aliasy dla odwołania.|  
|Private|Opcjonalna wartość logiczna. Określa, czy odwołania powinny być kopiowane do folderu wyjściowego. Ten atrybut jest zgodna **Kopiuj lokalnie** właściwości odwołania, który znajduje się w środowisku IDE programu Visual Studio.|  
  
### <a name="comreference"></a>COMReference  
 Reprezentuje składnika modelu COM (niezarządzany) odwołania do projektu.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|Nazwa|Opcjonalny ciąg. Wyświetlana nazwa składnika.|  
|Identyfikator GUID|Opcjonalny ciąg. Identyfikator GUID dla składnika w formularzu {12345678-1234-1234-1234-1234567891234}.|  
|VersionMajor|Opcjonalny ciąg. Główna część numeru wersji składnika. Na przykład "5" w przypadku numer wersji pełnej "5.46".|  
|VersionMinor|Opcjonalny ciąg. Pomocnicza część numeru wersji składnika. Na przykład "46" Jeśli liczba pełną wersję "5.46".|  
|IDENTYFIKATOR LCID|Opcjonalny ciąg. Identyfikator ustawień regionalnych dla składnika.|  
|WrapperTool|Opcjonalny ciąg. Nazwa narzędzia otoki, która jest używana dla składnika, na przykład, "tlbimp".|  
|Izolowane|Opcjonalna wartość logiczna. Określa, czy składnik jest wolny reg składnika.|  
  
### <a name="comfilereference"></a>COMFileReference  
 Reprezentuje listę bibliotek typów, które źródła danych do docelowego ResolvedComreference.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|WrapperTool|Opcjonalny ciąg. Nazwa narzędzia otoki, która jest używana dla składnika, na przykład, "tlbimp".|  
  
### <a name="nativereference"></a>NativeReference  
 Reprezentuje natywnego pliku manifestu lub odwołanie do tego pliku.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|Nazwa|Wymagany ciąg. Podstawowa nazwa pliku manifestu.|  
|HintPath|Wymagany ciąg. Względna ścieżka pliku manifestu.|  
  
### <a name="projectreference"></a>ProjectReference  
 Reprezentuje odwołanie do innego projektu.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana odwołania.|  
|Project|Opcjonalny ciąg. Identyfikator GUID dla odwołania do w formie {12345678-1234-1234-1234-1234567891234}.|  
|Package|Opcjonalny ciąg. Ścieżka pliku projektu, do którego prowadzi odwołanie.|  
  
### <a name="compile"></a>Kompilacji  
 Reprezentuje pliki źródłowe dla kompilatora.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|DependentUpon|Opcjonalny ciąg. Określa plik, który zależy od tego pliku do poprawnej kompilacji.|  
|AutoGen|Opcjonalna wartość logiczna. Wskazuje, czy plik został wygenerowany dla projektu przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE).|  
|Łącze|Opcjonalny ciąg. Ścieżka notational do wyświetlenia, gdy plik znajduje się fizycznie poza wpływ pliku projektu.|  
|Widoczne|Opcjonalna wartość logiczna. Wskazuje, czy należy wyświetlić plik w **Eksploratora rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|CopyToOutputDirectory|Opcjonalny ciąg. Określa, czy można skopiować pliku do katalogu wyjściowego. Dostępne są następujące wartości:<br /><br /> 1.  Nigdy nie<br />2.  Zawsze<br />3.  PreserveNewest|  
  
### <a name="embeddedresource"></a>EmbeddedResource  
 Reprezentuje zasoby do osadzenia w wygenerowanym zestawie.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|DependentUpon|Opcjonalny ciąg. Określa plik, który zależy od tego pliku do poprawnej kompilacji|  
|Generator|Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie.|  
|LastGenOutput|Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny generator plików uruchomione na tym elemencie.|  
|CustomToolNamespace|Wymagany ciąg. Przestrzeń nazw, w której każdy generator działa na tym elemencie plików należy utworzyć kod.|  
|Łącze|Opcjonalny ciąg. Ścieżka notational jest wyświetlana, jeśli plik znajduje się fizycznie poza wpływ projektu.|  
|Widoczne|Opcjonalna wartość logiczna. Wskazuje, czy należy wyświetlić plik w **Eksploratora rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|CopyToOutputDirectory|Opcjonalny ciąg. Określa, czy można skopiować pliku do katalogu wyjściowego. Dostępne są następujące wartości:<br /><br /> 1.  Nigdy nie<br />2.  Zawsze<br />3.  PreserveNewest|  
|LogicalName|Wymagany ciąg. Nazwa logiczna zasobu osadzonego.|  
  
### <a name="content"></a>Zawartość  
 Reprezentuje pliki, które nie są skompilowane w projekcie, ale może być osadzone lub opublikowane wraz z jej.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|DependentUpon|Opcjonalny ciąg. Określa plik, który zależy od tego pliku do poprawnej kompilacji.|  
|Generator|Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie.|  
|LastGenOutput|Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny generator plików, która została uruchomiona na tym elemencie.|  
|CustomToolNamespace|Wymagany ciąg. Przestrzeń nazw, w której każdy generator działa na tym elemencie plików należy utworzyć kod.|  
|Łącze|Opcjonalny ciąg. Ścieżka notational będzie wyświetlana, jeśli plik znajduje się fizycznie poza wpływ projektu.|  
|PublishState|Wymagany ciąg. Stan publikowania zawartości, albo:<br /><br /> -Domyślne<br />— Włączone<br />-Wyłączone<br />-Pliku danych<br />-Wymagań wstępnych|  
|IsAssembly|Opcjonalna wartość logiczna. Określa, czy plik jest zestawem.|  
|Widoczne|Opcjonalna wartość logiczna. Wskazuje, czy należy wyświetlić plik w **Eksploratora rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|CopyToOutputDirectory|Opcjonalny ciąg. Określa, czy można skopiować pliku do katalogu wyjściowego. Dostępne są następujące wartości:<br /><br /> 1.  Nigdy nie<br />2.  Zawsze<br />3.  PreserveNewest|  
  
### <a name="none"></a>Brak  
 Reprezentuje pliki, które powinny mieć żadnej roli w procesie kompilacji.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|DependentUpon|Opcjonalny ciąg. Określa plik, który zależy od tego pliku do poprawnej kompilacji.|  
|Generator|Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie.|  
|LastGenOutput|Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny generator plików uruchomione na tym elemencie.|  
|CustomToolNamespace|Wymagany ciąg. Przestrzeń nazw, w której każdy generator działa na tym elemencie plików należy utworzyć kod.|  
|Łącze|Opcjonalny ciąg. Ścieżka notational będzie wyświetlana, jeśli plik znajduje się fizycznie poza wpływ projektu.|  
|Widoczne|Opcjonalna wartość logiczna. Wskazuje, czy należy wyświetlić plik w **Eksploratora rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|CopyToOutputDirectory|Opcjonalny ciąg. Określa, czy można skopiować pliku do katalogu wyjściowego. Dostępne są następujące wartości:<br /><br /> 1.  Nigdy nie<br />2.  Zawsze<br />3.  PreserveNewest|  
  
### <a name="baseapplicationmanifest"></a>BaseApplicationManifest  
 Reprezentuje podstawowy manifest aplikacji dla kompilacji i zawiera [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] informacje na temat wdrażania zabezpieczeń.  
  
### <a name="codeanalysisimport"></a>CodeAnalysisImport  
 Reprezentuje projektu programu FxCop, aby zaimportować.  
  
### <a name="import"></a>Import  
 Reprezentuje zestawy, których przestrzenie nazw powinny być importowane przez [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Wspólne właściwości projektów MSBuild](../msbuild/common-msbuild-project-properties.md)
