---
title: Lokalizowanie pakietów VSIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d94e390374ca2eb77b4332b3a5c253acce69f051
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="localizing-vsix-packages"></a>Lokalizowanie pakietów VSIX

Lokalizowanie z pakietu VSIX, tworząc plik Extension.vsixlangpack dla każdego języka docelowego i umieszczanie ich w odpowiednim folderze. Po zainstalowaniu zlokalizowanego pakietu zlokalizowana nazwa rozszerzenia zostanie wyświetlona oraz zlokalizowany opis. Jeśli podasz pliku licencji zlokalizowanych lub adres URL, który wskazuje zlokalizowane informacje są także wyświetlane.

Jeśli zawartość pakietu VSIX zawiera pakiet VSPackage, który dodaje polecenia menu lub innych interfejsu użytkownika, zobacz [lokalizowanie polecenia Menu](../extensibility/localizing-menu-commands.md) informacji o lokalizacji nowych elementów interfejsu użytkownika.

## <a name="directory-structure"></a>Struktura katalogów

 Gdy użytkownik instaluje rozszerzenia **rozszerzenia i aktualizacje** sprawdza najwyższy poziom pakietu VSIX dla folderu, którego nazwa jest zgodna z ustawieniami regionalnymi programu Visual Studio na komputerze docelowym. Jeśli **rozszerzenia i aktualizacje** znajduje a .vsixlangpack plików w folderze, zastępuje on zlokalizowanych wartości w tym pliku odpowiednie wartości w pliku .vsixmanifest. Te wartości są wyświetlane po zainstalowaniu rozszerzenia. Poniższy przykład przedstawia strukturę katalogu pakietu VSIX jest zlokalizowana na hiszpański (es-ES) i francuski (fr-FR).  

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Szablony projektu obsługiwane VSIX w [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generowania manifestu VSIX i nadaj mu nazwę source.extension.vsixmanifest. Gdy program Visual Studio tworzy projekt, kopiuje zawartość tego pliku do Extension.VsixManifest w pakiecie VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Plik Extension.vsixlangpack

Plik Extension.vsixlangpack [VSIX Language Pack schematu 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Ten schemat jest `PackageLanguagePackManifest`, których od razu następuje `Metadata` element podrzędny. Metadane mogą zawierać elementy podrzędne do 6, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, i `Icon`. Te elementy podrzędne odpowiadają `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, i `Icon` elementy podrzędne `Metadata` elementu Extension.vsixmanifest pliku.

Podczas tworzenia pliku vsixlangpack należy ustawić `Include in Vsix` właściwości `true`. W przeciwnym razie tekst zlokalizowanych instalacji zostanie zignorowany.

### <a name="to-set-the-include-in-vsix-property"></a>Aby ustawić uwzględnienia we właściwości pliku Vsix

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Extension.vsixlangpack, a następnie kliknij przycisk **właściwości**.

2.  Siatki właściwości, kliknij przycisk **Include w pliku Vsix**i ustaw jej wartość `true`.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższym przykładzie przedstawiono istotne części pliku Extension.vsixmanifest razem w odpowiednich plikach Extension.vsixlangpack hiszpański. Wartości z pakietu językowego Zastąp wartości w manifeście, jeśli ustawienia regionalne Visual Studio na komputerze docelowym jest ustawiony na język hiszpański.

### <a name="code"></a>Kod

 [Extension.vsixmanifest]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

 [Extension.vsixlangpack]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
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
|[Odwołanie do schematu LanguagePack 2.0 VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Pakietu językowego VSIX zawiera opis informacji o lokalizacji pliku .vsix wdrożenia.|
|[Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Opisuje struktury i zawartości pakietu vsix.|
|[Lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md)|Pokazuje, jak do zlokalizowania inne zasoby tekstu w rozszerzeniu.|