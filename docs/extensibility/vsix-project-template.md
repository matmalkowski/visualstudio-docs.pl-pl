---
title: Szablon projektu VSIX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: de8de116a9853391249a7a37a35bd54d0a6946d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-project-template"></a>Szablon projektu VSIX
Można użyć szablonu projektu VSIX do zakodowania w projekcie VSIX jedno lub więcej rozszerzeń programu Visual Studio, a następnie opublikuj pakietu na [galerii programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) witryny sieci Web.  
  
 Wdrożenie VSIX obsługuje VSPackages, zestawy, składniki MEF, szablony projektów, szablony elementów, formanty z przybornika i typy rozszerzenia niestandardowego.  
  
> [!NOTE]
>  Aby użyć pliku VSIX projektów, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji na temat programu Visual Studio SDK, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Gdzie można znaleźć szablonu projektu VSIX  
 Szablon projektu VSIX jest dostępna w **nowy projekt** okno dialogowe. Rozwiń pozycję **Visual Basic** węzła lub **Visual C#** węzeł, a następnie wybierz pozycję **rozszerzalności**.  
  
> [!TIP]
>  Upewnij się, że program .NET Framework 4.5 lub wyższa określono na liście rozwijanej na górze **nowy projekt** okno dialogowe.  
  
## <a name="uses-of-the-vsix-project-template"></a>Używa szablonu projektu VSIX  
 Szablon projektu VSIX ma dwa podstawowe zastosowania:  
  
-   Aby wdrożyć szablony projektów, szablonów elementów i inne rozszerzenia, które nie jest już obsługiwane VSIX.  
  
-   Opakowywać dane wyjściowe wiele rozszerzeń do pakietu jedno wdrożenie.  
  
 Nie trzeba wdrażać VSPackages lub inne rodzaje rozszerzeń, które mają już VSIX obsługuje przy użyciu szablonu projektu VSIX.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Pakowanie rozszerzenia w projekcie pustego pliku VSIX  
 Można spakować istniejące rozszerzenie lub rozszerzenia, które nie ma jeszcze VSIX obsługuje, opakowując go w projekcie VSIX jest pusta. Rozszerzenie w celu jej opakowania musi być typu, który jest obsługiwany przez [schematu VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Do pakietu rozszerzenia przy użyciu projektu VSIX  
  
1.  Tworzenie projektów, które składają się na Twoje rozszerzenie.  
  
2.  Tworzenie projektu VSIX przy użyciu **projektu VSIX** szablonu.  
  
     Otwiera Source.Extension.vsixmanifest w **projektanta manifestu**.  
  
3.  Na **zasoby** , wybierz pozycję **nowy** przycisku.  
  
     **Dodaj nowy element zawartości** zostanie wyświetlone okno dialogowe.  
  
4.  W **typu** listy, wybierz typ rozszerzenie do dodania.  
  
5.  Aby dodać element rozszerzenia lub zawartości, który znajduje się w bieżącym rozwiązaniu (na przykład szablon elementu lub skompilowanego zestawu), wykonaj następujące czynności:  
  
    1.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
    2.  W **projektu** listy, wybierz nazwę rozszerzenia.  
  
    3.  W **Osadź w tym folderze** wprowadź nazwę folderu, w którym Osadzanie zasobów, a następnie wybierz pozycję **OK** przycisku.  
  
6.  Aby dodać rozszerzenie lub elementu zawartości, który nie znajduje się w bieżącym rozwiązaniu, wykonaj następujące czynności:  
  
    1.  W **źródła** pola listy, wybierz **pliku w systemie plików**.  
  
    2.  W **ścieżki** pola, wprowadź pełną ścieżkę do pliku rozszerzenie skompilowanych lub skompresowany lub użyj **Przeglądaj** przycisk, aby przejść do lokalizacji pliku.  
  
    3.  W **Osadź w tym folderze** wprowadź nazwę folderu, w którym Osadzanie zasobów, a następnie wybierz pozycję **OK** przycisku.  
  
7.  Jeśli chcesz, aby pakiet obejmują dodatkowe rozszerzenia, należy je dodać w taki sam sposób.  
  
8.  Skompiluj rozwiązanie.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Tworzy plik .vsix, który zawiera plik manifestu VSIX, pliku XML [Content_Types] i wszystkie zasoby rozszerzenia, które zostały dodane do projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu 2.0 rozszerzenia VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Znajdowanie rozszerzeń programu Visual Studio i korzystanie z nich](../ide/finding-and-using-visual-studio-extensions.md)