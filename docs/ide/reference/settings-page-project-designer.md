---
title: Strona Ustawienia, Projektant projektu
ms.date: 06/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c0f7b47b56522f5c4aeef0054e6b7b52434ff87
ms.sourcegitcommit: 562867be91ee1aebbed4658c8de0949f422860fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/14/2018
ms.locfileid: "35609454"
---
# <a name="settings-page-project-designer"></a>Strona Ustawienia, Projektant projektu

Użyj **ustawienia** strony projektanta projektu, aby określić ustawienia aplikacji projektu. Ustawienia aplikacji pozwalają na przechowywanie i pobieranie ustawień właściwości i inne informacje dotyczące aplikacji dynamicznie. Umożliwiają one również Obsługa niestandardowych aplikacji i preferencji użytkownika na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md).

Aby uzyskać dostęp do **ustawienia** wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie wybierz **projektu** > **właściwości**. Gdy pojawi się w Projektancie projektu, zaznacz **ustawienia** kartę.

## <a name="header-bar"></a>Pasek nagłówka

Na pasku nagłówka w górnej części **ustawienia** strona zawiera kilka formantów:

**Synchronizuj**

**Synchronizuj** przywraca ustawienia zakresu użytkownika, które korzysta z aplikacji w czasie wykonywania, lub podczas debugowania do wartości domyślnych, zgodnie z definicją w czasie projektowania. Aby przywrócić dane, Usuń czasu wykonywania wygenerowanych plików specyficzne dla aplikacji z dysku, a nie z danych projektu.

**Ustawienia sieci Web obciążenia**

**Ładowanie ustawień sieci Web** Wyświetla **logowania** okno dialogowe, którego można załadować ustawień uwierzytelnionego użytkownika lub dla użytkowników anonimowych. Ten przycisk jest aktywny tylko wtedy, gdy aktywowano usługi aplikacji klienta na **usług** strony i określić **Lokalizacja usługi ustawień sieci Web**.

**Kod widoku**

Dla projektów C# **kod widoku** przycisk umożliwia wyświetlenie kodu w *Settings.cs* pliku. Ten plik definiuje `Settings` klasy, która umożliwia obsługę określonych zdarzeń na `Settings` obiektu. W językach innych niż Visual Basic, należy jawnie wywołać `Save` metody tej klasy otoki w celu utrzymania ustawień użytkownika. Zwykle to zrobić w **zamknięcia** obsługi zdarzeń formularza głównego. Poniżej przedstawiono przykładowy wywołania `Save` metody:

```csharp
Properties.Settings.Default.Save();
```

W projektach Visual Basic **kod widoku** przycisk umożliwia wyświetlenie kodu w *Settings.vb* pliku. Ten plik definiuje `MySettings` klasy, która umożliwia obsługę określonych zdarzeń na `My.Settings` obiektu. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji przy użyciu `My.Settings` obiektów, zobacz [dostęp do ustawień aplikacji](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji, zobacz [ustawienia aplikacji dla formularzy systemu Windows](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Modyfikator dostępu**

**Modyfikator dostępu** przycisk określa poziom dostępu `Properties.Settings` (w języku C#) lub `My.Settings` (w języku Visual Basic) pomocnika klas, które generuje Visual Studio w *Settings.Designer.cs* lub *Settings.Designer.vb*.

Projekty Visual C#, modyfikator dostępu można następnie **wewnętrzne** lub **publicznego**.

Projekty Visual Basic modyfikator dostępu można następnie **Friend** lub **publicznego**.

Domyślnym ustawieniem jest **wewnętrzne** w języku C# i **Friend** w języku Visual Basic. Gdy program Visual Studio generuje klasy pomocy jako **wewnętrzne** lub **Friend**, pliku wykonywalnego (*.exe*) aplikacje nie może uzyskiwać dostęp do zasobów i ustawienia, które zostały dodane do biblioteki klas (*.dll* plików). Jeśli masz współużytkowania zasobów i ustawienia z biblioteki klas, ustawioną modyfikator dostępu **publicznego**.

Aby uzyskać więcej informacji na temat klas pomocnika ustawienia, zobacz [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Ustawienia siatki

**Ustawienia siatki** służy do konfigurowania ustawień aplikacji. Ta siatka zawiera następujące kolumny:

**Nazwa**

Wprowadź nazwę ustawienia aplikacji, w tym polu.

**Typ**

Użyj listy rozwijanej, aby wybrać typ ustawienia. Najczęściej używane typy są wyświetlane na liście rozwijanej, na przykład **ciąg**, **(parametry połączenia)**, i **System.Drawing.Font**. Można wybrać innego typu, wybierając **Przeglądaj** na końcu listy, a następnie wybierając typ z **wybierz typ** okno dialogowe. Po wybraniu typu, jest ona dodawana do typowych na liście rozwijanej (dla bieżącego rozwiązania tylko).

**Zakres**

Wybierz opcję **aplikacji** lub **użytkownika**.

Ustawienia zakresu aplikacji, takie jak parametry połączenia są skojarzone z aplikacją. Użytkownicy nie mogą zmieniać ustawień z zakresu aplikacji w czasie wykonywania.

Ustawienia zakresu użytkownika, takich jak system czcionki, są przeznaczone służący do preferencji użytkownika. Użytkownicy mogą zmieniać ich w czasie wykonywania.

**Wartość**

Dane lub wartość skojarzoną z ustawienia aplikacji. Na przykład, jeśli ustawienie jest czcionka, jego wartość może być **Verdana 9.75pt, style = Bold**.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie ustawieniami aplikacji](../managing-application-settings-dotnet.md)
- [Ustawienia aplikacji dostępu (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)