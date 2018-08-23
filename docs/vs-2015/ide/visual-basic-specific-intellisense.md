---
title: IntelliSense specyficzne dla języka Visual Basic | Dokumentacja firmy Microsoft
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
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9bae55b10695ba73fec86d7ab63943e3440e3f05
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683526"
---
# <a name="visual-basic-specific-intellisense"></a>IntelliSense specyficzne dla Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IntelliSense specyficzne dla języka Visual Basic](https://docs.microsoft.com/visualstudio/ide/visual-basic-specific-intellisense).  
  
Edytor kodu źródłowego języka Visual Basic oferuje następujące funkcje IntelliSense:  
  
-   Porady dotyczące składni  
  
     Porady dotyczące składni Wyświetlanie składni instrukcji w miarę wpisywania. To jest przydatne w przypadku instrukcji takich jak [Declare](http://msdn.microsoft.com/library/d3f21fb0-b804-4c99-97ed-583b23894cf1).  
  
## <a name="automatic-completion"></a>Automatyczne uzupełnianie  
  
-   Uzupełnianie na różnych słów kluczowych  
  
     Na przykład, jeśli wpiszesz `goto` i spację, funkcję IntelliSense wyświetli listę etykiet zdefiniowanych w menu rozwijanym. Obejmują innych obsługiwanych słów kluczowych `Exit`, `Implements`, `Option`, i `Declare`.  
  
-   Uzupełnianie na `Enum` i `Boolean`  
  
     Po instrukcji będzie odnosił się do elementu członkowskiego wyliczenia, IntelliSense wyświetli się lista elementów członkowskich `Enum`. Kiedy oświadczenie będzie odnosił się do `Boolean`, funkcja IntelliSense wyświetli menu rozwijanego PRAWDA / FAŁSZ.  
  
 Uzupełnianie można wyłączyć domyślnie, anulując **automatyczna lista członków** z **ogólne** — strona właściwości w **języka Visual Basic** folderu.  
  
 Można ręcznie wywołać uzupełniania, wywołując listę elementów członkowskich, Dokończ wyraz lub ALT + Strzałka w prawo. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md).  
  
## <a name="intellisense-in-zone"></a>Funkcja IntelliSense w strefie  
 Funkcja IntelliSense w strefie pomaga deweloperom języka Visual Basic, którzy muszą wdrażać aplikacje za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] i są ograniczone do ustawienia częściowej relacji zaufania. Tej funkcji:  
  
-   Umożliwia wybranie uprawnień, których aplikacja będzie uruchamiana za pomocą.  
  
-   API wyświetlaną w wybranej strefie jako dostępne w listę elementów członkowskich, a następnie Wyświetl interfejsów API, które wymagają dodatkowych uprawnień jako niedostępny.  
  
 Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)



