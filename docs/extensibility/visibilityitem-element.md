---
title: VisibilityItem Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85cc2a3d65d5a4763aeca231175201cf55a74b3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="visibilityitem-element"></a>VisibilityItem Element
`VisibilityItem` Określa statyczne widoczności poleceń i pasków narzędzi. Każdy wpis identyfikuje polecenia lub menu a skojarzone polecenie kontekstu interfejsu użytkownika. Visual Studio wykrywa polecenia, menu i paski narzędzi oraz ich widoczności bez ładowania VSPackages, który definiuje ich. Używa IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodę, aby sprawdzić, czy kontekst interfejsu użytkownika poleceń jest aktywny.  
  
 Po załadowaniu pakiet VSPackage Visual Studio oczekuje widoczności poleceń będzie określany przez pakiet VSPackage zamiast `VisibilityItem`. Aby określić dla polecenia widoczność, można zaimplementować jedną <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> obsługi zdarzeń lub <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody, w zależności od tego, jak zostały zaimplementowane polecenia.  
  
 Polecenia lub menu, która ma `VisibilityItem` element jest wyświetlany tylko wtedy, gdy jest aktywny kontekst skojarzony. Jednego polecenia, menu lub pasek narzędzi można skojarzyć z co najmniej jeden kontekst interfejsu użytkownika polecenie umieszczając w niej wpis dla każdej kombinacji kontekst poleceń. Polecenia lub menu jest skojarzony z wielu kontekstów interfejsu użytkownika poleceń, następnie polecenia lub menu jest widoczna gdy dowolny kontekstów interfejsu użytkownika skojarzone polecenie jest aktywny.  
  
 `VisibilityItem` Elementu dotyczy tylko polecenia, menu i pasków narzędzi nie do grup. Element, który nie ma powiązanego `VisibilityItem` element jest widoczny, zawsze, gdy menu nadrzędnego jest aktywny.  
  
## <a name="syntax"></a>Składnia  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikator GUID/identyfikator polecenia.|  
|identyfikator|Wymagany. Identyfikator GUID/identyfikator identyfikator polecenia.|  
|kontekst|Wymagany. Kontekst interfejsu użytkownika, w którym to polecenie jest widoczne.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints` Element Określa widoczność statycznych grupy poleceń i pasków narzędzi.|  
  
## <a name="remarks"></a>Uwagi  
 Standardowa kontekstów interfejsu użytkownika programu Visual Studio są zdefiniowane w *ścieżki instalacji programu Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h plik również jako <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> i <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> klasy. Bardziej szczegółowy zestaw kontekstów interfejsu użytkownika jest zdefiniowany w <xref:Microsoft.VisualStudio.VSConstants> klasy.  
  
## <a name="example"></a>Przykład  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints Element](../extensibility/visibilityconstraints-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)