---
title: Odwołanie do schematu 2.0 pakiet językowy VSIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: douge
ms.workload:
- dagriffe
ms.openlocfilehash: 571f90f31014dcc4d5686483bfc037e458f4a31e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX Language Pack — odwołanie do schematu 2.0

Schematu językowego VSIX zawiera informacje o instalacji zlokalizowanych pakietów VSIX. Ten schemat w wersji 2.0 obsługuje lokalizacja dodatkowe elementy.

## <a name="language-pack-schema"></a>Schemat pakiet językowy

Element główny pliku pakiet języka jest `<PackageLanguagePackManifest>`, z atrybutem `Version`, która jest wersja formatu pakietu języka. W tym temacie opisano w wersji 2.0 w formacie pakietu języka, które jest określone w manifeście przez ustawienie `Version` atrybut na wartość `Version="2.0.0"`. Element główny zawiera dokładnie jeden element podrzędny `<Metadata>` elementu.

### <a name="packagelangaugepackmanifest-element"></a>PackageLangaugePackManifest Element

W ramach `<PackageLanguagePackManifest>` elementu musi istnieć następującego elementu:
|Tytuł|Opis|
|-----------|-----------------|
|`<Metadata>`| Element zawierający dla wszystkich metadanych zlokalizowanego pakietu

### <a name="metadata-element"></a>Element metadanych

W ramach `<Metadata>` element może mieć następujące elementy:
|Tytuł|Opis|
|-----------|-----------------|
|`<DisplayName>`|Zlokalizowana nazwa rozszerzenia do zainstalowania|
|`<Description>`|Zlokalizowany opis rozszerzenia do zainstalowania|
|`<License>`| Ścieżka do zlokalizowanej wersji rozszerzenia licencji|
|`<MoreInfo>`| Łącze do zlokalizowanych informacji o rozszerzeniu|
|`<ReleaseNotes>`| Ścieżka lub łącze do zlokalizowanej wersji w informacjach o wersji|
|`<Icon>`| Ścieżka do ikony rozszerzeń zlokalizowanej wersji|

### <a name="sample-manifest"></a>Manifest próbki

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Zobacz też

|Tytuł|Opis|
|-----------|-----------------|
|[Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)|Pokazuje, jak zapewnić obsługę instalacji zlokalizowanego pakietu VSIX.|
|[Odwołanie do schematu 2.0 rozszerzenia VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)|Manifestu VSIX opisuje zawartość pliku wdrożenia .vsix, dzięki czemu rozszerzenia programu Visual Studio można zainstalować za pomocą **rozszerzenia i aktualizacje** okno dialogowe.|
|[Znajdowanie rozszerzeń programu Visual Studio i korzystanie z nich](../ide/finding-and-using-visual-studio-extensions.md)|Przedstawia sposób użycia **rozszerzenia i aktualizacje** okno dialogowe, aby zainstalować, usunąć aktywować i dezaktywować rozszerzenia.|