---
title: KeyBinding, Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb8e0dca8293d5d5e853dde19e0c411cfd3e4e63
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495300"
---
# <a name="keybinding-element"></a>KeyBinding, element
KeyBinding, element określa skróty klawiaturowe dla poleceń.  
  
 Polecenia może mieć zarówno pojedynczych, jak i podwójną klawiszy skojarzonych z nimi. Na przykład jednego powiązanie klawiszy **Ctrl**+**S** dla **Zapisz** polecenia. Podwójna klawiszy wymaga dwóch kolejnych kombinacje klawiszy, aby wyzwolić poleceniu. Na przykład dwa powiązanie klawiszy **Ctrl * +** K **,** Ctrl**+** K **, aby ustawić zakładki.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagane.|  
|identyfikator|Wymagane.|  
|edytor|Wymagane. Identyfikator GUID edytora wskazuje Kontekst edycyjny, dla którego ten skrót klawiaturowy zostanie uaktywniona. Wartość zakresu globalnego powiązania jest "guidVSStd97".|  
|klucz1|Wymagane. Prawidłowe wartości to wszystkie typable znaków alfanumerycznych, a także dwucyfrowych wartości szesnastkowych, poprzedzony 0 x i [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|  
|mod1|Opcjonalna. Dowolną kombinację **Ctrl**, **Alt**, i **Shift** rozdzielone spacjami.|  
|klucz2|Opcjonalna. Prawidłowe wartości to wszystkie typable znaków alfanumerycznych, a także dwucyfrowych wartości szesnastkowych, poprzedzony 0 x i [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|  
|mod2|Opcjonalna. Dowolną kombinację **Ctrl**, **Alt**, i **Shift** rozdzielone spacjami.|  
|Emulator|Opcjonalna.|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny||  
|Adnotacja||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[KeyBindings, element](../extensibility/keybindings-element.md)|Grupuje elementy powiązanie klawiszy i inne grupy powiązań klawiszy.|  
  
## <a name="example"></a>Przykład  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [KeyBindings, element](../extensibility/keybindings-element.md)   
 [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
