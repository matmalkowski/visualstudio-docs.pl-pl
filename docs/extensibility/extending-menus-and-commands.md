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
ms.workload: vssdk
ms.openlocfilehash: 815aac693686dc59d6934b00fb456c3a1afce72c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extending-menus-and-commands"></a>Rozszerzanie menu i poleceń
Polecenia są sposób dodawania działań i procesów dla Visual Studio. W większości przypadków polecenia są wyświetlane w menu i pasków narzędzi. Szablon projektu pakiet VSPackage przedstawia sposobu wdrażania wykraczającego poza podstawowe polecenia. Aby nieco dłużej, ale nadal podstawowych implementacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Aby uzyskać więcej informacji dotyczących polecenia, menu i pasków narzędzi Visual Studio, zobacz [polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Polecenia, menu i pasków narzędzi są zdefiniowane w pliku vsct, który jest częścią pakietu VSPackage projektów. Można znaleźć informacje o programie Visual Studio IDE i w pliku vsct [jak VSPackages Dodaj elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 W poniższych tematach opisano sposób dodawania różnych rodzajów polecenia, menu i pasków narzędzi.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie menu do paska menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Wyjaśniono, jak dodać menu na górnym pasku menu programu Visual Studio.  
  
 [Wiązanie skrótów klawiaturowych z elementami menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Wyjaśniono, jak dodać do elementu menu skrótów klawiaturowych (np. CTRL + 3).  
  
 [Dodawanie podmenu do menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Wyjaśniono, jak dodać podmenu do menu u góry.  
  
 [Dodawanie listy ostatnio używanych elementów do podmenu](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Wyjaśniono, jak dodać listę ostatnio używanych.  
  
 [Tworzenie grup przycisków do wielokrotnego użytku](../extensibility/creating-reusable-groups-of-buttons.md)  
 Opisuje sposób grupowania elementów polecenie, aby mogły one zostać uwzględnione w wielu menu.  
  
 [Dodawanie ikon do poleceń menu](../extensibility/adding-icons-to-menu-commands.md)  
 Opisuje sposób dodawania ikony do polecenia na pasku narzędzi i menu.  
  
 [Zmiana tekstu polecenia menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Opisuje `TextChanges` flagami, aby umożliwić można zmienić dynamicznie elementu menu.  
  
 [Zmiana wyglądu polecenia](../extensibility/changing-the-appearance-of-a-command.md)  
 Opisuje sposób dynamiczne Włączanie lub wyłączanie polecenia.  
  
 [Aktualizowanie interfejsu użytkownika](../extensibility/updating-the-user-interface.md)  
 Opisuje sposób wymusić aktualizację interfejsu użytkownika w celu odzwierciedlenia ostatnich zmian.  
  
 [Lokalizowanie poleceń menu](../extensibility/localizing-menu-commands.md)  
 Wyjaśniono, jak do zlokalizowania poleceń menu.  
  
## <a name="related-sections"></a>Sekcje pokrewne