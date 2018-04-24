---
title: 'Porady: tworzenie i usuwanie zależności projektu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/21/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b9a655f61c7e91a1626038781601401a539bbb1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Porady: tworzenie i usuwanie zależności projektu
Podczas kompilowania rozwiązania, które zawiera wiele projektów, może być konieczne, aby najpierw utworzyć niektórych projektów, aby wygenerować kod używany przez inne projekty. Gdy projekt korzysta z pliku wykonywalnego kod wygenerowany przez inny projekt, projekt, który generuje kod jest określany jako zależności projektu z projektu, który wykorzystuje kod. Takie relacji zależności można zdefiniować w **zależności projektu** okno dialogowe.  

### <a name="to-assign-dependencies-to-projects"></a>Aby przypisać zależności do projektów  

1.  W **Eksploratora rozwiązań**, wybierz projekt.  

2.  Na **projektu** menu, wybierz **zależności projektu**.  

     **Zależności projektu** zostanie otwarte okno dialogowe.  

    > [!NOTE]
    >  **Zależności projektu** opcja jest dostępna tylko w rozwiązania z projektem więcej niż jeden.  

3.  Na **zależności** , a następnie wybierz projekt z **projektu** menu rozwijanego.  

4.  W **zależy od** pola, zaznacz pole wyboru w innych projektów, które należy utworzyć przed tego projektu.  

 Rozwiązania musi składać się z więcej niż jeden projekt, aby można było utworzyć zależności projektu.  

### <a name="to-remove-dependencies-from-projects"></a>Aby usunąć zależności z projektów  

1.  W **Eksploratora rozwiązań**, wybierz projekt.  

2.  Na **projektu** menu, wybierz **zależności projektu**.  

     **Zależności projektu** zostanie otwarte okno dialogowe.  

    > [!NOTE]
    >  **Zależności projektu** opcja jest dostępna tylko w rozwiązania z projektem więcej niż jeden.  

3.  Na **zależności** , a następnie wybierz projekt z **projektu** menu rozwijanego.  

4.  W **zależy od** pola, usuń zaznaczenie pola wyboru obok inne projekty, które nie są już zależności tego projektu.  

## <a name="see-also"></a>Zobacz także  
 [Tworzenie i wyczyścić projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Kompilowanie i kompilacji](../ide/compiling-and-building-in-visual-studio.md)   
 [Zrozumienie konfiguracje kompilacji](../ide/understanding-build-configurations.md)   
 [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)

