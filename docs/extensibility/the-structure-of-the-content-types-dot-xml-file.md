---
title: Struktura pliku XML [Content_types] | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 08f1bb76f27f7ae0923eed43339f656c90f4856f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Struktura pliku XML [Content_types]
Zawiera informacje o rodzajach zawartość pakietu VSIX. Do zainstalowania pakietu Visual Studio korzysta z pliku XML [Content_Types], ale nie jest instalowana w samym pliku.  
  
> [!NOTE]
>  Chociaż ten temat dotyczy tylko pliki XML [typ_zawartości], które są używane w pakietach VSIX, typ pliku XML [Content_Types] wchodzi w skład *otwarte konwencje pakietów (OPC)* standardowa. Aby uzyskać więcej informacji, zobacz [OPC: A nowe standardowe dla pakietów danych](http://go.microsoft.com/fwlink/?LinkID=148207) w witrynie MSDN.  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano elementu głównego i jego atrybuty i elementy podrzędne.  
  
### <a name="root-element"></a>Element główny  
  
|Element|Opis|  
|-------------|-----------------|  
|`Types`|Zawiera elementy podrzędne, które wylicza typy plików w pakiecie VSIX.|  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Xmlns`|(Wymagane). Lokalizacja schematu używane dla tego pliku XML [Content_Types].|  
  
### <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|http://schemas.openformats.org/Package/2006/Content-Types|Lokalizacja schematu typy zawartości.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 `Types` Element może zawierać dowolną liczbę `Default` elementów.  
  
|Element|Opis|  
|-------------|-----------------|  
|`Default`|Opisuje typ zawartości w pakiecie VSIX. Każdy typ pliku w pakiecie muszą mieć własny `Default` elementu.|  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Extension`|Rozszerzenie nazwy pliku plików w pakiecie VSIX.|  
|`ContentType`|Opisuje typ zawartości skojarzonej z rozszerzeniem nazwy pliku.|  
  
### <a name="attribute-name-attribute"></a>{Nazwa atrybutu} Atrybut  
 Visual Studio rozpoznawane `ContentType` wartości skojarzonych z nim `Extension` typów.  
  
|Rozszerzenia|Typ zawartości|  
|---------------|-----------------|  
|txt|zwykły tekst|  
|pkgdef|zwykły tekst|  
|XML|tekstu/xml|  
|vsixmanifest|tekstu/xml|  
|htm i html|tekst i html|  
|RTF|Aplikacja/rtf|  
|plik PDF|Aplikacja/pdf|  
|plik GIF|obraz/gif|  
|jpg lub jpeg|Obraz/jpg|  
|TIFF|obraz/tiff|  
|vsix|Aplikacja/zip|  
|ZIP|Aplikacja/zip|  
|biblioteki dll|application/octet-stream|  
|wszystkie typy plików|application/octet-stream|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Następujący plik .xml [Content_Types] w tym artykule opisano typowy pakietu VSIX.  
  
### <a name="code"></a>Kod  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Odwołanie do schematu 1.0 rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Nowy Standard pakowanie danych](http://go.microsoft.com/fwlink/?LinkID=148207)