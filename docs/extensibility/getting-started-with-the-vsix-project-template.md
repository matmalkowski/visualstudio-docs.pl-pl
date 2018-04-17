---
title: Wprowadzenie do szablonu projektu VSIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c96c0f66792f6a7a190fb5ea69ec5727ea4f2db1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-with-the-vsix-project-template"></a>Wprowadzenie do szablonu projektu VSIX
Można użyć szablonu projektu VSIX, można utworzyć rozszerzenia lub istniejące rozszerzenie dla wdrożenia pakietu. Szablon projektu VSIX wersji zarówno Visual Basic i Visual C# i jest instalowany jako część programu Visual Studio SDK.  
  
 Szablon projektu VSIX składa się tylko z pliku source.extension.vsixmanifest, który zawiera informacje o rozszerzeniu i zasobów, które ten składnik jest dostarczany.  
  
 Aby znaleźć szablonu projektu VSIX, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Wdrażanie niestandardowego szablonu projektu za pomocą szablonu projektu VSIX  
 Poniższe kroki pokazują, jak korzystać z projektu VSIX do pakietu szablon projektu, który można udostępnić z innymi deweloperami lub Przekaż do galerii programu Visual Studio.  
  
1.  Tworzenie szablonu projektu.  
  
    1.  Otwórz projekt, z którym ma zostać utworzony szablon. Ten projekt może być dowolnego typu projektu.  
  
    2.  Na **projektu** menu, kliknij przycisk **Eksportuj szablon**. Wykonaj kroki kreatora.  
  
         Plik zip jest tworzony w %USERPROFILE%\My Documents\Visual Studio  *\<wersji >*\My wyeksportowane szablony\\.  
  
2.  Utwórz pusty projekt VSIX.  
  
     Na **pliku** menu, kliknij przycisk **nowy** , a następnie kliknij przycisk **projektu**. Wybierz opcję **Visual Basic** lub **Visual C#**. W obszarze wybranego węzła, wybierz **rozszerzalności**, a następnie wybierz **projektu VSIX**.  
  
3.  Dodaj plik zip do projektu. Ustaw jego **Kopiuj do katalogu wyjściowego** właściwości `Copy Always`.  
  
4.  W **Eksploratora rozwiązań**, kliknij dwukrotnie `source.extension.vsixmanifest` plik, aby otworzyć go w **projektanta manifestu VSIX**, a następnie dokonaj następujących zmian:  
  
    -   Ustaw **nazwa produktu** do **mój szablon projektu**.  
  
    -   Ustaw **identyfikator produktu** do **MyProjectTemplate - 1**.  
  
    -   Ustaw **autora** do **Fabrikam**.  
  
    -   Ustaw **opis** do **mój szablon projektu**.  
  
    -   W **zasoby** Dodaj **Microsoft.VisualStudio.ProjectTemplate** wpisz i ustaw ścieżki do nazwy pliku zip.  
  
5.  Zapisz i zamknij plik Source.Extension.vsixmanifest,a.  
  
6.  Skompiluj projekt.  
  
7.  Kliknij dwukrotnie plik .vsix w katalogu wyjściowego.  
  
8.  A **Instalatora VSIX** pojawi się komunikat. Postępuj zgodnie z instrukcjami, aby zainstalować rozszerzenie.  
  
9. Zamknij program Visual Studio, a następnie otwórz go ponownie.  
  
10. Wybierz **rozszerzenia i aktualizacje** (na **narzędzia** menu) i wybierz **szablony** kategorii. Jeden z dostępnych rozszerzeń powinien być **mój szablon projektu**.  
  
11. Nowy szablon projektu jest wyświetlany w **nowy projekt** okna dialogowego, w tym samym miejscu jako oryginalnego szablonu projektu. Na przykład utworzyć szablon o nazwie **konsoli VB** z aplikacji konsoli języka Visual Basic, **konsoli VB** zostanie wyświetlony w okienku tym samym jako Visual Basic **aplikacji konsoli**szablonu.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Aby określić lokalizację szablonu w oknie dialogowym nowego projektu  
  
1.  Szablon foldery znajdują się w *ścieżki instalacji usługi Visual Studio*\Common7\IDE\ProjectTemplates i *ścieżki instalacji usługi Visual Studio*\Common7\IDE\ItemTemplates katalogów. Nazwy sekcji najwyższego poziomu w oknie dialogowym Nowy projekt nie odpowiada nazwy folderów szablonu. W przypadku, gdy będą się różnić, należy użyć nazwy w folderze szablonów.  
  
     Zmień .vsix rozszerzenie na zip, a następnie otwórz plik.  
  
2.  Utwórz nowy folder o takiej samej nazwie jak sekcja okna dialogowego Nowy projekt szablonu powinny być wyświetlane w.  
  
3.  Jeśli szablon jest pojawią się w podsekcji, utwórz podfolder o tej samej nazwie.  
  
4.  Przenieś plik zip szablonu do nowego folderu.  
  
5.  Zmień rozszerzenie zip .vsix.  
  
6.  Otwórz plik manifestu VSIX.  
  
7.  W manifeście VSIX zaktualizować **zasobów** ścieżka szablonu, tak aby punkty do katalogu głównego drzewa katalogów, który zawiera plik szablonu. Na przykład jeśli szablon \CSharp\Windows, odwołania powinny wskazywać \CSharp.