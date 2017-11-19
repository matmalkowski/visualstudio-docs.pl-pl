---
title: "Porady: Dodawanie zależności do pakietu VSIX | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3f3b54e19d8418f35a733b73ea0616b53bd42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Porady: Dodawanie zależności do pakietu VSIX
Można skonfigurować wdrożenie pakietu VSIX, która instaluje wszystkie zależności, które nie są już istnieje na komputerze docelowym. W tym celu należy uwzględnić zależności pliku VSIX do pliku source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Aby dodać zależność  
  
1.  Otwórz plik Source.Extension.vsixmanifest,a w **projekt** widoku. Przejdź do **zależności** i kliknij polecenie **nowy**.  
  
2.  Aby dodać zainstalowanego rozszerzenia: w **Dodawanie nowych zależności** okno dialogowe, wybierz opcję **zainstalowane rozszerzenie** , a następnie w **nazwa**, zaznacz rozszerzenie na liście.  
  
3.  Aby dodać inny VSIX, który nie jest zainstalowany:: w **Dodawanie nowych zależności** okno dialogowe, wybierz opcję **pliku w systemie plików** , a następnie użyj **Przeglądaj** przycisk, aby wybrać pliku VSIX.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu 1.0 rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Struktura pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)