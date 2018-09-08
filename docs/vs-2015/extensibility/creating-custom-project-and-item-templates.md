---
title: Tworzenie szablonów elementów i projektów niestandardowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cd850cf73f9d7a9c443c374bd8a83e48c3470a31
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44124871"
---
# <a name="creating-custom-project-and-item-templates"></a>Tworzenie niestandardowych szablonów projektów i szablonów elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Tworzenie niestandardowych szablonów projektów i elementów](https://docs.microsoft.com/visualstudio/extensibility/creating-custom-project-and-item-templates).  
  
Visual Studio SDK zawiera szablony projektów, które Tworzenie szablonu niestandardowego projektu i szablonu niestandardowego elementu. Te szablony obejmują kilka typowych podstawieniach parametrów i kompilacji jako pliki zip. Nie są automatycznie wdrażane, a nie są one dostępne w doświadczalnym wystąpieniu. Należy skopiować pliku zip plik do lokalizacji  
  
 Szablony do tworzenia szablonu pozwalają obejmują szablony w rozszerzeniach większe. Pozwala to na implementowanie kontroli wersji na pliki źródłowe i utworzyć grupę z projektów szablonu w jednym pakiecie VSIX.  
  
 W przypadku scenariuszy tworzenia podstawowego szablonu należy używać **Eksportuj szablon** kreatora, której dane wyjściowe do skompresowanego pliku. Aby uzyskać więcej informacji na temat tworzenia podstawowego szablonu zobacz [tworzenie projektów i szablonów elementów](../ide/creating-project-and-item-templates.md).  
  
 Począwszy od programu Visual Studio "15" (wersja zapoznawcza), 4, skanowanie w poszukiwaniu szablonów niestandardowych projektów i elementów nie jest już zostaną wykonane. Zamiast tego rozszerzenia, należy podać plik manifestu szablonu, które opisują lokalizację instalacji tych szablonów. Za pomocą instalacji w wersji 2 można zaktualizować rozszerzenia VSIX. W przypadku wdrożenia przy użyciu Instalatora MSI rozszerzenia, musisz ręcznie wygenerować plik manifestu szablonu. Aby uzyskać więcej informacji, zobacz [uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio "15"](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schematu manifestu szablonu jest udokumentowany w [Visual Studio Manifest odwołanie do schematu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="creating-a-project-template"></a>Tworzenie szablonu projektu  
  
1.  Utwórz projekt szablonu projektu. Można znaleźć szablonu projektu w **nowy projekt** okna dialogowego, w języku Visual Basic lub Visual C# **rozszerzalności** folderu.  
  
     Szablon generuje plik klasy, ikony, plik .vstemplate, plik można edytować projekt o nazwie ProjectTemplate.vbproj lub ProjectTemplate.csproj i niektóre pliki, które zwykle są generowane przez innych typów projektów, takich resources.resx pliku AssemblyInfo. plik i pliku .settings. Każdy plik kodu zawiera typowe podstawieniach parametrów, gdzie jest to odpowiednie.  
  
2.  Dodawanie i usuwanie elementów z projektu, co jest wymagane dla projektu. Nie usuwaj pliku projektu można edytować, plik AssemblyInfo lub plik .vstemplate.  
  
3.  Zaktualizuj plik .vstemplate w celu uwzględnienia wszelkich dodanych i usuniętych. [Projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) elementu dla każdego pliku, które mają zostać uwzględnione w szablonie.  
  
4.  Modyfikowanie plików kodu i innej zawartości widocznych dla użytkownika, a następnie dodaj odpowiedni parametr podstawienia.  
  
5.  Zmodyfikuj wygenerowane zawartość zgodnie z potrzebami.  
  
6.  Skompiluj projekt.  
  
     Visual Studio tworzy plik .zip zawierający szablon. Nie są one wdrażane, a nie jest dostępna w eksperymentalnym wystąpieniu.  
  
## <a name="creating-an-item-template"></a>Tworzenie szablonu elementu  
  
1.  Tworzenie szablonu elementu projektu.  
  
     Szablon generuje plik klasy, ikony, plik .vstemplate i pliku AssemblyInfo. Plik klasy zawiera niektóre typowe podstawieniach parametrów.  
  
2.  Dodawanie i usuwanie elementów z projektu, co jest wymagane dla projektu.  
  
3.  Zaktualizuj plik .vstemplate w celu uwzględnienia wszelkich dodanych i usuniętych. [Projektu](../extensibility/project-element-visual-studio-templates.md) musi zawierać element [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) elementu dla każdego pliku, które mają zostać uwzględnione w szablonie.  
  
4.  Modyfikowanie plików kodu i innej zawartości widocznych dla użytkownika, a następnie dodaj odpowiedni parametr podstawienia.  
  
5.  Zmodyfikuj zawartość jest generowana zgodnie z potrzebami.  
  
6.  Skompiluj projekt.  
  
     Visual Studio tworzy skompresowany plik, który zawiera ten szablon. Nie są one wdrażane, a nie jest dostępna w eksperymentalnym wystąpieniu.  
  
## <a name="deployment"></a>wdrażania  
  
#### <a name="to-deploy-the-project-or-item-template"></a>Aby wdrożyć szablon projektu lub elementu  
  
1.  Utwórz projekt VSIX. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).  
  
2.  Ustaw projekt VSIX jako projekt startowy. W **Eksploratora rozwiązań**, wybierz węzeł projektu VSIX, kliknij prawym przyciskiem myszy i wybierz **Ustaw jako projekt startowy**.  
  
3.  Ustaw projekt szablonu projektu jako zasób usługi w projekcie VSIX. Otwórz plik .vsixmanifest. Przejdź do **zasoby** kartę, a następnie kliknij przycisk **New**.  
  
    1.  Ustaw **typu** pole **Microsoft.VisualStudio.ProjectTemplate** lub **Microsoft.VisualStudio.ItemTemplate**.  
  
    2.  Dla źródła, wybierz **projekt w bieżącym rozwiązaniu** opcji, a następnie wybierz projekt, który zawiera ten szablon.  
  
4.  Skompiluj rozwiązanie, a następnie naciśnij klawisz F5. Zostanie wyświetlone wystąpienie eksperymentalne.  
  
5.  Dla projektu szablonu projektu, powinien zostać wyświetlony na liście szablonu projektu **nowy projekt** okna dialogowego (**plik / nowy / Project**), a w Visual C# lub Visual Basic węzła. Dla szablonu elementu projektu, powinien zostać wyświetlony szablon elementu okno dialogowe Dodaj nowy element na liście (w **Eksploratora rozwiązań**, wybierz węzeł projektu i kliknij **Add / nowy element**).  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje o szablonach programu Visual Studio](../ide/visual-studio-template-reference.md)

