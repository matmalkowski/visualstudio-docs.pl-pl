---
title: Tworzenie niestandardowych Project and Item Templates | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3677dd4ad6177f4085c907d1fceaaf37978bf769
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="creating-custom-project-and-item-templates"></a>Tworzenie niestandardowych projekt oraz szablony elementów

Visual Studio SDK zawiera szablony projektów, które utworzyć szablon niestandardowy projekt i szablonu niestandardowego elementu. Te szablony obejmują niektóre typowe podstawienia parametru i skompiluj jako pliki zip. Nie są automatycznie wdrażane, a nie są dostępne w eksperymentalnym wystąpieniu. Plik zip wygenerowanego należy skopiować do katalogu szablonu użytkownika.
  
Szablony tworzenia szablonu pozwala na uwzględnianie szablonów w większych rozszerzeń. Dzięki temu można zaimplementować kontroli wersji na pliki źródłowe i wbudowane grupy projektów szablonu w jeden pakiet VSIX.  
  
Można również skonfigurować szablon można zainstalować pakietów NuGet. Aby uzyskać więcej informacji, zobacz [pakietów NuGet w szablony Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Scenariusze tworzenia szablonów podstawowe, należy używać **Eksportuj szablon** kreatora, który wyprowadza do skompresowanego pliku. Aby uzyskać więcej informacji o tworzeniu szablonu podstawowego, zobacz [szablony tworzenie projektów i elementów](../ide/creating-project-and-item-templates.md).  

> [!NOTE]
> Począwszy od programu Visual Studio 2017 skanowanie w poszukiwaniu szablony niestandardowe projektów i elementów zostaną już wykonane. Zamiast tego rozszerzenia, należy podać manifestu plików szablonów, które opisują lokalizację instalacji tych szablonów. Można użyć programu Visual Studio 2017 można zaktualizować rozszerzenia VSIX. W przypadku wdrożenia przy użyciu Instalatora MSI rozszerzenie, należy ręcznie wygenerować pliki manifestu szablonu. Aby uzyskać więcej informacji, zobacz [uaktualniania niestandardowe szablony projektów i elementów dla programu Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schemat manifestu szablonu jest udokumentowany w [programu Visual Studio manifestu odwołanie do schematu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="creating-a-project-template"></a>Tworzenie szablonu projektu  
  
1.  Tworzenie projektu szablonu projektu. Można znaleźć szablonu projektu w **nowy projekt** okna dialogowego, w języku Visual Basic lub Visual C# **rozszerzalności** folderu.  
  
     Szablon generuje plik klasy, ikony pliku .vstemplate, plik można edytować projektu o nazwie ProjectTemplate.vbproj lub ProjectTemplate.csproj i niektóre pliki, które są zwykle generowane przez innych typów projektów, takie resources.resx pliku AssemblyInfo. plik, a w pliku .settings. Każdy plik kodu zawiera typowe podstawienia parametru odpowiednim.  
  
2.  Dodawanie i usuwanie elementów z projektu, co jest wymagane dla projektu. Nie usuwaj pliku projektu można edytować, plik AssemblyInfo lub pliku .vstemplate.  
  
3.  Zaktualizuj plik .vstemplate, aby uwzględnić wszystkie dodawania i usuwania. [Projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) elementu dla każdego pliku, które mają zostać uwzględnione w szablonie.  
  
4.  Modyfikowanie plików kodu i innej zawartości dla użytkownika, a następnie dodaj odpowiedni parametr podstawienia.  
  
5.  Zmodyfikuj wygenerowana zawartość zgodnie z potrzebami.  
  
6.  Skompiluj projekt.  
  
     Visual Studio tworzy plik zip, który zawiera szablon. Nie została wdrożona, i nie jest dostępna w eksperymentalnym wystąpieniu.  
  
## <a name="creating-an-item-template"></a>Tworzenie szablonu elementu  
  
1.  Tworzenie projektu szablonu elementu.  
  
     Szablon generuje plik klasy, ikony pliku .vstemplate i pliku AssemblyInfo. Plik klasy zawiera niektóre typowe podstawienia parametru.  
  
2.  Dodawanie i usuwanie elementów z projektu, co jest wymagane dla projektu.  
  
3.  Zaktualizuj plik .vstemplate, aby uwzględnić wszystkie dodawania i usuwania. [Projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) elementu dla każdego pliku, które mają zostać uwzględnione w szablonie.  
  
4.  Modyfikowanie plików kodu i innej zawartości dla użytkownika, a następnie dodaj odpowiedni parametr podstawienia.  
  
5.  Zmodyfikuj wygenerowana zawartość zgodnie z potrzebami.  
  
6.  Skompiluj projekt.  
  
     Visual Studio tworzy skompresowany plik, który zawiera szablon. Nie została wdrożona, i nie jest dostępna w eksperymentalnym wystąpieniu.  
  
## <a name="deployment"></a>wdrażania  
  
#### <a name="to-deploy-the-project-or-item-template"></a>Aby wdrożyć szablon projektu lub elementu  
  
1.  Tworzenie projektu VSIX. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).  
  
2.  Ustaw projekt VSIX jako projekt startowy. W **Eksploratora rozwiązań**, wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy i wybierz **Ustaw jako projekt startowy**.  
  
3.  Ustaw projekt szablonu projektu jako zasób projektu VSIX. Otwórz plik .vsixmanifest. Przejdź do **zasoby** i kliknij polecenie **nowy**.  
  
    1.  Ustaw **typu** do **Microsoft.VisualStudio.ProjectTemplate** lub **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Dla źródła, wybierz **projekt w bieżącym rozwiązaniu** opcji, a następnie wybierz projekt, który zawiera szablon.  
  
4.  Skompiluj rozwiązanie, a następnie naciśnij klawisz F5. Pojawi się eksperymentalne wystąpienie.  
  
5.  Dla projektu szablonu projektu, powinien zostać wyświetlony na liście szablonu projektu **nowy projekt** okna dialogowego (**Plik > Nowy > Projekt**), Visual C# lub Visual Basic węzła. Dla elementu projektu szablonu, powinien zostać wyświetlony szablonu elementu na liście w oknie dialogowym Dodawanie nowego elementu (w **Eksploratora rozwiązań**, wybierz węzeł projektu i kliknij przycisk **Add / nowy element**).  
  
## <a name="see-also"></a>Zobacz też

[Odwołanie do szablonu Visual Studio](../ide/visual-studio-template-reference.md)  
[Pakiety NuGet w szablony programu Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)