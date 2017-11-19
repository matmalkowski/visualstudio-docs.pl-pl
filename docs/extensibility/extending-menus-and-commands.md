---
title: "Rozszerzanie menu i poleceń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: "49"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c53f836b6384968bf812ae9ae559a281fda6f13
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="extending-menus-and-commands"></a>Rozszerzanie menu i poleceń
Polecenia są sposób dodawania działań i procesów dla Visual Studio. W większości przypadków polecenia są wyświetlane w menu i pasków narzędzi. Szablon projektu pakiet VSPackage przedstawia sposobu wdrażania wykraczającego poza podstawowe polecenia. Aby nieco dłużej, ale nadal podstawowych implementacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Aby uzyskać więcej informacji dotyczących polecenia, menu i pasków narzędzi Visual Studio, zobacz [polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Polecenia, menu i pasków narzędzi są zdefiniowane w pliku vsct, który jest częścią pakietu VSPackage projektów. Można znaleźć informacje o programie Visual Studio IDE i w pliku vsct [jak VSPackages Dodaj elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 W poniższych tematach opisano sposób dodawania różnych rodzajów polecenia, menu i pasków narzędzi.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie Menu na pasku Menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Wyjaśniono, jak dodać menu na górnym pasku menu programu Visual Studio.  
  
 [Skróty klawiaturowe powiązania elementów Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Wyjaśniono, jak dodać do elementu menu skrótów klawiaturowych (np. CTRL + 3).  
  
 [Dodawanie do Menu podmenu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Wyjaśniono, jak dodać podmenu do menu u góry.  
  
 [Dodawanie większość ostatnio używane do podmenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Wyjaśniono, jak dodać listę ostatnio używanych.  
  
 [Tworzenie grup wielokrotnych przycisków](../extensibility/creating-reusable-groups-of-buttons.md)  
 Opisuje sposób grupowania elementów polecenie, aby mogły one zostać uwzględnione w wielu menu.  
  
 [Dodawanie ikon do poleceń Menu](../extensibility/adding-icons-to-menu-commands.md)  
 Opisuje sposób dodawania ikony do polecenia na pasku narzędzi i menu.  
  
 [Zmiana tekstu polecenia Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Opisuje `TextChanges` flagami, aby umożliwić można zmienić dynamicznie elementu menu.  
  
 [Zmiana wyglądu polecenia](../extensibility/changing-the-appearance-of-a-command.md)  
 Opisuje sposób dynamiczne Włączanie lub wyłączanie polecenia.  
  
 [Aktualizowanie interfejsu użytkownika](../extensibility/updating-the-user-interface.md)  
 Opisuje sposób wymusić aktualizację interfejsu użytkownika w celu odzwierciedlenia ostatnich zmian.  
  
 [Lokalizowanie poleceń Menu](../extensibility/localizing-menu-commands.md)  
 Wyjaśniono, jak do zlokalizowania poleceń menu.  
  
## <a name="related-sections"></a>Sekcje pokrewne