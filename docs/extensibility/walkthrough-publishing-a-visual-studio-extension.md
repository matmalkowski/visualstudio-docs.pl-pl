---
title: "Wskazówki: Publikowanie rozszerzenie programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: be1402da1677388712472d4309c40ce767358f7b
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Wskazówki: Publikowanie rozszerzenie programu Visual Studio

Ten przewodnik przedstawia sposób publikowania rozszerzenia programu Visual Studio do programu Visual Studio Marketplace. Podczas dodawania rozszerzenia do witryny Marketplace, deweloperzy mogą używać **rozszerzenia i aktualizacje** do przeglądania istnieje dla nowych i zaktualizowanych rozszerzeń.

## <a name="prerequisites"></a>Wymagania wstępne

 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Tworzenie rozszerzenia programu Visual Studio

W takim przypadku będą używane domyślne rozszerzenie pakiet VSPackage, ale te same kroki są prawidłowe dla wszystkich rodzajów rozszerzenia.

1. Utwórz pakiet VSPackage w języku C# o nazwie "TestPublish", który ma polecenia menu. Aby uzyskać więcej informacji, zobacz [tworzenie pierwszej rozszerzenia: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Pakiet rozszerzenia

1. Zaktualizuj vsixmanifest rozszerzenia przy użyciu prawidłowych informacji o nazwę produktu, autora i wersję.

  ![Zaktualizuj vsixmanifest rozszerzenia](media/update-extension-vsixmanifest.png)

2. Tworzenie rozszerzenia **wersji** tryb. Teraz rozszerzenia zostaną dodane do pakietu jako VSIX w folderze \bin\Release.

3. Możesz dwukrotnie kliknąć VSIX, aby zweryfikować instalację.

## <a name="test-the-extension"></a>Rozszerzenie testu

 Przed rozpoczęciem dystrybucji rozszerzenia, budowania i testowania, aby upewnić się, że jest poprawnie zainstalowana w eksperymentalne wystąpienie programu Visual Studio.

1. W programie Visual Studio Rozpocznij debugowanie. Aby otworzyć eksperymentalne wystąpienie programu Visual Studio.

2. W eksperymentalnym wystąpieniu, przejdź do **narzędzia** menu i kliknij przycisk **rozszerzenia i aktualizacje...** . Można włączyć rozszerzenia TestPublish, powinny być wyświetlane w środkowym okienku.

3. Na **narzędzia** menu, upewnij się, zobacz polecenia testowego.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publikowanie rozszerzenia portalu Marketplace programu Visual Studio

1. Upewnij się, utworzone wersji rozszerzenia i że jest aktualny.

2. Otwórz w przeglądarce sieci web [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) witryny sieci Web.

3. W prawym górnym rogu kliknij **Zaloguj**.

4. Użyj konta Microsoft do logowania. Jeśli nie masz konta Microsoft, należy go utworzyć w tym momencie.

5. Kliknij przycisk **publikowania rozszerzenia**.  Spowoduje to przejście do strony Zarządzanie dla wszystkich rozszerzeń.  Jeśli nie masz konta wydawcy, pojawi się monit o jego utworzenie w tym momencie.

  ![Przekaż do witryny Marketplace](media/upload-to-marketplace.png)

6. Wybierz wydawcę, którego chcesz użyć w celu przekazania Twoje rozszerzenie.  Można zmienić wydawcy, klikając na liście po lewej stronie nazwy wydawców.  Polecenie **nowe rozszerzenie** i wybierz **programu Visual Studio**.

7. W **1: Przekaż rozszerzenia**, możesz przekazać plik VSIX bezpośrednio do programu Visual Studio Marketplace lub po prostu Dodaj łącze własne witryny sieci Web. W takim przypadku będzie przekazać naszych rozszerzenia TestPublish.vsix.  Przeciągnij i upuść rozszerzenie lub użyj **kliknij** łącze, aby wyszukać plik.  Rozszerzenie można znaleźć w folderze \bin\Release projektu.  Kliknij przycisk **Kontynuuj**.

