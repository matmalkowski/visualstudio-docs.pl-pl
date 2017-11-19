---
title: "Porady: Tworzenie szablonów projektów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a473ac2be65acc9b08455fe687b52468f5ca9fa6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-project-templates"></a>Porady: tworzenie szablonów projektów
Ta procedura umożliwia utworzenie szablonu przy użyciu **Eksportuj szablon** kreatora, w którym pakietów szablonu w pliku zip. Można również tworzyć szablony w formacie pliku VSIX dla ulepszone wdrażanie, za pomocą rozszerzenia eksportu Kreatora szablonów lub z szablonów w [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)], lub szablonów można tworzyć ręcznie.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Aby utworzyć szablon niestandardowy projekt przy użyciu standardowych Kreatora eksportowania szablonu  
  
1.  Tworzenie projektu.  
  
    > [!NOTE]
    >  Gdy nazwy projektu, który będzie źródło szablonu, należy używać tylko znaków prawidłowego identyfikatora. Szablon wyeksportowany z projektu o nazwie nieprawidłowe znaki może spowodować błędy kompilacji w przyszłości projekty na podstawie szablonu. Aby uzyskać więcej informacji na prawidłowy identyfikator znaków, zobacz [zadeklarowane nazwy elementów](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
2.  Edytuj projekt, dopóki nie jest gotowy do wyeksportowania jako szablon.  
  
3.  Zgodnie z potrzebami Edytuj pliki kodu, wskaż, gdzie parametr zastąpienia powinno mieć miejsce. Aby uzyskać więcej informacji na zastępowanie parametru, zobacz [porady: parametry zastępczych w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Na **projektu** menu, kliknij przycisk **Eksportuj szablon**. **Eksportuj szablon** zostanie otwarty Kreator.  
  
5.  Kliknij przycisk **projektu szablonu**.  
  
6.  Jeśli masz więcej niż jeden projekt w bieżącym rozwiązaniu, wybierz projekty, do których mają zostać wyeksportowane do szablonu.  
  
7.  Kliknij przycisk **Dalej**.  
  
8.  Wybierz ikonę i obraz podglądu dla szablonu. Będą one widoczne w **nowy projekt** okno dialogowe.  
  
9. Wprowadź nazwę i opis szablonu.  
  
10. Kliknij przycisk **Zakończ**. Projektu jest wyeksportowany do pliku zip umieszczony w lokalizacji określonej w danych wyjściowych i, jeśli zaznaczone, należy zaimportować do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Jeśli masz [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] zainstalowana, można zawijać Zakończono szablonu w pliku .vsix dla wdrożenia przy użyciu **projektu VSIX** szablonu. Aby uzyskać więcej informacji, zobacz [wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Porady: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md)
