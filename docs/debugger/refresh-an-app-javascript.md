---
title: Odświeżanie aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: a45564f34fe0167821febb511a023c01f7c38358
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476283"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Odśwież w aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio
  
 Można wprowadzić zmiany w kodzie podczas debugowania kodu, a następnie Odśwież aplikacji platformy uniwersalnej systemu Windows, przy użyciu języka JavaScript, wybierając **aplikacji odświeżania systemu Windows** znajdującego się na **debugowania** paska narzędzi. Wybranie tego przycisku ponowne załadowanie aplikacji bez zatrzymania i ponownego uruchomienia debugera. Funkcja odświeżania umożliwia modyfikowanie kodu HTML, CSS i JavaScript i szybko wyświetlić wyniki. Ta funkcja jest obsługiwana w przypadku aplikacji platformy uniwersalnej systemu Windows.  
  
 Odświeżanie nie zarządzania stanem Twojej aplikacji lub uwzględnić następujące zmiany do swojej aplikacji:  
  
-   Zmiany pliku manifestu pakietu, w tym zmian do obrazów, określona w manifeście pakietu.  
  
-   Odwołanie zmiany, takie jak dodanie lub usunięcie odwołania do zestawu SDK lub zmiana składników środowiska wykonawczego systemu Windows (plików winmd).  
  
-   Zmiany zasobów, takie jak zmiany do ciągów w plikach .resjson.  
  
-   Zmiany pliku projektu, które powodują zmiany nazwy ścieżki, nowe pliki projektu lub usuniętych plików.  
  
-   Zmiany właściwości projektu i elementu, takie jak zmiany na wybranym urządzeniu debugowania lub zmian do pakietu akcji dla plików (w oknie właściwości).  
  
> [!IMPORTANT]
>  Podczas zmiany odwołań, zmień manifest pakietu lub wprowadzić inne zmiany określone w powyższej listy należy zatrzymać i ponownie uruchomić debugera do aktualizacji plików źródłowych HTML, CSS i JavaScript.  
  
### <a name="to-refresh-an-app"></a>Aby odświeżyć aplikacji  
  
1.  Z projektu platformy uniwersalnej systemu Windows otwórz w programie Visual Studio, wybierz **komputera lokalnego** jako cel debugowania.
  
     ![Wybierz opcję debugowania listy docelowej](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.  
  
4.  Przełącz się do programu Visual Studio. 
  
5.  Na stronie głównej aplikacji platformy uniwersalnej systemu Windows edycji niektórych kodu HTML.
  
7.  Kliknij przycisk **aplikacji odświeżania systemu Windows** przycisku, który wygląda podobnie do następującej: ![przycisk aplikacji odświeżania systemu Windows](../debugger/media/js_refresh.png "JS_Refresh"). (Lub naciśnij klawisz F4.)  
  
8.  Przełącz się do aplikacji. Aplikacja zostanie ponownie załadowana i zaktualizowane HTML używany do renderowania aplikacji.
  
## <a name="see-also"></a>Zobacz też  
 [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)