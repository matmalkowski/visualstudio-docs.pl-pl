---
title: "Zewnętrzny Element | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ff198f5c4b574bf3a27ae1ee8fb6ffdd482c7f71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extern-element"></a>Extern — Element
Zewnętrzny element odwołuje się do żadnych plików zewnętrznych nagłówków (.h) do scalenia pliku vsct w czasie kompilacji. Pliki do scalenia muszą znajdować się na ścieżce dołączanych podane do kompilatora VSCT lub odwołuje się [obejmują elementu](../extensibility/include-element.md). Pliki mogą być inne vsct lub pliki nagłówkowe C++.  
  
 Definicje w plikach nagłówka musi mieć postać "# [Symbol] [wartość] define" wartość może być inny symbol, jeśli został wcześniej zdefiniowany. Definicje mogą być używane w instrukcji warunkowych elementów polecenia. Każdy symbol nie faktycznie używana zostaną odrzucone.  
  
 CommandTable Element  
Extern — Element  
  
## <a name="syntax"></a>Składnia  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|href|Wymagany. Ścieżka do pliku nagłówka:<br /><br /> href="stdidcmd.h"|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|język|Opcjonalny. Domyślny język wszystkich [ \<ciągów >](../extensibility/strings-element.md) elementów w tabeli poleceń:<br /><br /> język = "en-us"|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak.|Brak.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Wszystkie elementy, które reprezentują polecenia definiuje — to znaczy elementy menu, menu Paski narzędzi i pola kombi — udostępniająca pakiet VSPackage IDE.|  
  
## <a name="example"></a>Przykład  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Jak VSPackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)