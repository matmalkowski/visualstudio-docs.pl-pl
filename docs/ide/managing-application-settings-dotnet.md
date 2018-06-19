---
title: Zarządzanie ustawieniami aplikacji (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04d2c31db4c117f3bc902218a61656e5eca49e27
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31951024"
---
# <a name="manage-application-settings-net"></a>Zarządzanie ustawieniami aplikacji (.NET)

Ustawienia aplikacji pozwalają dynamicznie przechowywać informacje o aplikacji. Ustawienia umożliwiają przechowywanie danych na komputerze klienckim, który nie powinny znajdować się w kodzie aplikacji (na przykład parametry połączenia), preferencje użytkownika i inne informacje, które są potrzebne w czasie wykonywania.

Ustawienia aplikacji zastąpienie właściwości dynamicznych, używany w starszych wersjach programu Visual Studio.

Każde ustawienie aplikacji musi mieć unikatową nazwę. Nazwa może zawierać dowolną kombinację litery, cyfry i podkreślenia, że nie rozpoczyna się od numeru i nie może zawierać spacji. Nazwa została zmieniona przez `Name` właściwości.

Ustawienia aplikacji mogą być przechowywane jako dowolny typ danych, który jest serializowany do pliku XML lub ma `TypeConverter` implementującej `ToString` / `FromString`. Najbardziej typowych są `String`, `Integer`, i `Boolean`, ale można również przechowywać wartości jako <xref:System.Drawing.Color>, <xref:System.Object>, lub w postaci ciągu połączenia.

Ustawienia aplikacji także zawierać wartość. Ma wartość **wartość** właściwości musi być zgodny z typem danych ustawienie.

Ponadto ustawienia aplikacji może być powiązana z właściwością formularza lub kontrolki, w czasie projektowania.

Istnieją dwa typy ustawień aplikacji, w oparciu o zakresie:

- Informacje takie jak adres URL usługi sieci Web lub parametry połączenia bazy danych można użyć ustawień zakresu aplikacji. Te wartości są skojarzone z aplikacją. W związku z tym użytkownicy nie mogą zmieniać ich w czasie wykonywania.

- Ustawień z zakresu użytkownika można uzyskać informacje, takie jak utrwalanie ostatniej pozycji formularza lub preferencji czcionki. Użytkownicy mogą zmieniać tych wartości w czasie wykonywania.

Typ ustawienia można zmienić za pomocą **zakres** właściwości.

System projektu przechowuje ustawienia aplikacji w dwóch plikach XML:

- *app.config* pliku, który jest tworzony w czasie projektowania, podczas tworzenia pierwsze ustawienie aplikacji

- *user.config* pliku, który jest tworzony w czasie wykonywania, gdy użytkownik uruchomi aplikację zmienia wartość każdego ustawienia użytkownika.

Należy zauważyć, że zmiany w ustawieniach użytkownika nie są zapisywane na dysku, chyba że aplikacja specjalnie wywołuje metodę, aby to zrobić.

## <a name="create-application-settings-at-design-time"></a>Utwórz ustawienia aplikacji w czasie projektowania

Ustawienia aplikacji w czasie projektowania, można utworzyć na dwa sposoby: za pomocą **ustawienia** strony **projektanta projektu**, lub za pomocą **właściwości** okna formularza lub formant, dzięki czemu można powiązać ustawienie właściwości.

Podczas tworzenia ustawienia zakresu aplikacji (na przykład parametry połączenia bazy danych lub odwołania do zasobów serwera), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapisuje go w *app.config* z `<applicationSettings>` tagu. (Parametry połączenia są zapisywane w obszarze `<connectionStrings>` tagu.)

Podczas tworzenia ustawienia zakresu użytkownika (na przykład domyślną czcionkę, strony głównej lub rozmiaru okna), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapisuje go w *app.config* z `<userSettings>` tagu.

> [!IMPORTANT]
> Parametry połączenia w przypadku zapisania *app.config*, należy podjąć środki ostrożności, aby uniknąć ujawniania poufne informacje, takie jak hasła lub ścieżki serwera w parametrach połączenia.
>
> Jeśli skorzystasz z ciągu połączenia ze źródła zewnętrznego, takich jak użytkownika, podając identyfikator użytkownika i hasło, należy zachować ostrożność do upewnij się, że wartości, które można użyć do utworzenia połączenia ciąg zawiera dodatkowych ciąg parametrów połączenia Spowoduje to zachowanie połączenia.
>
> Rozważ użycie funkcji chronione konfiguracji do szyfrowania poufnych informacji w pliku konfiguracji. Aby uzyskać więcej informacji, zobacz [chronić informacje o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Ponieważ nie istnieje żaden model pliku konfiguracji dla bibliotek klas, ustawienia aplikacji nie są stosowane dla projektów biblioteki klas. Wyjątek stanowi Visual Studio Tools dla pakietu Office DLL projektu, który może mieć plik konfiguracji.

## <a name="use-customized-settings-files"></a>Użyj ustawień niestandardowych, pliki

Możesz dodać pliki dostosowanych ustawień do projektu wygodny zarządzania grupami ustawień. Ustawienia, które znajdują się w jednym pliku są ładowane i zapisywane jako jednostki. Zapisanie ustawień w oddzielnych plików dla często używane i rzadko używane grup, można zaoszczędzić czas ładowania i zapisywania ustawień.

Na przykład, takich jak można dodać pliku *SpecialSettings.settings* do projektu. Podczas Twojego `SpecialSettings` klasy nie jest widoczna w `My` przestrzeni nazw, **kod widoku** można odczytać pliku ustawień niestandardowych, który zawiera `Partial Class SpecialSettings`.

**Projektanta ustawień** najpierw szuka *Settings.settings* plik, który tworzy system projektu; ten plik jest domyślnie plik, który **projektanta projektu** Wyświetla w **ustawienia** kartę. *Settings.Settings* znajduje się w *mój projekt* folder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów i *właściwości* folder [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów. **Projektanta projektu** wyszukuje inne ustawienia plików w folderze głównym projektu. W związku z tym należy umieścić plik ustawień niestandardowych. Jeśli dodasz *.settings* pliku w innym miejscu w projekcie, **projektanta projektu** nie będzie mógł go zlokalizować.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Dostępu lub zmień ustawienia aplikacji w czasie wykonywania w języku Visual Basic

W projektach Visual Basic, mogą korzystać ustawienia aplikacji w czasie wykonywania za pomocą `My.Settings` obiektu. Na **ustawienia** kliknij przycisk **wyświetlić kod** przycisk, aby wyświetlić *Settings.vb* pliku. *Settings.VB* definiuje `Settings` klasy, która pozwala na obsługę tych zdarzeń w klasie ustawień: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, i <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Zwróć uwagę, że `Settings` klasy w *Settings.vb* jest częściowej klasy, która wyświetla tylko użytkowników kod, nie całego wygenerowanej klasy. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji przy użyciu `My.Settings` obiektów, zobacz [dostęp do ustawień aplikacji (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Wartości ustawienia zakresu użytkownika, które zmiany użytkowników w czasie wykonywania (na przykład pozycję formularza od razu) są przechowywane w *user.config* pliku. Należy zauważyć, że wartości domyślne są nadal zapisywane w *app.config*.

Jeśli ustawienia zakresu użytkownika zostały zmienione w czasie wykonywania, na przykład w przypadku testowania aplikacji i chcesz zresetować te ustawienia do wartości domyślnych, kliknij przycisk **Synchronizuj** przycisku.

Zdecydowanie zaleca się używanie `My.Settings` obiekt i domyślnie *.settings* pliku ustawień dostępu. Jest to spowodowane służy **projektanta ustawień** można przypisać właściwości do ustawienia i, ponadto użytkownika ustawienia są automatycznie zapisywane przed zamykania aplikacji. Jednak aplikacji Visual Basic można uzyskać dostępu do ustawień bezpośrednio. W takim przypadku należy uzyskać dostęp `MySettings` klasy i używać niestandardowej *.settings* w katalogu głównym projektu. Musisz zapisać ustawienia użytkownika przed zakończeniem aplikacji, jak C# aplikacji; jest to opisane w poniższej sekcji.

## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Dostępu lub zmień ustawienia aplikacji w czasie wykonywania w języku C# #

W językach innych niż Visual Basic, takich jak C#, muszą uzyskać dostęp do `Settings` klasy bezpośrednio, jak pokazano w następującym [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] przykład.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Należy jawnie wywołać `Save` metody tej klasy otoki w celu utrzymania ustawień użytkownika. Zwykle to zrobić w `Closing` obsługi zdarzeń formularza głównego. W poniższym przykładzie C# przedstawiono sposób wywołania `Save` metody.

```csharp
Properties.Settings.Default.Save();
```

Aby uzyskać ogólne informacje o uzyskiwaniu dostępu do ustawień aplikacji `Settings` , zobacz [Przegląd ustawień aplikacji (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Informacje o iteracji w ustawieniach, zobacz ten [wpis na forum](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Zobacz także

- [Dostęp do ustawień aplikacji (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
