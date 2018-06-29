---
title: 'Porady: Dodawanie walidacji do klas jednostek'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d102bdf20349d6bd4efdecd1c460f1e46646eb37
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089341"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Porady: Dodawanie walidacji do klas jednostek
*Sprawdzanie poprawności* klas jednostek jest proces potwierdzania wartości wprowadzone w obiektach danych są zgodne z ograniczeniami w schemacie obiektu, a także do reguły dla aplikacji. Sprawdzanie poprawności danych, aby wysyłać aktualizacje do podstawowej bazy danych jest dobrym rozwiązaniem, które zmniejsza błędy. Zmniejsza liczbę rund między aplikacją i bazy danych.

 [Narzędzi LINQ do SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) udostępnia częściowej metody, które użytkownicy mogą rozszerzać kod wygenerowany przez projektanta, który jest uruchamiany podczas operacji wstawiania, aktualizacji i usuwa pełną jednostek, a także podczas i po poszczególnych kolumn zmiany.

> [!NOTE]
>  Ten temat zawiera podstawowe kroki Dodawanie walidacji do klas jednostek przy użyciu **Projektanta obiektów relacyjnych**. Ponieważ może być trudne dla poniższych kroków ogólnych bez odwołujących się do klasy określonej jednostki, jest dostępne wskazówki, który używa danych rzeczywistych.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Dodawanie walidacji do zmiany wartości w określonej kolumnie
 Ta procedura przedstawia sposób sprawdzania poprawności danych w przypadku zmiany wartości w kolumnie. Ponieważ weryfikacja jest przeprowadzana w definicji klasy (a nie w interfejsie użytkownika), jest zwracany wyjątek, jeśli wartość powoduje niepowodzenie sprawdzania poprawności. Implementuje obsługę błędów dla kodu w aplikacji, która próbuje zmienić wartości w kolumnie.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Aby sprawdzić poprawność danych podczas zmiany wartości kolumny

1.  Otwarcia lub utworzenia nowego składnika LINQ to SQL klasy pliku (**.dbml** pliku) w **Projektanta obiektów relacyjnych**. (Kliknij dwukrotnie **.dbml** w pliku **Eksploratora rozwiązań**.)

2.  W **Projektanta obiektów relacyjnych**, kliknij prawym przyciskiem myszy klasę, dla której chcesz dodać sprawdzanie poprawności, a następnie kliknij przycisk **kod widoku**.

     Otwiera edytora kodu z klasy częściowej klasy wybranej jednostki.

3.  Umieść kursor w klasie częściowej.

4.  Dla projektów języka Visual Basic:

    1.  Rozwiń węzeł **nazwę metody** listy.

    2.  Zlokalizuj **OnCOLUMNNAMEChanging** metodę dla kolumny, aby dodać sprawdzania poprawności.

    3.  `OnCOLUMNNAMEChanging` Metoda jest dodawana do klasy częściowej.

    4.  Dodaj następujący kod, aby najpierw sprawdź, czy wprowadzona wartość, a następnie upewnij się, że wartość wprowadzona dla kolumny, która jest możliwa do aplikacji. `value` Argument zawiera proponowanej wartości, a więc Dodaj logikę, aby potwierdzić, że jest nieprawidłowa:

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Dla projektów C#:

    Ponieważ projektów C# nie generują automatycznie procedury obsługi zdarzeń, można użyć funkcji IntelliSense można utworzyć kolumny, zmiana metody częściowe. Typ `partial` , a następnie miejsce dostęp do listy dostępnych metod częściowych. Kliknij metodę zmiana kolumn dla kolumny, która ma zostać dodany sprawdzania poprawności dla. Poniższy kod podobny kod, który jest generowany, gdy wybrana metoda częściowa zmiana kolumny:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Dodawanie walidacji aktualizacji do klasy jednostki
 Oprócz sprawdzenia wartości podczas zmiany, można zweryfikować danych podczas próby aktualizacji klasy całą jednostkę. Sprawdzania poprawności podczas próby aktualizacji umożliwia porównanie wartości w wielu kolumnach, jeśli reguły biznesowe wymagają to. Poniższa procedura przedstawia sposób sprawdzania poprawności, gdy podejmowana jest próba aktualizacji klasy całą jednostkę.

> [!NOTE]
>  Sprawdzanie poprawności kodu na zakończenie klas jednostek aktualizacji są wykonywane w częściowym <xref:System.Data.Linq.DataContext> klasy (zamiast w klasie częściowej klasy jednostki określonych).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Do sprawdzania poprawności danych podczas aktualizacji do klasy jednostki

1.  Otwarcia lub utworzenia nowego składnika LINQ to SQL klasy pliku (**.dbml** pliku) w **Projektanta obiektów relacyjnych**. (Kliknij dwukrotnie **.dbml** w pliku **Eksploratora rozwiązań**.)

2.  Kliknij prawym przyciskiem myszy pusty obszar **Projektanta obiektów relacyjnych** i kliknij przycisk **kod widoku**.

     Otwiera edytora kodu z klasę częściową dla `DataContext`.

3.  Umieść kursor w klasie częściowej dla `DataContext`.

4.  Dla projektów języka Visual Basic:

    1.  Rozwiń węzeł **nazwę metody** listy.

    2.  Kliknij przycisk **UpdateENTITYCLASSNAME**.

    3.  `UpdateENTITYCLASSNAME` Metoda jest dodawana do klasy częściowej.

    4.  Dostęp do wartości poszczególnych kolumn przy użyciu `instance` argumentu, jak pokazano w poniższym kodzie:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Dla projektów C#:

    Ponieważ projektów C# nie generują automatycznie procedury obsługi zdarzeń, można użyć funkcji IntelliSense do utworzenia częściowego `UpdateCLASSNAME` metody. Typ `partial` , a następnie miejsce dostęp do listy dostępnych metod częściowych. Kliknij metodę aktualizacji dla klasy, w której chcesz dodać sprawdzania poprawności. Poniższy kod podobny kod, który jest generowany po wybraniu `UpdateCLASSNAME` metody częściowej:

    ```csharp
    partial void UpdateCLASSNAME(CLASSNAME instance)
    {
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
        {
            string ErrorMessage = "Invalid data!";
            throw new System.Exception(ErrorMessage);
        }
    }
    ```

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)
- [LINQ do SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)