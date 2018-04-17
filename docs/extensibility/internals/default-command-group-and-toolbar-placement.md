---
title: Domyślne polecenia, grupy i umieszczania narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0753a29e323f18ad40bcc62a70cf8e9b1123b728
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="default-command-group-and-toolbar-placement"></a>Polecenie domyślne grupy i położenie paska narzędzi
Jednolitość produktu i stabilności interfejsu użytkownika wyświetla domyślnie określonym grupom polecenia i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawiera definicje dla poleceń i polecenia grup. VSPackages można również użyć standardowych poleceń i polecenia grupy.  
  
 Domyślne grupy polecenia dzielą się na trzy kategorie: IDE poleceń, polecenia produktu i poleceń edytora.  
  
## <a name="default-ide-commands"></a>Domyślne polecenia IDE  
 Domyślne narzędzi IDE zawiera polecenia współużytkowane przez wszystkie produkty zawarte w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Obejmują one poleceń dotyczących ogólnego projektu działań, takich jak **zapisać** polecenia i **Dodaj element** polecenia. VSPackages nie może dodać do lub odjęcia od ten pasek narzędzi z jednym wyjątkiem: Jeśli produktu lub pakiet VSPackage dodaje nowe okno narzędzi, a następnie okno należy dodać do listy dostępnych narzędzi systemu Windows na **widoku** menu. Własnych narzędzi można dodać nowych produktów lub VSPackages.  
  
## <a name="default-product-commands"></a>Domyślne polecenia produktu  
 Każdy produkt może zapewnić IDE z własnych narzędzi domyślny, który zawiera ważne i często używane polecenia. Najlepiej, jednak użyć istniejącego menu i pasków narzędzi, jeśli to możliwe i uzupełnienie je z innych pasków narzędzi poszczególnych zadań zgodnie z potrzebami.  
  
 Pole Priorytet dla paska narzędzi określa jej położenie wiersza. Zero priorytet umieszcza pasku narzędzi na trzeci wiersz (wiersz 3), poniżej paska menu (wiersz: 1) i **standardowe** paska narzędzi (wiersz 2). W związku z tym pasków narzędzi są wyświetlane w wierszu (priorytet + 3). Kolejne paski narzędzi są umieszczane w tym samym wierszu, jeśli jest miejsca; w przeciwnym razie automatycznie są przenoszone do następnego wiersza.  
  
## <a name="default-editor-commands"></a>Domyślny edytor poleceń  
 Pakiet VSPackage, który zawiera niestandardowy Edytor powinien zapewnić narzędzi domyślny, który zawiera najważniejsze i często używane polecenia w tym edytorze. Paska narzędzi edytora powinny być wyświetlane, gdy edytora jest aktywne i powinny być ukrywane, gdy edytor nie jest aktywny. Steruje się w tym widoczność `VisibilityConstraints Element` pliku vsct.  
  
 Paski narzędzi edytora powinna zostać umieszczona poniżej IDE i produktu pasków narzędzi.  
  
## <a name="see-also"></a>Zobacz też  
 [Definicja IDE polecenia, menu i grupy](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)