---
title: Managed Extensibility Framework w edytorze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91b507893cf2d17b9885944a766c9c9a8c084a7a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework w edytorze
Edytor jest utworzony przy użyciu składników Managed Extensibility Framework (MEF). Można tworzyć własne składników MEF do rozszerzania edytora, a kod może wykorzystać również składników edytora.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Omówienie Managed Extensibility Framework  
 MEF jest biblioteki .NET, która umożliwia dodawanie i modyfikowanie funkcji aplikacji lub składnika, który wykonuje MEF modelu programowania. Edytor programu Visual Studio zarówno może udostępniać i korzystać z części MEF.  
  
 MEF znajduje się w zestawie System.ComponentModel.Composition.dll programu .NET Framework w wersji 4.  
  
 Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="component-parts-and-composition-containers"></a>Składniki i kompozycji kontenerów  
 Składnik jest klasą lub elementem członkowskim klasy, które można wykonać jedną (lub obie) z następujących czynności:  
  
-   Korzystać z innego składnika  
  
-   Używane przez inny składnik  
  
 Rozważmy na przykład zakupów aplikacja, która ma składnik wpis kolejności, który jest zależna od produktu dostępności danych przez składnik spisu magazynu. W warunkach MEF części spisu można *wyeksportować* produktu dostępność danych i umożliwia części wpisu kolejności *zaimportować* danych. Wpis kolejności i spisu część nie trzeba wiedzieć o innych; *kontenera kompozycji* (udostępniany przez aplikację hosta) jest odpowiedzialny za utrzymanie zbiór eksporty i rozpoznawanie eksportów i importuje.  
  
 Kontener kompozycji <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, zazwyczaj należy przez hosta. Kontener kompozycji przechowuje *katalogu* wyeksportowanego składniki.  
  
### <a name="exporting-and-importing-component-parts"></a>Eksportowanie i Importowanie części  
 Możesz wyeksportować wszystkie funkcje tak długo, jak są one zaimplementowane jako klasa publiczna lub publicznego elementu członkowskiego klasy (właściwości lub metody). Nie masz pochodzić z część z <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Zamiast tego należy dodać <xref:System.ComponentModel.Composition.ExportAttribute> atrybutu w klasie lub element członkowski klasy, która ma zostać wykonane eksportowanie. Ten atrybut określa *umowy* przez które inny składnik części można importować z funkcji.  
  
### <a name="the-export-contract"></a>Kontrakt eksportu  
 <xref:System.ComponentModel.Composition.ExportAttribute> Definiuje jednostki (klasą, interfejsem lub struktury), która jest eksportowany. Zwykle atrybut eksportu przyjmuje parametr, który określa typ eksportu.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Domyślnie <xref:System.ComponentModel.Composition.ExportAttribute> atrybut definiuje kontrakt, który jest typem klasy eksportowanie.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 W tym przykładzie wartość domyślna `[Export]` jest odpowiednikiem atrybutu `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 Możesz też wyeksportować właściwości lub metody, jak pokazano w poniższym przykładzie.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Importowanie eksportu MEF  
 Jeśli chcesz korzystać z eksportu MEF, musisz znać kontraktu (zwykle typ) za pomocą którego on został wyeksportowany, a następnie dodaj <xref:System.ComponentModel.Composition.ImportAttribute> atrybut, który ma tę wartość. Domyślnie atrybut importu przyjmuje jeden parametr, który jest typem klasy modyfikowanego przezeń. Następujące wiersze kodu importu <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> typu.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Pobieranie funkcji edytora z części składników MEF  
 Jeśli istniejący kod jest częścią składników MEF, umożliwia metadanych MEF używać części edytora.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Aby korzystać z funkcji edytora z części składników MEF  
  
1.  Dodaj odwołania do System.Composition.ComponentModel.dll, który znajduje się w globalnej pamięci podręcznej zestawów (GAC), i zestawy edytora.  
  
2.  Dodaj odpowiednie instrukcje using.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Dodaj `[Import]` atrybutu do interfejsu usługi, w następujący sposób.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Po uzyskaniu usługi może wykorzystać jeden z jego składników.  
  
5.  Kiedy została wykonana z zestawu, umieść ją w... \Common7\IDE\Components\ folder instalacji programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)