---
title: 'Porady: równoczesne kompilowanie wielu konfiguracji'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3772e194f801735edf4c857b605b3abb6c22144b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Porady: równoczesne kompilowanie wielu konfiguracji

Większość typów projektów z wieloma, lub nawet wszystkie ich konfiguracji kompilacji, w tym samym czasie można tworzyć przy użyciu **tworzenia partii** okno dialogowe. Jednak w tym samym momencie nie można utworzyć następujących typów projektów w wielu konfiguracjach kompilacji:

1.  [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacje dla systemu Windows przy użyciu języka JavaScript.

2.  Wszystkie projekty Visual Basic.

 Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [konfiguracje kompilacji omówienie](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Aby zbudować projekt w wielu konfiguracjach kompilacji

1.  Na pasku menu wybierz **kompilacji** > **tworzenia partii**.

2.  W **kompilacji** kolumny, zaznacz pola wyboru dla konfiguracji, w których chcesz skompilować projekt.

    > [!TIP]
    > Aby zmodyfikować lub utworzyć konfigurację kompilacji dla rozwiązania, wybierz **kompilacji** > **programu Configuration Manager** na pasku menu, aby otworzyć **programu Configuration Manager** okno dialogowe. Po zakończeniu edycji konfiguracji kompilacji dla rozwiązania, wybierz **odbudować** przycisk **tworzenia partii** okno dialogowe, aby zaktualizować wszystkie konfiguracje dla projektów w rozwiązaniu kompilacji.

3.  Wybierz **kompilacji** lub **odbudować** przycisków, aby skompilować projekt z określonymi konfiguracjami.

## <a name="see-also"></a>Zobacz także

- [Porady: tworzenie i edycja konfiguracji](../ide/how-to-create-and-edit-configurations.md)
- [Zrozumienie konfiguracje kompilacji](../ide/understanding-build-configurations.md)
- [Tworzenie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)