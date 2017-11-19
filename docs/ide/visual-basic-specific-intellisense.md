---
title: "IntelliSense specyficzne dla języka Visual Basic | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f140a0eaf5d464ec4ead377d86257a8627fd6da4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="visual-basic-specific-intellisense"></a>IntelliSense specyficzne dla Visual Basic
Edytor kodu źródłowego języka Visual Basic oferuje następujące funkcje IntelliSense:  
  
-   Porady dotyczące składni  
  
     Porady dotyczące składni Wyświetlanie składni instrukcji, która wpisywania. Jest to przydatne dla instrukcji takich jak [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).  
  
## <a name="automatic-completion"></a>Automatyczne uzupełnianie  
  
-   Ukończenia różnych słów kluczowych  
  
     Na przykład jeśli wpiszesz `goto` i miejsca, IntelliSense wyświetli listę etykiet zdefiniowanych w menu rozwijanym. Obejmują innych obsługiwanych słów kluczowych `Exit`, `Implements`, `Option`, i `Declare`.  
  
-   Ukończenia `Enum` i`Boolean`  
  
     Gdy oświadczenie będzie odwoływać się do elementu członkowskiego wyliczenia, IntelliSense wyświetla listę elementów członkowskich `Enum`. Po instrukcji odnoszą się do `Boolean`, IntelliSense spowoduje wyświetlenie menu rozwijanego PRAWDA / FAŁSZ.  
  
 Uzupełnianie można wyłączyć domyślnie przez wyłączenie **automatyczna lista członków** z **ogólne** stronę właściwości w **Visual Basic** folderu.  
  
 Uzupełnianie można wywołać ręcznie za pomocą listy elementów członkowskich, całe słowo lub ALT + Strzałka w prawo. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md).  
  
## <a name="intellisense-in-zone"></a>IntelliSense w strefie  
 IntelliSense w strefie pomaga deweloperów języka Visual Basic, którzy muszą wdrażać aplikacje za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] i są ograniczone do ustawień częściowej relacji zaufania. Ta funkcja:  
  
-   Umożliwia wybranie uprawnienia, których aplikacja będzie uruchamiana z.  
  
-   Interfejsy API wyświetlania w wybranej strefy jako dostępne w elementach członkowskich listy, a następnie wyświetlić interfejsów API, które wymagają dodatkowych uprawnień jako niedostępny.  
  
 Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z IntelliSense](../ide/using-intellisense.md)