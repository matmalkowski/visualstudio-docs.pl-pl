---
title: 'Porady: Dodawanie walidacji do klas jednostek | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f512a330a1253f0db9b0f7e75de5f0a6ca52658d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775764"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Porady: Dodawanie walidacji do klas jednostek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Dodawanie walidacji do klas jednostek](https://docs.microsoft.com/visualstudio/data-tools/how-to-add-validation-to-entity-classes).  
  
  
*Sprawdzanie poprawności* klas jednostek jest procesem potwierdzania, że wartości wprowadzone w obiektach danych są zgodne z ograniczeniami w schemacie obiektu, a także zasadami ustanowionymi dla aplikacji. Sprawdzanie poprawności danych, aby wysłać aktualizacje do podstawowej bazy danych jest dobrą praktyką, która zmniejsza błędy. Zmniejsza to także potencjalną liczbę rund między aplikacją a bazą danych.  
  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) dostarcza metod częściowych, które umożliwiają użytkownikom Rozszerz kod wygenerowany przez projektanta, który jest uruchamiany podczas operacji wstawiania, aktualizacji i usuwa pełną jednostek, a także podczas i po poszczególnych kolumn zmiany.  
  
> [!NOTE]
>  Ten temat zawiera podstawowe kroki Dodawanie walidacji do klas jednostek za pomocą [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Ponieważ może być trudne do tych kroków ogólny bez odwołujące się do klasy określonej jednostki, podano wskazówki, korzystającej z rzeczywistych danych.  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Dodawanie sprawdzania poprawności zmian do wartości w określonej kolumnie  
 Ta procedura pokazuje sposób sprawdzania poprawności danych, po zmianie wartości w kolumnie. Ponieważ Weryfikacja odbywa się wewnątrz definicji klasy (zamiast interfejsu użytkownika) jest zgłaszany wyjątek, jeśli wartość powoduje, że weryfikacja nie powiedzie się. Implementuje obsługę błędów dla kodu w aplikacji, który podejmie próbę zmiany wartości w kolumnach.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>Aby sprawdzić poprawność danych podczas zmiany wartości w kolumnie  
  
1.  Otwórz lub Utwórz nowy plik LINQ to SQL klas (**dbml** pliku) w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Kliknij dwukrotnie **dbml** w pliku **Eksploratora rozwiązań**.)  
  
2.  W Projektancie obiektów relacyjnych, kliknij prawym przyciskiem myszy klasę, dla którego chcesz dodać sprawdzanie poprawności, a następnie kliknij przycisk **Wyświetl kod**.  
  
     Zostanie otwarty Edytor kodu klasę częściową dla klasy wybranego obiektu.  
  
3.  Umieść kursor w klasie częściowej.  
  
4.  Dla projektów języka Visual Basic:  
  
    1.  Rozwiń **nazwę metody** listy.  
  
    2.  Znajdź **na**_COLUMNNAME_**zmiana** metody dla kolumny, które chcesz dodać sprawdzanie poprawności, aby.  
  
    3.  `On` *COLUMNNAME* `Changing` metoda jest dodawana do klasy częściowej.  
  
    4.  Dodaj następujący kod, aby najpierw sprawdź, czy wprowadzona wartość, a następnie upewnij się, że wprowadzona dla kolumny, która wartość jest dopuszczalny dla aplikacji. `value` Argument zawiera proponowana wartość, więc Dodaj logikę, aby upewnić się, że jest prawidłowa wartość:  
  
        ```vb  
        If value.HasValue Then  
            ' Add code to ensure that the value is acceptable.  
            ' If value < 1 Then  
            '    Throw New Exception("Invalid data!")  
            ' End If  
        End If  
        ```  
  
     Dla projektów C#:  
  
    1.  Ponieważ projektów języka C# nie generują automatycznie obsługi zdarzeń, można użyć funkcji IntelliSense do tworzenia metody częściowe zmieniającej się kolumny.  
  
         Typ `partial` i następnie spację, aby uzyskać dostęp do listy dostępnych metod częściowych. Kliknij metodę zmieniającej się kolumny dla kolumny, które chcesz dodać sprawdzanie poprawności. Poniższy kod jest podobny kod, który jest generowany po wybraniu metody częściowej zmieniającej się kolumny:  
  
        ```csharp  
        partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
            {  
               throw new System.NotImplementedException();  
            }  
  
        ```  
  
## <a name="adding-validation-for-updates-to-an-entity-class"></a>Dodawanie sprawdzania poprawności dla aktualizacji do klasy jednostki  
 Oprócz sprawdzania wartości podczas wprowadzania zmian, możesz również walidować dane podczas próby aktualizacji klasy całą jednostkę. Sprawdzanie poprawności podczas próby aktualizacji umożliwia porównanie wartości w wielu kolumnach, jeśli reguły biznesowe tego wymagać. Poniższa procedura pokazuje, jak sprawdzania poprawności, gdy podejmowana jest próba aktualizacja klasy całą jednostkę.  
  
> [!NOTE]
>  Kod sprawdzania poprawności na zakończenie klas jednostek aktualizacji jest wykonywana w części <xref:System.Data.Linq.DataContext> klasy (a nie w klasie częściowej klasy określonej jednostce).  
  
#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Aby sprawdzić poprawność danych podczas aktualizacji do klasy jednostki  
  
1.  Otwórz lub Utwórz nowy plik LINQ to SQL klas (**dbml** pliku) w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Kliknij dwukrotnie **dbml** w pliku **Eksploratora rozwiązań**.)  
  
2.  Kliknij prawym przyciskiem myszy pusty obszar na O/R Designer, a następnie kliknij przycisk **Wyświetl kod**.  
  
     Zostanie otwarty Edytor kodu za pomocą klasę częściową dla `DataContext`.  
  
3.  Umieść kursor w klasie częściowej dla `DataContext`.  
  
4.  Dla projektów języka Visual Basic:  
  
    1.  Rozwiń **nazwę metody** listy.  
  
    2.  Kliknij przycisk **aktualizacji**_ENTITYCLASSNAME_.  
  
    3.  `Update` *ENTITYCLASSNAME* metoda jest dodawana do klasy częściowej.  
  
    4.  Dostęp do wartości poszczególnych kolumn przy użyciu `instance` argumentu, jak pokazano w poniższym kodzie:  
  
        ```vb  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
     Dla projektów C#:  
  
    1.  Ponieważ projektów języka C# nie generują automatycznie obsługi zdarzeń, można użyć funkcji IntelliSense do utworzenia częściowego `Update` *CLASSNAME* metody.  
  
    2.  Typ `partial` i następnie spację, aby uzyskać dostęp do listy dostępnych metod częściowych. Kliknij metodę aktualizacji dla klasy, które chcesz dodać sprawdzanie poprawności. Poniższy kod jest podobny kod, który jest generowany, gdy wybierzesz `Update` *CLASSNAME* metody częściowej:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)

