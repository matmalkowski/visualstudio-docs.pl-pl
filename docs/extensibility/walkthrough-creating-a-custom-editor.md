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
ms.openlocfilehash: ecc70112dc89a1866a4688fd39d8a2aae129387b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-editor"></a>Wskazówki: Tworzenie edytora niestandardowego
Szablon projektu pakiet VSPackage można utworzyć prosty niestandardowego edytora w języku C++.  Szablon projektu pakiet VSPackage już nie obsługuje projektów C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Szablon projektu pakietu Visual Studio  
 Szablon projektu pakietu Visual Studio można znaleźć w **nowy projekt** okna dialogowego w folderze rozszerzalności języka C++  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Aby utworzyć pakiet VSPackage przy użyciu szablonu pakietu Visual Studio  
  
1.  Tworzenie projektu przy użyciu szablonu pakietu Visual Studio.  
  
2.  Wybierz **edytora niestandardowego** opcję i kliknij przycisk **dalej**. **Opcji edytora** zostanie wyświetlona strona.  
  
3.  Wpisz nazwę w edytorze w **nazwa edytora** pole. Wpisz rozszerzenie pliku, który ma zostać skojarzony z edytora w **rozszerzenie pliku** pole. Edytor jest dostępna w przypadku plików dla tego rozszerzenia. Rozszerzenie pliku jest zarejestrowany dla programu Visual Studio, nie dla systemu Windows. Wpisz nazwę pliku domyślne dla nowych dokumentów utworzonych za pomocą edytora w **domyślnej nazwy pliku** pole.  
  
4.  Kliknij przycisk **Zakończ** można utworzyć w folderze określonym VSPackage.  
  
### <a name="to-test-your-custom-editor"></a>Aby przetestować edytora niestandardowego  
  
1.  Na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **pliku**.  
  
2.  W **zainstalowane szablony** okienku **nowy plik** okno dialogowe, wybierz szablon pliku, a następnie plik typ ma właśnie zarejestrowany.  
  
3.  Kliknij przycisk **Otwórz** do wyświetlania i edytowania dokumentu.  
  
     Edytor obsługuje operacje kopiowania i wklejania, Znajdź i Zamień i Otwórz i obciążenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)