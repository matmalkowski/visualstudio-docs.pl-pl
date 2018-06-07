---
title: Pamięci podręcznej schematu edytora XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf3c41c16f904077f884bc6cffcdf0ba97233a1a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572790"
---
# <a name="schema-cache"></a>Pamięci podręcznej schematów

Edytor XML zawiera znajduje się w pamięci podręcznej schematu *%InstallRoot%\Xml\Schemas* katalogu. Pamięci podręcznej schematu jest globalne dla wszystkich użytkowników na tym komputerze i zawiera standardowe schematów XML, które są używane do walidacji dokumentu IntelliSense i XML.

Edytor XML znajduje się też schematy znajduje się w rozwiązaniu, schematy określone w **schematy** pole z dokumentu **właściwości** okno i schematy identyfikowane przez `xsi:schemaLocation` i `xsi:noNamespaceSchemaLocation`atrybutów.

W poniższej tabeli opisano schematów, które są instalowane z edytora XML.

|Nazwa pliku|Opis|
|--------------|-----------------|
|*Catalog.xsd*|Schemat dla plików katalogu schematu edytora XML. Aby uzyskać informacje o wykazów schematów zobacz poniżej.|
|*Plik DotNetConfig.xsd*|Schemat dla plików Web.Config "http://schemas.microsoft.com/.NETConfiguration/v2.0".|
|*MSBUILD.xsd*|Schemat dla programu MSBuild pliki upewnij, "http://schemas.microsoft.com/developer/msbuild/2003".|
|*MSDATA.xsd*|Schematu dla adnotacji XSD dodane przez <xref:System.Data.DataSet> klasy "urn: schemas-microsoft-com: XML-msdata".|
|*msxsl.xsd*|Schemat dla rozszerzenia bloku skryptu XSLT firmy Microsoft, urn: schemas-microsoft-com:xslt.|
|*SnippetFormat.xsd*|Schemat dla plików XML fragmentu kodu. Aby uzyskać przykłady, zobacz *%InstallDir%\VC#\Expansions*.|
|*Soap1.1.xsd*|Schemat dla Simple Object Access Protocol (SOAP) 1.1, http://schemas.xmlsoap.org/soap/envelope/.|
|*Soap1.2.xsd*|Schemat dla Simple Object Access Protocol 1.2.|
|*SiteMapSchema.xsd*|Schemat pliku XML mapy witryny ASP.NET, "http://schemas.microsoft.com/AspNet/SiteMap-File-1.0".|
|*WSDL.xsd*|Schemat dla sieci Web Service Description Language, http://schemas.xmlsoap.org/wsdl/.|
|*xenc.xsd*|Schemat XML, do szyfrowania http://www.w3.org/2000/09/xmldsig#.|
|*XHTML.xsd*|Schemat dla XHTML http://www.w3.org/1999/xhtml.|
|*XLINK.xsd*|Schemat dla XLink1.0, http://www.w3.org/1999/xlink.|
|*XML.xsd*|Schemat opisujący atrybuty XML: Space i XML: lang, http://www.w3.org/XML/1998/namespace.|
|*xmlsig.xsd*|Schemat XML podpisów cyfrowych, http://www.w3.org/2000/09/xmldsig#.|
|*xsdschema.xsd*|Schemat XSD, opisujący http://www.w3.org/2001/XMLSchema.|
|*XSLT.xsd*|Przekształca schematu XML, http://www.w3.org/1999/XSL/Transform.|

## <a name="update-schemas-in-the-cache"></a>Aktualizowanie schematów w pamięci podręcznej
 Edytor ładuje katalog pamięci podręcznej schematu, gdy pakiet edytora XML jest załadowany i oczekuje na zmiany podczas pracy. Jeśli schemat został dodany, jest automatycznie ładowany do indeksu w pamięci znanych schematów. Jeśli schemat został usunięty, zostanie ono automatycznie usunięte z indeksu w pamięci. Jeśli schemat został zaktualizowany, automatycznie unieważnia w pamięci podręcznej tego schematu.

