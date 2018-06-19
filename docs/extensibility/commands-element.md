---
title: Polecenia elementu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d905914c9819671cf8c77d81ec8d51302467a9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108485"
---
# <a name="commands-element"></a>Element poleceń
Reprezentuje kolekcję poleceń na pasku narzędzi pakiet VSPackage. Kolekcja może mieć maksymalnie pięć podpunkty w następujący sposób: menu, grup przycisków, kombinacje i bitmapy.  
  
 Każdy podsekcji elementu podrzędnego, na przykład \<Menu >, jest identyfikowany przez identyfikator unikatowy polecenia, który jest identyfikatorem GUID i identyfikator numeryczny pary. Identyfikator GUID identyfikuje "zestaw poleceń" i służy do grupowania poleceń logicznie powiązanych. Pakiet VSPackage powinna definiować własne polecenia ustawione, aby uniknąć kolizji z identyfikatory poleceń, które są zdefiniowane przez inne pakiety VSPackage.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Pakiet|Identyfikator GUID, który identyfikuje pakiet VSPackage, który zawiera polecenia.<br /><br /> Na przykład pakiet = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakiet VSPackage.|  
|[Groups, element](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy poleceń w pakiet VSPackage.|  
|[Buttons, element](../extensibility/buttons-element.md)|Grupuje elementy przycisku.|  
|[Bitmaps, element](../extensibility/bitmaps-element.md)|Grupuje elementy mapy bitowej.|  
|[Combos, element](../extensibility/combos-element.md)|Grupuje elementy kombi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkich elementów, które reprezentują poleceń, które zawiera pakiet VSPackage do środowiska IDE. Możliwych elementów są elementy menu, menu, paski narzędzi i pola kombi.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie [polecenia Element](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage">  
    <Menus>  
      <Menu Condition="'%(DEBUG)' != 'true'"   
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"   
        priority="0x0000" type="Menu">  
        <Annotation>  
          <Documentation>this is an annotation</Documentation>  
          <AppInfo>  
            <CustomData>  
              <CustomSubElement>Some data</CustomSubElement>  
            </CustomData>  
          </AppInfo>  
        </Annotation>  
        <CommandFlag>AlwaysCreate</CommandFlag>  
        <Strings>  
          <ButtonText>MainMenu</ButtonText>  
        </Strings>  
      </Menu>  
  </Menus>  
<Commands>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Jak VSPackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)