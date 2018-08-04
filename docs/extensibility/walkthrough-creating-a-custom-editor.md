---
title: 'Wskazówki: Tworzenie edytora niestandardowego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9110e1c2ac6c39898f7dbbd6f9f4412ebcba278
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497440"
---
# <a name="walkthrough-create-a-custom-editor"></a>Przewodnik: Tworzenie edytora niestandardowego
Szablon projektu pakietu VSPackage można utworzyć proste edytora niestandardowego w języku C++. Szablon projektu pakietu VSPackage już nie obsługuje projektów C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Szablon projektu pakietu Visual Studio  
 Można znaleźć szablonu projektu pakietu Visual Studio w **nowy projekt** , okno dialogowe **rozszerzalności C++** folderu.  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Do utworzenia pakietu VSPackage przy użyciu szablonu pakietu Visual Studio  
  
1.  Utwórz projekt za pomocą szablonu pakietu Visual Studio.  
  
2.  Wybierz **edytora niestandardowego** opcji, a następnie kliknij przycisk **dalej**. **Opcji edytora** zostanie wyświetlona strona.  
  
3.  Wpisz nazwę w edytorze **nazwa edytora** pole. Wpisz rozszerzenie pliku, który ma zostać skojarzony z edytora w **rozszerzenie pliku** pole. Edytor jest dostępna dla plików za pomocą tego rozszerzenia. Rozszerzenie pliku jest zarejestrowane dla programu Visual Studio, nie dla Windows. Wpisz nazwę pliku domyślne dla nowych dokumentów utworzonych za pomocą edytora w **domyślnej nazwy pliku** pole.  
  
4.  Kliknij przycisk **Zakończ** do utworzenia Twojego pakietu VSPackage w podanym folderze.  
  
### <a name="to-test-your-custom-editor"></a>Aby przetestować niestandardowego edytora  
  
1.  Na **pliku** menu wskaż **New** a następnie kliknij przycisk **pliku**.  
  
2.  W **zainstalowane szablony** okienku **nowy plik** okno dialogowe, wybierz szablon pliku, a następnie plik typ zarejestrowany.  
  
3.  Kliknij przycisk **Otwórz** do wyświetlania i edytowania dokumentu.  
  
     Edytor obsługuje operacje kopiowania i wklejania, Znajdź i Zamień i open i obciążenia.  
  
## <a name="see-also"></a>Zobacz także  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)