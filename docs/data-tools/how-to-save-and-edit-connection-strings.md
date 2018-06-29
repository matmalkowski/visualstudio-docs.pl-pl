---
title: 'Porady: zapisywanie i edycja parametrów połączeń'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 050d5f7bcda86890642a5bef10fa04d2c12b4203
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089234"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Porady: zapisywanie i Edycja parametrów połączeń
Parametry połączenia w aplikacjach Visual Studio są zapisywane w pliku konfiguracji aplikacji (nazywane również ustawienia aplikacji) lub ustalony bezpośrednio w aplikacji. Zapisywanie ciągów połączenia w pliku konfiguracji aplikacji upraszcza zadanie obsługi aplikacji. Jeśli parametry połączenia muszą być zmienione, możesz je zaktualizować, w pliku ustawień aplikacji (zamiast konieczności go zmienić w kodzie źródłowym i ponownie skompilować aplikację).

Przechowuje informacje poufne (na przykład hasło) w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji. Parametry połączenia zapisane w pliku konfiguracyjnym aplikacji nie są szyfrowane lub zaciemniona, dlatego może być osoba dostępu do pliku i wyświetlić jej zawartość. Przy użyciu zintegrowanych zabezpieczeń systemu Windows jest bardziej bezpieczny sposób kontrolowania dostępu do bazy danych.

Jeśli użytkownik nie chce używać zintegrowane zabezpieczenia systemu Windows i baza danych wymaga nazwy użytkownika i hasła, można je pominąć w parametrach połączenia, ale aplikacja będzie musiał podać te informacje do pomyślnego połączenia z bazą danych. Na przykład można utworzyć okno dialogowe, które monituje użytkownika o informacje i dynamicznie tworzy parametry połączenia w czasie wykonywania. Zabezpieczeń może nadal być problemem, jeśli informacje zostaje zatrzymana w drodze do bazy danych.
Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Aby zapisać parametry połączenia z poziomu Kreatora konfiguracji źródła danych
W **Kreator konfiguracji źródła danych**, wybierz opcję, aby zapisać połączenie w **zapisać parametry połączenia do pliku konfiguracji aplikacji** strony.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Aby zapisać parametry połączenia bezpośrednio do ustawień aplikacji
1. W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** ikona (Visual Basic) lub **właściwości** ikona (C#) można otworzyć **projektanta projektu** .
1. Wybierz **ustawienia** kartę.
1. Wprowadź **nazwa** ciągu połączenia. Podczas uzyskiwania dostępu do ciągu połączenia w kodzie należy odwoływać się do tej nazwy.
1. Ustaw **typu** do (**ciąg połączenia**).
1. Pozostaw **zakres** ustawioną **aplikacji**.
1. Wpisz ciąg połączenia w **wartość** pól, lub kliknij przycisk **wielokropka** przycisk (...) w **wartość** pole, aby otworzyć **właściwości połączenia** okno dialogowe Tworzenie parametrów połączenia.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Edytuj parametry połączenia, przechowywane w ustawieniach aplikacji
Można zmodyfikować informacje dotyczące połączenia, który jest zapisywany w ustawieniach aplikacji przy użyciu **projektanta projektu**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Aby edytować ciąg połączenia, przechowywane w ustawieniach aplikacji
1. W **Eksploratora rozwiązań**, kliknij dwukrotnie **mój projekt** ikona (Visual Basic) lub **właściwości** ikona (C#) można otworzyć **projektanta projektu** .
1. Wybierz **ustawienia** kartę.
1. Zlokalizuj połączenia, aby edytować i wybrać tekst w **wartość** pola.
1. Edytuj parametry połączenia w **wartość** pól, lub kliknij przycisk **wielokropka** przycisk (...) w **wartość** pole, aby edytować połączenie z **połączenia Właściwości** okno dialogowe.

## <a name="edit-connection-strings-for-datasets"></a>Edytuj parametry połączenia dla zestawów danych
Można zmodyfikować informacje o połączeniu dla każdego TableAdapter w zestawie danych.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Aby edytować ciąg połączenia dla Obiekt TableAdapter w zestawie danych
1. W **Eksploratora rozwiązań**, kliknij dwukrotnie plik zestawu danych (**XSD** pliku) mający połączenia, który chcesz edytować.
1. Wybierz **TableAdapter** lub kwerendę, która ma połączenie, którą chcesz edytować.
1. W **właściwości** okna, rozwiń węzeł **węzła połączenia**.
1. Aby szybko zmodyfikować parametrów połączenia, należy edytować **ConnectionString** właściwości, lub kliknij strzałkę w dół na **połączenia** właściwości i wybierz polecenie **nowe połączenie**.

## <a name="security"></a>Zabezpieczenia
Przechowuje informacje poufne (na przykład hasło) w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji. Przy użyciu zintegrowanych zabezpieczeń systemu Windows jest bardziej bezpieczny sposób kontrolowania dostępu do bazy danych.
Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Zobacz także

- [Dodawanie połączenia](../data-tools/add-new-connections.md)