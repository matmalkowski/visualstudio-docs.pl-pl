---
title: 'Porady: odblokować programu Visual Studio'
ms.date: 07/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a85e2d8f057a84b56553e8592b3f6a5e390690a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943121"
---
# <a name="how-to-unlock-visual-studio"></a>Porady: odblokować programu Visual Studio

Visual Studio można ocenić bezpłatnie do 30 dni. Logowanie do środowiska IDE rozszerza okresu próbnego do 90 dni. Aby nadal używać programu Visual Studio, odblokowywania środowiska IDE przez:

- za pomocą subskrypcji usługi online

- wprowadzania klucza produktu

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Aby odblokować programu Visual Studio za pomocą subskrypcji usługi online

Aby odblokować programu Visual Studio przy użyciu subskrypcji MSDN lub Visual Studio Team usługi skojarzone z kontem Microsoft lub konta służbowego:

1. Polecenie **Zaloguj** przycisk w prawym górnym rogu IDE (lub przejdź do **pliku** > **ustawienia konta** otworzyć **ustawienia konta**  okno dialogowe i kliknięcie **Zaloguj** przycisku).

1. Wprowadź poświadczenia dla konta Microsoft lub konta służbowego. Program Visual Studio umożliwia znalezienie subskrypcji programu Visual Studio lub Visual Studio Team Services subskrypcji skojarzonych z Twoim kontem.

> [!IMPORTANT]
> Visual Studio automatycznie wyszukuje skojarzone subskrypcji online podczas łączenia z kontem usługi Visual Studio Team Services z **Team Explorer** okna narzędzia. Po ustanowieniu połączenia z kontem usługi Visual Studio Team Services można Zaloguj się przy użyciu zarówno firmy Microsoft, jak i pracy lub szkołą kont. Jeśli istnieje subskrypcją w trybie online dla tego konta użytkownika, programu Visual Studio automatycznie odblokowywania środowiska IDE dla Ciebie.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Aby odblokować programu Visual Studio przy użyciu klucza produktu

1. Wybierz **pliku** > **ustawienia konta** otworzyć **ustawienia konta** okno dialogowe i kliknięcie **licencji przy użyciu klucza produktu**łącza.

Wprowadź klucz produktu w odpowiednim miejscu.

> [!TIP]
> Wersje wstępne programu Visual Studio nie ma kluczy produktów. Możesz zalogować się do środowiska IDE do użycia wersje wstępne.

## <a name="address-license-problem-states"></a>Stany problem licencji adresów

### <a name="update-stale-licenses"></a>Licencje starych aktualizacji

 Może już wspomniano poniżej komunikat, który licencja jest przestarzała w programie Visual Studio, który brzmi, "licencja stała się przestarzała i trzeba ją zaktualizować."

 ![Komunikat starych licencji usługi Visual Studio](../ide/media/vs2017_stale-license.png)

 Ten komunikat oznacza, że podczas subskrypcji nadal może być nieprawidłowa licencja, jaką tokenu Visual Studio będzie korzystać aktualności subskrypcji nie została odświeżona i stała się przestarzała z jednego z następujących powodów:

- Visual Studio nie zostały użyte lub nie miały Brak połączenia internetowego przez dłuższy czas.
- Nastąpiło wylogowanie Visual Studio.

Token licencji przejdzie starych, Visual Studio najpierw zapisuje komunikat ostrzegawczy pytaniem, aby ponownie wprowadzić swoje poświadczenia.

W przypadku nie ponownie wprowadzić swoje poświadczenia, token rozpoczyna Przejdź starych i **ustawienia konta** okna dialogowego informuje o ile dni masz jeszcze przed token pełni wygaśnie. Po wygaśnięciu tokenu programu, należy ponownie poświadczenia dla tego konta lub licencji z innej metody powyżej, aby kontynuować przy użyciu programu Visual Studio.

> [!Important]
> Jeśli używasz programu Visual Studio przez dłuższy czas, w środowiskach o ograniczonym lub Brak dostępu do Internetu, należy używać klucza produktu można odblokować programu Visual Studio, aby uniknąć zakłócenia.

### <a name="update-expired-licenses"></a>Aktualizacja wygasłego licencji

 Jeśli subskrypcja utraciła ważność całkowicie i nie ma praw dostępu do programu Visual Studio, możesz odnowić subskrypcję, lub dodać innego konta, które ma subskrypcję. Aby uzyskać więcej informacji o licencji są używane, przejdź do **pliku** > **ustawienia konta** i przyjrzyj się informacje o licencji po prawej stronie okna dialogowego. Jeśli masz inną subskrypcję skojarzoną z innego konta, należy dodać to konto do **wszystkich kont** listy po lewej stronie okna dialogowego, wybierając **Dodaj konto** łącza.

## <a name="see-also"></a>Zobacz także

* [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md)