8. W **2: Podaj szczegóły rozszerzenia**, niektóre pola są wypełniane automatycznie z pliku source.extension.vsixmanifest z rozszerzenia.  Więcej informacji o poszczególnych znajduje się poniżej:

    * **Wewnętrzna nazwa** będą używane w adresie URL strony szczegółów rozszerzenia. Na przykład publikowania rozszerzenia w obszarze Nazwa wydawcy "mójużytkownik" i określając wewnętrzna nazwa ma zostać "myextension" spowoduje adresu URL "marketplace.visualstudio\.com/items?itemName=myname.myextension" dla rozszerzenia Strona szczegółów.
    
    * **Nazwa wyświetlana** Twojego rozszerzenia.  To jest wypełniana automatycznie z pliku source.extension.vsixmanifest.
   
    * **Wersja** numer rozszerzenia przekazywania.  To jest wypełniana automatycznie z pliku source.extension.vsixmanifest.
    
    * **Identyfikator VSIX** jest unikatowy identyfikator, który używa programu Visual Studio dla rozszerzenia.  Jest to wymagane, jeśli chcesz mieć rozszerzenie aktualizowane automatycznie.  To jest wypełniana automatycznie z pliku source.extension.vsixmanifest.
    
   * **Logo** który będzie używany dla rozszerzenia.  To jest wypełniana automatycznie od pliku source.extension.vsixmanifest, jeśli zostanie podana.
    
    * **Krótki opis** z czego Twoje rozszerzenie.  To jest wypełniana automatycznie od pliku source.extension.vsixmanifest.
    
    * **Omówienie** jest dobrym miejscem do dołączyć zrzuty ekranu i szczegółowe informacje na temat działania Twoje rozszerzenie.
    
    * **Obsługiwane wersje programu Visual Studio** pozwala wybrać, które wersje programu Visual Studio rozszerzenia będą działać na.  Rozszerzenie zostanie ona zainstalowana tylko w tych wersjach.
    
    * **Obsługiwane wersje programu Visual Studio** pozwala wybrać, które wersje programu Visual Studio rozszerzenia będą działać na.  Rozszerzenie zostanie ona zainstalowana tylko do tych wersji.
    
    * **Typ**.  Najczęściej spotykanym typem rozszerzenia są **narzędzia**.
    
    * **Kategorie**.  Wybierz maksymalnie trzech, które są najbardziej odpowiednie dla rozszerzenia.
    
    * **Tagi** są słowa kluczowe, które pomagają użytkownikom znaleźć rozszerzenia. Tagi może pomóc zwiększyć przydatność wyszukiwania rozszerzeń w witrynie Marketplace.
    
    * **Cennik kategorii** jest koszt Twoje rozszerzenie.
    
    * **Repozytorium kodu źródłowego** umożliwia udostępnianie łącze do kodu źródłowego ze społecznością.
    
    * **Zezwalaj na pytań i odpowiedzi na Twoje rozszerzenie** pozwoli użytkownikom na pozostaw pytań na stronie wpis rozszerzenia.

9. Kliknij przycisk **Zapisz & Przekaż**. Zostanie otwarta strona Zarządzanie Wstecz, aby Twoje wydawcy.  Rozszerzenie nie został opublikowany.  Aby opublikować rozszerzenie, kliknij prawym przyciskiem myszy na Twoje rozszerzenie i wybierz **Upublicznij**.  Możesz wyświetlić sposób rozszerzenia będzie wyglądać w witrynie Marketplace, wybierając **rozszerzenie widoku**.  W przypadku nabycia numerów kliknij **raporty**.  Aby wprowadzić zmiany do rozszerzenia, polecenie **Edytuj*.

  ![Rozszerzenie wpisu Menu](media/extension-entry-menu.png)

10. Po kliknięciu przycisku **Upublicznij**, rozszerzenie teraz jest publiczny.  Wyszukaj w Visual Studio Marketplace na Twoje rozszerzenie.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Dodać użytkowników do zarządzania kontem wydawcy

Marketplace obsługuje przyznawanie uprawnień dodatkowym użytkownikom dostęp do zarządzania kontem wydawcy.

1. Przejdź do konta wydawcy, który chcesz dodać użytkowników do.

2. Wybierz **członków** i wybierz polecenie **Dodaj**

  ![Dodaj dodatkowe użytkownika](media/add-users.png)

3. Następnie możesz określić adres e-mail użytkownika, o których chcesz dodać, a następnie przyznać odpowiedni poziom dostępu w ramach **wybierz rolę**.  Możesz wybrać następujące opcje:

  * **Twórcy**: użytkownika można publikowania rozszerzenia, ale nie można wyświetlić lub zarządzania rozszerzeniami opublikowane przez innych użytkowników.
  
  * **Czytnik**: użytkownika można wyświetlić rozszerzenia, ale nie można opublikować lub zarządzania rozszerzeniami.
  
  * **Współautor**: użytkownik można opublikować i Zarządzaj rozszerzeniami, ale nie można edytować ustawienia wydawcy lub zarządzanie dostępem.
  
  * **Właściciel**: użytkownik może publikować i zarządzać rozszerzeniami, Edytuj ustawienia wydawcy i zarządzanie dostępem.
  
## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Zainstaluj rozszerzenia z witryny Marketplace programu Visual Studio

Teraz, gdy rozszerzenie zostanie opublikowana, zainstaluj go w programie Visual Studio i przetestować go brak.

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje...** .

2. Kliknij przycisk **Online** , a następnie wyszukaj TestPublish.

3. Kliknij przycisk **Pobierz**. Rozszerzenia są planowane do zainstalowania.

4. Aby ukończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuń rozszerzenie

Można usunąć rozszerzenia z witryny Marketplace programu Visual Studio i z tego komputera.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Aby usunąć rozszerzenia z Visual Studio Marketplace

1. Otwórz [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) witryny sieci Web.

2. W prawym górnym rogu kliknij **publikowania** rozszerzenia.  Wybierz wydawcy, który był używany podczas publikowania TestPublish.  Zostanie wyświetlony na liście TestPublish.

3. Kliknij prawym przyciskiem myszy wpis rozszerzenia, a następnie kliknij przycisk **Usuń** użytkownik jest proszony o potwierdzenie, czy chcesz usunąć rozszerzenie.  Kliknij przycisk **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Aby usunąć rozszerzenia z komputera

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje...** .

2. Wybierz TestPublish, a następnie kliknij przycisk **Odinstaluj**. Rozszerzenia są planowane do odinstalowania.

3. Aby ukończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
