---
title: Wdrażanie niestandardowych Start stron | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2cdbd301d48b0133268a40614178040271fcfc34
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237643"
---
# <a name="deploy-custom-start-pages"></a>Wdrażanie niestandardowych stron Start

Niestandardowe strony Start można wdrożyć za pomocą VSIX wdrażania lub kopiowania plików do poprawnych lokalizacji na komputerze docelowym.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>VSIX wdrożenia za pomocą szablonu projektu strony Start

Podczas tworzenia strony początkowej za pomocą szablonu projektu strony początkowej, a następnie Skompiluj projekt programu Visual Studio tworzy plik .vsix, którą można dystrybuować. Pakowanie strony początkowej w pliku .vsix zapewnia następujące opcje wdrażania, w zależności od zamierzonego odbiorców:

-   Możesz umieścić plik .vsix w udziale sieciowym lub w publicznej witrynie sieci Web. Strona początkowa jest instalowany automatycznie podczas otwierania tego pliku.

-   Możesz przekazać plik .vsix [galerii programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) witryna sieci Web, dzięki czemu użytkownicy mogą zainstalować ją za pomocą **Menedżera rozszerzenia**.

Szablon projektu strony początkowej tworzy kopię domyślne Visual Studio — strona początkowa, dzięki czemu można modyfikować kopii i zachować oryginalne.

Szablon projektu strony początkowej można uzyskać za pomocą **Menedżera rozszerzenia** lub pobrać z witryny sieci Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Wdrożenie VSIX bez użycia szablonu projektu strony Start
 Pomyślne wdrożenie VSIX wymaga można zainstalować w folderach, które są rozpoznawane przez proces rejestracji VSIX i przez rozszerzenie **Menedżera rozszerzenia**. Ponieważ szablon projektu strony początkowej określa już prawidłowe foldery, zalecane jest użycie go w każdym przypadku, gdy chcesz rozszerzenie VSIX wdrożenia pakietu. Jednak jeśli przypadek, w którym nie można użyć szablonu, można utworzyć wdrożenia VSIX bez korzystania z niego.

 Aby utworzyć wdrożenie VSIX bez użycia szablonu projektu strony początkowej, należy najpierw utworzyć plik .vsix dla strony początkowej w jeden z tych dwóch sposobów:

-   Dodając niestandardowe pliki strony początkowej do pustego projektu VSIX. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).

-   Tworząc ręcznie .vsix plik. Aby ręcznie utworzyć plik .vsix:

    1.  Utwórz plik extension.vsixmanifest i pliku XML [Content_Types] w nowym folderze. Aby uzyskać więcej informacji, zobacz [anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

    2.  W Eksploratorze Windows kliknij prawym przyciskiem myszy folder, który zawiera dwa pliki XML, kliknij przycisk Wyślij do, a następnie kliknij Folder skompresowane. Zmień nazwę wynikowy plik zip na Filename.vsix, gdzie nazwa pliku jest nazwą pliku do dystrybucji, który instaluje pakiet.

 Dla programu Visual Studio do rozpoznawania stronę startową `Content Element` VSIX Manifest musi zawierać `CustomExtension Element` mający `Type` ustawić atrybutu `"StartPage"`. Rozszerzenie strony początkowej, który został zainstalowany przy użyciu wdrożenia VSIX jest wyświetlana w **dostosowanie strony początkowej** listy na **uruchamiania** Opcje strony jako **[zainstalowane rozszerzenia]** *Nazwa rozszerzenia*.

 Jeśli strona początkowa pakiet zawiera zestawy, należy dodać powiązanie ścieżkę rejestracji, aby były dostępne po uruchomieniu programu Visual Studio. Aby to zrobić, upewnij się, że pakiet zawiera plik .pkgdef zawiera następujące informacje.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>VSIX wdrożenia dla wszystkich użytkowników
 Domyślnie rozszerzenia wdrożone w pakietach VSIX instalować tylko dla bieżącego użytkownika. Istnieje możliwość instalacji strony początkowej dla wszystkich użytkowników komputera docelowego przez utworzenie wdrożenia u wszystkich użytkowników.

#### <a name="to-create-an-all-users-deployment"></a>Aby utworzyć wdrożenie u wszystkich użytkowników

1.  Otwórz plik extension.vsixmanifest w widoku kodu.

2.  W `Identifier` Dodaj element manifestu vsix `AllUsers` element, który ma wartość `true`.

    ```
    <AllUsers>true</AllUsers>
    ```

     Powoduje to Instalatora vsix, aby monitować o podanie uprawnień administratora, a następnie zainstaluj pliki \Common7\IDE\Extensions.

3.  Otwórz plik .pkgdef.

4.  Modyfikowanie .pkgdef można ustawić domyślną strony początkowej w obszarze HKLM, dodając następujące polecenie, gdzie *MyStartPage.xaml* to nazwa pliku .xaml, która zawiera stronę początkową.

     [$RootKey$ \StartPage\Default]

     "Identyfikator Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     Ta wartość informuje Visual miały do wyszukiwania w nowej lokalizacji strony początkowej.

## <a name="file-copy-deployment"></a>Wdrożenia kopiowania plików
 Nie trzeba utworzyć plik .vsix wdrażania niestandardowej strony początkowej. Zamiast tego możesz skopiować znaczniki i pliki pomocnicze bezpośrednio w folderze \StartPages\ użytkownika. **Dostosowanie strony początkowej** listy na **uruchamiania** opcje strona zawiera listę wszystkich plików .xaml w tym folderze, podając ścieżkę — na przykład %USERPROFILE%\My Documents\Visual Studio  *Wersja*\StartPages\\*nazwę pliku*.xaml. Jeśli strona początkowa zawiera odwołania do zestawów prywatnych, należy skopiować je i wklej je w folderze \PrivateAssemblies\.

 Do dystrybucji strony początkowej, utworzony bez tworzenia pakietów w pliku .vsix zalecamy Użyj strategii kopię podstawowego pliku na przykład skrypt wsadowy lub innych technologii wdrażania, które umożliwia umieszczenie plików w katalogach wymagane.

### <a name="to-manually-install-a-custom-start-page"></a>Aby ręcznie zainstalować niestandardowej strony początkowej

1.  Plik .xaml, który zawiera kod znaczników strony początkowej oraz wszelkie pliki pomocnicze innego niż zestawy, skopiuj i wklej je w folderze \StartPages\ użytkownika.

2.  Jeśli strona początkowa wymaga zestawy, skopiuj je i wklej je w... \\ *Folder instalacji programu visual Studio*\Common7\IDE\PrivateAssemblies\\.

3.  W **dostosowanie strony początkowej** listy na **uruchamiania** opcji wybierz Nowa strona początkowa. Aby uzyskać więcej informacji, zobacz [Dostosowywanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Dostosowanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md)
- [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)