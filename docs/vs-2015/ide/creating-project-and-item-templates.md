---
title: Tworzenie szablonów projektów i elementów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e288329637c6a6f421a5b32f19084897a31e5f22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680481"
---
# <a name="creating-project-and-item-templates"></a>Tworzenie szablonów projektów i elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [tworzenie projektów i szablonów elementów](https://docs.microsoft.com/visualstudio/ide/creating-project-and-item-templates).  
  
Szablony projektu i elementu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zapewniają fragmenty do ponownego użycia udostępniające użytkownikom podstawowy kod i struktury, które można wykorzystać do własnych celów.  
  
## <a name="visual-studio-templates"></a>Szablony Visual Studio  
 Wiele wstępnie zdefiniowanych szablonów projektu i elementu jest instalowane podczas instalacji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikacja interfejsu Windows Forms i biblioteki klas szablonów, które są dostępne w **nowy projekt** okno dialogowe to przykłady szablonów projektu. Zainstalowane szablony elementu są dostępne w **Dodaj nowy element** okna dialogowego i zawierają elementy, takie jak pliki kodu, plików XML, strony HTML i arkusze stylów.  
  
 Te szablony zapewniają punkt wyjścia dla użytkowników rozpoczynających tworzenie projektów lub rozszerzanie bieżących projektów. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Złożoność szablonów elementów może mieścić od zaledwie jednego pustego pliku, który ma poprawne rozszerzenie nazwy pliku po element wieloplikowy, który zawiera na przykład, pliki kodu źródłowego z kodem skróconym, informacje o projektancie plików i zasoby osadzone.  
  
 Oprócz szablonów zainstalowanych w **nowy projekt** i **Dodaj nowy element** okien dialogowych, możesz tworzyć własne szablony lub pobrać i używać szablonów utworzonych przez społeczność. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md) i [porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md).  
  
## <a name="contents-of-a-template"></a>Zawartość szablonu  
 Wszystkie szablony projektów i elementów, instalowane wraz z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub utworzone przez użytkownika, działają na podstawie tych samych zasad i spisu treści. Wszystkie szablony zawierają następujące elementy:  
  
-   Pliki, które można utworzyć, jeśli jest używany szablon. Dotyczy to plików kodu źródłowego, zasobów osadzonych, plików projektu i tak dalej.  
  
-   Jeden plik .vstemplate. Ten plik zawiera metadane, które dostarczają [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] informacji wymaganych, aby wyświetlić szablon w **nowy projekt** i **Dodaj nowy element** okna dialogowe i umożliwia utworzenie projektu lub elementu z szablon. Aby uzyskać więcej informacji na temat plików .vstemplate, zobacz [parametry szablonu](../ide/template-parameters.md).  
  
 Jeśli te pliki są kompresowane w pliku zip i umieść w odpowiednim folderze, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wyświetla je automatycznie. Szablony projektów są wyświetlane w **Moje szablony** części **nowy projekt** okien dialogowych i szablonów elementów są wyświetlane w **Dodaj nowy element** okien dialogowych. Aby uzyskać więcej informacji na temat folderów szablonów, zobacz [jak: Znajdź i organizowania szablony](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="starter-kits"></a>Zestawy początkowe  
 Zestawy startowe są rozszerzone przez szablony, które mogą być współużytkowane z innymi członkami społeczności. Zestaw startowy zawiera przykłady kodu, które kompilują, dokumentację i inne zasoby, aby pomóc użytkownikom poznać nowe narzędzia i techniki programowania, podczas tworzenia użytecznych, rzeczywistych aplikacji. Podstawowe zawartości i procedury zestawu startowego są identyczne z tymi szablonami. Aby uzyskać więcej informacji, zobacz [porady: tworzenie startowe](../ide/how-to-create-starter-kits.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)   
 [Porady: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)   
 [Instrukcje: Tworzenie pakietów startowych](../ide/how-to-create-starter-kits.md)