> [!NOTE]
> Ponieważ katalog pamięci podręcznej schematu jest globalny do komputera, należy dodawać tylko tutaj schematów, które standard i przydatne do wszystkich projektów programu Visual Studio, które mogą zostać utworzone na tym komputerze.


 Edytor XML obsługuje również dowolną liczbę schematu katalogu plików w katalogu pamięci podręcznej schematu. Wykazów schematów może wskazywać inne lokalizacje dla schematów, które chcesz wiedzieć o w edytorze. *Catalog.xsd* plików definiuje format pliku wykazu i znajduje się w katalogu pamięci podręcznej schematu. *Catalog.xml* plik jest domyślna i zawiera łącza do innych schematów w *InstallDir %*. Poniżej przedstawiono przykładowy *catalog.xml* pliku:

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%InstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%InstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%InstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

 `href` Atrybut może być dowolnym pliku http lub ścieżka URL wskazującym schematu. Ścieżka do pliku może być względem katalogu dokumentu. Następujące zmienne rozdzielone %%, są rozpoznawane przez Edytor który będzie wdrażany w ścieżce:

-   InstallDir

-   System

-   ProgramFiles

-   Programy

-   CommonProgramFiles

-   ApplicationData

-   CommonApplicationData

-   LCID

Dokument katalogu może zawierać `Catalog` element, który wskazuje innych katalogów. Można użyć `Catalog` elementu do punktu centralnego katalogu, współużytkowane przez zespół lub firmy lub udostępnione partnerów biznesowych w wykazie online. `href` Atrybut jest URL http lub ścieżki pliku innych katalogów. Poniżej przedstawiono przykład `Catalog` elementu:

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

 Katalog można też kontrolować sposób schematy są skojarzone z dokumentów XML za pomocą specjalnych `Association` elementu. Ten element kojarzy schematów, które mają docelowej przestrzeni nazw z rozszerzeniem określonego pliku, które mogą być przydatne, ponieważ w edytorze XML, które nie są automatycznie skojarzeń schematów, które nie mają `targetNamespace` atrybutu. W poniższym przykładzie `Association` element kojarzy schematu dotNetConfig ze wszystkich plików mających rozszerzenie pliku "Konfiguracja":

```xml
<Association extension="config" schema="%InstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Schematy zlokalizowanych
 W wielu przypadkach *catalog.xml* plik nie zawiera wpisy dla zlokalizowanych schematów. Można dodać dodatkowe dane do *catalog.xml* plik do katalogu zlokalizowanego schematu.

 W poniższym przykładzie nowy `Schema` element został utworzony używającej % zmienna % LCID wskaż zlokalizowanych schematu.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Zmienić lokalizację pamięci podręcznej schematu

Można dostosować przy użyciu pamięci podręcznej schematu lokalizację **różne** strona Opcje. Jeśli masz katalog ulubionych schematów, zamiast tego użyć tych schematów można skonfigurować edytora.

> [!NOTE]
> Ta zmiana wpływa tylko bieżącego użytkownika programu Visual Studio.

### <a name="to-change-the-schema-cache-location"></a>Aby zmienić lokalizację pamięci podręcznej schematu

1.  Z **narzędzia** menu, wybierz opcję **opcje**.

2.  Rozwiń węzeł **Edytor tekstu**, rozwiń węzeł **XML**, a następnie kliknij przycisk **różne**.

3.  Kliknij przycisk **Przeglądaj** znajdującego się na **schematy** pola.

4.  Wybierz folder dla pamięci podręcznej schematu, a następnie kliknij przycisk **OK**.

### <a name="to-add-another-directory-of-common-schemas"></a>Aby dodać innego katalogu wspólnej schematów

1.  Edytuj *catalog.xml* pliku w katalogu pamięci podręcznej schematu edytora XML.

2.  Dodaj nową `<Catalog href="..."/>` element, który wskazuje katalog schematów dodatkowych.

3.  Zapisz zmiany.

     Katalog jest automatycznie ładowane.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)