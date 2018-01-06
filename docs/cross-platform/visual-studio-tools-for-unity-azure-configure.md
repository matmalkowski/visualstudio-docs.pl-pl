---
title: "Visual Studio Tools for Unity skonfigurować wskazówki Azure | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: BAE62C27-CA7A-4466-8738-3DB880221CE1
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 25424ea06c01224bb1b35f783be82a857b991adf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configure-easy-tables-in-azure"></a>Skonfigurowanie łatwego tabel na platformie Azure

Łatwe tabele są funkcją [Azure Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/) umożliwiające Konfiguracja i zarządzanie tabelami SQL bezpośrednio w portalu Azure graficznego interfejsu użytkownika. Aplikacje mobilne platformy Azure obsługuje wiele funkcji, ale zakres, w tym przykładzie jest ograniczony do odczytywania i zapisywania danych przechowywanych w zaplecza aplikacji mobilnej Azure z projektu platformy Unity.

## <a name="create-a-new-azure-mobile-app"></a>Tworzenie nowej aplikacji mobilnej Azure

Zaloguj się do [portalu Azure](https://ms.portal.azure.com). Jeśli nie masz subskrypcji platformy Azure, [bezpłatnej wersji próbnej](https://azure.microsoft.com/en-us/free/) lub częścią środki na korzystanie z [podstawowe informacje dotyczące programu Visual Studio Dev](https://www.visualstudio.com/dev-essentials/) więcej niż wystarczy wykonywania czynności opisanych w tym przewodniku.

**Raz w portalu:**

1. Wybierz **nowe > sieci Web i mobilność > Aplikacja mobilna > Utwórz**.

  ![Tworzenie nowej aplikacji mobilnej](media/vstu_azure-configure-easy-tables-image1.png)

2. Konfigurowanie nowej aplikacji mobilnej:

  * **Nazwa aplikacji**. Będzie to utworzyć adres URL używany do łączenia z zaplecza aplikacji mobilnej Azure. Należy wybrać unikatową nazwę, wskazane przez zielonym znacznikiem wyboru.

  * **Subskrypcja**. Wybierz subskrypcję, używanego w nowej aplikacji mobilnej dla rozliczeń.

  * **Grupa zasobów**. Grupy zasobów umożliwiają łatwiejsze zarządzanie powiązane zasoby. Domyślnie Azure tworzy nową grupę zasobów o takiej samej nazwie jako nową aplikację. Domyślnie dobrze się sprawdza przewodnika.

  *  **Lokalizacja planu usługi aplikacji**. Plan usługi nakazują mocy obliczeniowej, lokalizacji i koszt zasobów używanych do obsługi nowej aplikacji mobilnej Azure. Domyślnie Azure utworzy nowy plan usługi niektóre ustawienia domyślne. Jest to najprostsza opcja w ramach tego przewodnika. Jednak można użyć tego menu dostosować warstwy cenowej nowy plan usługi lub lokalizacji geograficznej. Ponadto można modyfikować ustawienia planu usługi po jej wdrożeniu.

  ![Tworzenie nowej aplikacji mobilnej](media/vstu_azure-configure-easy-tables-image2.png)

3. Wybierz **Utwórz** i nadaj Azure na kilka minut, aby wdrożyć nowy zasób. Zostanie wyświetlone powiadomienie w portalu Azure, po zakończeniu wdrożenia.

## <a name="add-a-new-data-connection"></a>Dodaj nowe połączenie danych

4. Po zakończeniu wdrożenia kliknij **wszystkie zasoby** przycisk, a następnie wybierz nowo utworzony aplikacji mobilnej.

  ![Wybierz nowej aplikacji mobilnej](media/vstu_azure-configure-easy-tables-image3.png)

5. W nowo otwartym bloku, przewiń w dół w lewym menu po stronie i kliknij przycisk **łatwe tabel** przycisk kategorii **MOBILE** nagłówka.

  ![Wybierz tabele łatwe](media/vstu_azure-configure-easy-tables-image4.png)

6. Polecenie **należy skonfigurować łatwe tabel/łatwy interfejsów API** Zwróć uwagę, wyświetlanie wzdłuż górnej części bloku łatwe tabel.

  ![Kliknij opcję Konfiguruj powiadomienie łatwe tabel](media/vstu_azure-configure-easy-tables-image5.png)

7. Kliknij przycisk Zwróć uwagę, że mówi **należy używać łatwe tabel bazy danych. Kliknij tutaj, aby utworzyć**.

  ![Kliknij przycisk Utwórz powiadomień bazy danych](media/vstu_azure-configure-easy-tables-image6.png)

8. W bloku połączeń danych, kliknij **Dodaj** przycisku.

  ![Kliknij przycisk Dodaj](media/vstu_azure-configure-easy-tables-image7.png)

9. Na dodawanie bloku połączenia danych, wybierz **bazy danych SQL**.

  ![Wybierz bazę danych SQL](media/vstu_azure-configure-easy-tables-image8.png)

10. Powoduje otwarcie bloku konfigurowania nowej bazy danych SQL i programu SQL server:

  * **Nazwa**. Wprowadź nazwę dla bazy danych.

  * **Serwer docelowy**. Kliknij przycisk **serwer docelowy** aby otworzyć nowy blok serwera.

      * **Nazwa serwera**. Wprowadź nazwę serwera.

      * **Identyfikator logowania administratora serwera i hasło**. Utwórz nazwę użytkownika i hasło administratora serwera.

      * **Lokalizacja**. Wybierz lokalizację pobliskich dla serwera.

      * Upewnij się, że **Zezwalaj usługom platformy azure na dostęp do serwera** pole wyboru jest zaznaczone.

      * Kliknij przycisk **wybierz** do ukończenia konfiguracji serwera.

    * **Warstwa cenowa**. Pozostaw domyślne ustawienie dla przewodnika. To ustawienie można zmodyfikować później.

    * **Sortowanie**. Pozostaw ustawienie domyślne.

    * Kliknij przycisk **wybierz** aby ukończyć konfigurowanie bazy danych.

    ![Konfigurowanie programu SQL server i bazy danych](media/vstu_azure-configure-easy-tables-image9.png)

11. W bloku połączenie danych dodatku, kliknij przycisk **ciąg połączenia**. Gdy zostanie wyświetlony blok ciągu połączenia, pozostaw ustawienia domyślne i kliknij przycisk **OK**.

  ![Kliknij ciąg połączenia](media/vstu_azure-configure-easy-tables-image9.1.png)

12. W bloku połączenie danych dodatku tekst "MS_TableConnectionString" nie powinny już być kursywą. Kliknij przycisk **OK** i zapewnić na kilka minut, aby utworzyć nowe połączenie danych Azure. Powiadomienie o pojawią się po zakończeniu procesu.

  ![Kliknij przycisk OK](media/vstu_azure-configure-easy-tables-image9.2.png)

## <a name="complete-the-easy-table-initialization"></a>Zakończenie inicjowania łatwe tabeli

13. Po nowe połączenie danych został utworzony pomyślnie, kliknij przycisk **wszystkie zasoby** przycisk i ponownie przejdź z powrotem do aplikacji mobilnej. Jest ważne ukończyć ten krok, aby odświeżyć powiadomienia konfiguracji łatwe tabeli.

14. Przewiń w dół i wybierz **łatwe tabel**i ponownie wybierz niebieski **należy skonfigurować łatwe tabel/łatwy interfejsów API** zauważyć.

  ![Kliknij powiadomienie łatwe tabel](media/vstu_azure-configure-easy-tables-image5.png)

15. Teraz wyświetlonym bloku powinny prezentować czy "istnieje już połączenie danych" poniżej **1** nagłówka. W obszarze **2** nagłówek, zaznacz pole wyboru, stwierdzający **potwierdzam, że spowoduje to zastąpienie zawartości witryny.** Teraz kliknij **inicjowania aplikacji** i poczekaj kilka minut na platformie Azure ukończyć proces inicjowania. Nowe powiadomienie będzie ogłaszamy po zakończeniu procesu.

  ![Kliknij przycisk Inicjowanie aplikacji](media/vstu_azure-configure-easy-tables-image10.png)

## <a name="next-step"></a>Następny krok

* [Tworzenie łatwych tabel](visual-studio-tools-for-unity-azure-setup.md)
