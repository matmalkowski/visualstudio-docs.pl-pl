---
title: "Szybki Start: tworzenie pierwszej aplikacji Node.js za pomocą programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs: JavaScript
ms.openlocfilehash: e08e08e760075fe250c294c59d4a072e2f529889
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Szybki Start: Program Visual Studio umożliwia tworzenie pierwszej aplikacji Node.js
W tej 5 – 10 min wprowadzenie do programu Visual Studio zintegrowane środowisko programistyczne (IDE) utworzysz prostą aplikację sieci web Node.js. Jeśli program Visual Studio nie został już zainstalowany, zainstaluj go bezpłatnie [tutaj](http://www.visualstudio.com).  

## <a name="create-a-project"></a>Tworzenie projektu
Najpierw utworzysz projekt aplikacji sieci web Node.js.

1. Otwórz program Visual Studio 2017 r.  

2. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu...** .  

3. W **nowy projekt** okno dialogowe, w lewym okienku rozwiń **JavaScript**, a następnie wybierz **Node.js**. W środkowym okienku wybierz **aplikacji sieci Web Node.js puste**, a następnie wybierz **OK**.   

     Jeśli nie widzisz **aplikacji sieci Web Node.js puste** projektu szablonu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Wybierz **programowanie Node.js** obciążenia, a następnie wybierz **Modyfikuj**.  

     ![Obciążenie node.js w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)  

    Program Visual Studio tworzy i nowe rozwiązanie i otworzy w projekcie. **Server.js** otwarty w edytorze.

## <a name="explore-the-ide"></a>Eksploruj IDE  

1. Spójrz na **Eksploratora rozwiązań** w okienku po prawej stronie.

   ![Eksplorator rozwiązań](../ide/media/quickstart-nodejs-solution-explorer.png)  

  - Wyróżnione czcionką pogrubioną jest projekt używa tej nazwy należy nadać w **nowy projekt** okno dialogowe. Na dysku ten projekt jest reprezentowana przez plik .njsproj w folderze projektu.

  - Na najwyższym poziomie to rozwiązanie, które domyślnie ma taką samą nazwę jak projektu. Rozwiązanie reprezentowane przez plik .sln miejsca na dysku jest kontenerem dla jednego lub więcej powiązanych projektów.

  - Węzeł npm zawiera wszystkie pakiety zainstalowane npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm wyszukiwanie i instalowanie pakietów npm za pomocą okna dialogowego.

1. Jeśli chcesz zainstalować pakiet npm lub node.js polecenia z wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz pozycję **Otwórz wiersz polecenia w tym miejscu**.

   ![Wiersz polecenia node.js](../ide/media/quickstart-nodejs-command-prompt.png) 

1. W **server.js** plik w edytorze (lewe okienko), wybierz `http.createServer` , a następnie naciśnij klawisz **F12** lub wybierz **przejdź do definicji** z menu kontekstowego (kliknij prawym przyciskiem myszy). To polecenie powoduje przejście do definicji `createServer` w index.d.ts funkcji.  

   ![Menu kontekstowe przejdź do definicji](../ide/media/quickstart-nodejs-gotodefinition.png)  

1. Umieść kursor na końcu ciągu w tym wierszu kodu, `res.end('Hello World\n');`i zmodyfikuj go, aby wygląda następująco:

    `res.end('Hello World\n' + res.connection.`

    Należy wpisać `connection.`, IntelliSense udostępnia opcje umożliwiające automatyczne zakończenia kod.

   ![Funkcja automatycznego uzupełniania IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)  

1. Wybierz **port lokalny**, a następnie wpisz `);` do wykonania instrukcji, dzięki czemu wygląda następująco:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Uruchamianie aplikacji
1. Naciśnij klawisz **Ctrl + F5** (lub **Debuguj > Uruchom bez debugowania**) do uruchomienia aplikacji. Aplikacja zostanie otwarty w przeglądarce.  

1. W oknie przeglądarki pojawi się "Hello World" oraz numer portu lokalnego.

1. Zamknij przeglądarkę sieci web.  

Gratulujemy Kończenie pracy tego przewodnika Szybki Start! Mamy nadzieję, że znasz nieco o środowiska IDE programu Visual Studio. Jeśli chcesz delve głębiej do jego możliwości, kontynuuj samouczek w **samouczki** sekcji spisu treści.  

## <a name="next-steps"></a>Następne kroki 

- Przejdź przez [samouczka dla środowiska Node.js](../nodejs/tutorial-nodejs.md)  
- Dowiedz się więcej o [programu Visual Studio IDE](../ide/visual-studio-ide.md)  
- Dowiedz się więcej o [narzędzia Node.js dla programu Visual Studio](https://github.com/Microsoft/nodejstools/wiki)