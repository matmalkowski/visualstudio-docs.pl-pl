---
title: KeyBinding Element | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f620d895defbeeb3317f4a977db454a14ce3adc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="keybinding-element"></a>KeyBinding Element
KeyBinding element określa skróty klawiaturowe dla poleceń.  
  
 Polecenia może zawierać pojedyncze i podwójne powiązań klucza skojarzonych z nimi. Przykładem jednego powiązania klucza jest CTRL + S dla **zapisać** polecenia. Podwójna powiązań klucza wymaga dwóch kolejnych kombinacje klawiszy do wyzwolenia polecenia. Przykład dwa powiązania klucza to CTRL + K, CTRL + K, aby ustawić zakładki.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany.|  
|identyfikator|Wymagany.|  
|edytor|Wymagany. Edytor GUID wskazuje Kontekst edycyjny, dla którego ten skrót klawiaturowy będzie aktywny. Wartość zakresu globalnego powiązania jest "guidVSStd97".|  
|klucz1|Wymagany. Prawidłowe wartości to wszystkie typable alfanumeryczne, a także Dwucyfrowe wartości szesnastkowe poprzedzony 0 x i [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|mod1|Opcjonalny. Dowolną kombinację CTRL, ALT i SHIFT, rozdzielone spacjami.|  
|klucz2|Opcjonalny. Prawidłowe wartości to wszystkie typable alfanumeryczne, a także Dwucyfrowe wartości szesnastkowe poprzedzony 0 x i [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|mod2|Opcjonalny. Dowolną kombinację CTRL, ALT i SHIFT, rozdzielone spacjami.|  
|emulator|Opcjonalny.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny||  
|Adnotacja||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element powiązania klawiszy](../extensibility/keybindings-element.md)|Elementy KeyBinding grup i innych grup powiązań kluczy.|  
  
## <a name="example"></a>Przykład  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Element powiązania klawiszy](../extensibility/keybindings-element.md)   
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
