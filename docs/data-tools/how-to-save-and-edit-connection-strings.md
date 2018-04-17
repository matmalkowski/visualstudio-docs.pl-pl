---
title: 'Porady: zapisywanie i Edycja parametrów połączeń | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b3d1da0eba7a113a1a7430b2a2685663dfbd4626
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-save-and-edit-connection-strings"></a>Porady: zapisywanie i edycja parametrów połączeń
Parametry połączenia w aplikacjach Visual Studio można zapisać w pliku konfiguracji aplikacji (nazywane również ustawienia aplikacji) lub ustalony bezpośrednio w aplikacji. Zapisywanie ciągów połączenia w pliku konfiguracji aplikacji upraszcza zadanie obsługi aplikacji. Jeśli parametry połączenia muszą być zmienione, wówczas można zaktualizować go w pliku ustawień aplikacji (zamiast konieczności go zmienić w kodzie źródłowym i ponownie skompilować aplikację).

Przechowuje informacje poufne (na przykład hasło) w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji. Parametry połączenia zapisane w pliku konfiguracyjnym aplikacji nie są szyfrowane lub zaciemniona, dlatego może być osoba dostępu do pliku i wyświetlić jej zawartość. Przy użyciu zintegrowanych zabezpieczeń systemu Windows jest bardziej bezpieczny sposób kontrolowania dostępu do bazy danych.

Jeśli użytkownik nie chce używać zintegrowane zabezpieczenia systemu Windows i baza danych wymaga nazwy użytkownika i hasła, można je pominąć w parametrach połączenia, ale aplikacja będzie musiał podać te informacje do pomyślnego połączenia z bazą danych. Na przykład można utworzyć okno dialogowe, które monituje użytkownika o informacje i dynamicznie tworzy parametry połączenia w czasie wykonywania. Zabezpieczeń może nadal być problemem, jeśli informacje zostaje zatrzymana w drodze do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Aby zapisać parametry połączenia z poziomu Kreatora konfiguracji źródła danych
W **Kreator konfiguracji źródła danych**, wybierz opcję, aby zapisać połączenie na Zapisz parametry połączenia do strony pliku konfiguracji aplikacji.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Aby zapisać parametry połączenia bezpośrednio do ustawień aplikacji
- W Eksploratorze rozwiązań kliknij dwukrotnie ikonę Mój projekt (Visual Basic) lub ikonę właściwości (C#) można otworzyć w Projektancie projektu.
- Wybierz kartę Ustawienia.
- Wprowadź nazwę parametrów połączenia. Podczas uzyskiwania dostępu do ciągu połączenia w kodzie należy odwoływać się do tej nazwy.
- Ustawienia typu (parametry połączenia).
- Pozostaw ustawioną aplikacji zakresu.
- Wpisz ciąg połączenia w polu wartość, lub kliknij przycisk wielokropka (...) w polu wartość, aby otworzyć okno dialogowe właściwości połączenia, aby utworzyć parametry połączenia.  

## <a name="editing-connection-strings-stored-in-application-settings"></a>Edycja ciągów połączenia, przechowywane w ustawieniach aplikacji
Można zmodyfikować informacje o połączeniu, zapisaną w ustawieniach aplikacji przy użyciu projektanta projektu.  

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Aby edytować ciąg połączenia, przechowywane w ustawieniach aplikacji
- W Eksploratorze rozwiązań kliknij dwukrotnie ikonę Mój projekt (Visual Basic) lub ikonę właściwości (C#) można otworzyć w Projektancie projektu.
- Wybierz kartę Ustawienia.
- Zlokalizuj połączenia, który chcesz edytować, a następnie zaznacz tekst, w polu wartość.
- Edytuj parametry połączenia w polu wartość, lub kliknij przycisk wielokropka (...) w polu wartość, aby edytować połączenie, w oknie dialogowym właściwości połączenia.  

## <a name="editing-connection-strings-for-datasets"></a>Edycja ciągów połączenia dla zestawów danych
Można zmodyfikować informacje o połączeniu dla każdego TableAdapter w zestawie danych.  

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Aby edytować ciąg połączenia dla Obiekt TableAdapter w zestawie danych
- W Eksploratorze rozwiązań kliknij dwukrotnie dataset (plik XSD) ma połączenie, które chcesz edytować.
- Wybierz Obiekt TableAdapter lub kwerendę, która ma połączenie, które chcesz edytować.
- W oknie właściwości rozwiń węzeł połączenia.
- Aby szybko zmodyfikować parametrów połączenia, zmień wartość właściwości ConnectionString, lub kliknij strzałkę w dół we właściwościach połączenia i wybierz nowe połączenie.

## <a name="security"></a>Zabezpieczenia
Przechowuje informacje poufne (na przykład hasło) w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji. Przy użyciu zintegrowanych zabezpieczeń systemu Windows jest bardziej bezpieczny sposób kontrolowania dostępu do bazy danych.
Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).
  
## <a name="see-also"></a>Zobacz także
[Dodawanie połączenia](../data-tools/add-new-connections.md)