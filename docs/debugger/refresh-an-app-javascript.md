---
title: "Odśwież platformy uniwersalnej systemu Windows lub Windows 8.1 aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5f5592893452c3fdf7f535758f09d7877030c03
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="refresh-a-uwp-or-windows-81-app"></a>Odśwież platformy uniwersalnej systemu Windows lub Windows 8.1 aplikacji
![Ma zastosowanie do systemu Windows i Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 Można wprowadzić zmiany w kodzie podczas debugowania kodu, a następnie Odśwież aplikacji platformy uniwersalnej systemu Windows, przy użyciu języka JavaScript, wybierając **aplikacji odświeżania systemu Windows** znajdującego się na **debugowania** paska narzędzi. Wybranie tego przycisku ponowne załadowanie aplikacji bez zatrzymania i ponownego uruchomienia debugera. Funkcja odświeżania umożliwia modyfikowanie kodu HTML, CSS i JavaScript i szybko wyświetlić wyniki. Ta funkcja jest obsługiwana w przypadku aplikacji platformy uniwersalnej systemu Windows i Windows 8.1.  
  
 Odświeżanie nie zarządzania stanem Twojej aplikacji lub uwzględnić następujące zmiany do swojej aplikacji:  
  
-   Zmiany pliku manifestu pakietu, w tym zmian do obrazów, określona w manifeście pakietu.  
  
-   Odwołanie zmiany, takie jak dodanie lub usunięcie odwołania do zestawu SDK lub zmiana składników środowiska wykonawczego systemu Windows (plików winmd).  
  
-   Zmiany zasobów, takie jak zmiany do ciągów w plikach .resjson.  
  
-   Zmiany pliku projektu, które powodują zmiany nazwy ścieżki, nowe pliki projektu lub usuniętych plików.  
  
-   Zmiany właściwości projektu i elementu, takie jak zmiany na wybranym urządzeniu debugowania lub zmian do pakietu akcji dla plików (w oknie właściwości).  
  
> [!IMPORTANT]
>  Podczas zmiany odwołań, zmień manifest pakietu lub wprowadzić inne zmiany określone w powyższej listy należy zatrzymać i ponownie uruchomić debugera do aktualizacji plików źródłowych HTML, CSS i JavaScript.  
  
### <a name="to-refresh-an-app"></a>Aby odświeżyć aplikacji  
  
1.  W programie Visual Studio Utwórz nowy projekt za pomocą szablonu projektu aplikacji nawigacji.  
  
     Może to być aplikacji platformy uniwersalnej systemu Windows lub aplikacji Windows 8.1.  
  
2.  Przy użyciu szablonu należy otworzyć w programie Visual Studio, wybierz cel debugowania.  
  
     Jeśli projekt Windows Phone Twój bieżący projekt startowy, wybierz emulator Windows Phone dla elementu docelowego debugowania. W przeciwnym razie wybierz **symulatora** lub **komputera lokalnego**.  
  
     ![Wybierz opcję debugowania listy docelowej](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.  
  
4.  Przełącz się do programu Visual Studio. (Naciśnij klawisz F12).  
  
5.  W **Eksploratora rozwiązań**w **stron** > **macierzystego** folder, otwórz home.html.  
  
6.  Zmień tekst tytułu strony z  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     do czegoś innego następująco:  
  
    ```html  
    Hello!  
    ```  
  
7.  Kliknij przycisk **aplikacji odświeżania systemu Windows** przycisku, który wygląda podobnie do następującej: ![przycisk aplikacji odświeżania systemu Windows](../debugger/media/js_refresh.png "JS_Refresh"). (Lub naciśnij klawisz F4.)  
  
8.  Przełącz się do aplikacji. Aplikacja zostanie ponownie załadowana bez ponownego uruchamiania debugera i pojawi się nowy tytuł strony.  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)