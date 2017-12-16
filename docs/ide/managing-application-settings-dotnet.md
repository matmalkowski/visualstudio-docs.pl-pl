---
title: "Zarządzanie ustawieniami aplikacji (.NET) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msvse_settingsdesigner.err.nameblank
helpviewer_keywords: application settings [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8a36cb7e8f395c177c155e457640b9cb98ae32e7
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="managing-application-settings-net"></a>Zarządzanie ustawieniami aplikacji (.NET)

Ustawienia aplikacji pozwalają dynamicznie przechowywać informacje o aplikacji. Ustawienia umożliwiają przechowywanie danych na komputerze klienckim, który nie powinny znajdować się w kodzie aplikacji (na przykład parametry połączenia), preferencje użytkownika i inne informacje, które są potrzebne w czasie wykonywania.

Ustawienia aplikacji zastąpienie właściwości dynamicznych, używany w starszych wersjach programu Visual Studio.

Każde ustawienie aplikacji musi mieć unikatową nazwę. Nazwa może zawierać dowolną kombinację litery, cyfry i podkreślenia, że nie rozpoczyna się od numeru i nie może zawierać spacji. Nazwę można zmienić, modyfikując `Name` właściwości.

Ustawienia aplikacji mogą być przechowywane jako dowolny typ danych, które można serializować do pliku XML lub ma `TypeConverter` implementującej `ToString` / `FromString`. Najbardziej typowych są `String`, `Integer`, i `Boolean`, ale można również przechowywać wartości jako <xref:System.Drawing.Color>, <xref:System.Object>, lub w postaci ciągu połączenia.

Ustawienia aplikacji także zawierać wartość. Ma wartość **wartość** właściwości musi być zgodny z typem danych ustawienie.

Ponadto ustawienia aplikacji może być powiązana z właściwością formularza lub kontrolki, w czasie projektowania.

Istnieją dwa typy ustawień aplikacji, w oparciu o zakresie:

- Informacje takie jak adres URL usługi sieci Web lub parametry połączenia bazy danych można użyć ustawień zakresu aplikacji. Te wartości są skojarzone z aplikacją. W związku z tym użytkownicy nie mogą zmieniać ich w czasie wykonywania.

- Ustawień z zakresu użytkownika można uzyskać informacje, takie jak utrwalanie ostatniej pozycji formularza lub preferencji czcionki. Użytkownicy mogą zmieniać tych wartości w czasie wykonywania.

Typ ustawienia można zmienić za pomocą **zakres** właściwości.

System projektu przechowuje ustawienia aplikacji w dwóch plikach XML:

- Plik app.config, który jest tworzony w czasie projektowania, podczas tworzenia pierwsze ustawienie aplikacji

- plik user.config, który jest tworzony w czasie wykonywania, gdy użytkownik uruchomi aplikację zmienia wartość każdego ustawienia użytkownika.

Należy zauważyć, że zmiany w ustawieniach użytkownika nie są zapisywane na dysku, chyba że aplikacja specjalnie wywołuje metodę, aby to zrobić.

## <a name="creating-application-settings-at-design-time"></a>Tworzenie ustawień aplikacji w czasie projektowania

Ustawienia aplikacji w czasie projektowania, można utworzyć na dwa sposoby: za pomocą **ustawienia** strony **projektanta projektu**, lub za pomocą **właściwości** okna formularza lub formant, dzięki czemu można powiązać ustawienie właściwości.

Podczas tworzenia ustawienia zakresu aplikacji (na przykład parametry połączenia bazy danych lub odwołania do zasobów serwera), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapisuje go w pliku app.config z `<applicationSettings>` tagu. (Parametry połączenia są zapisywane w obszarze `<connectionStrings>` tagu.)

Podczas tworzenia ustawienia zakresu użytkownika (na przykład domyślną czcionkę, strony głównej lub rozmiaru okna), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapisuje go w pliku app.config z `<userSettings>` tagu.

> [!IMPORTANT]
> Parametry połączenia są przechowywane w pliku app.config, należy podjąć środki ostrożności, aby uniknąć ujawniania poufne informacje, takie jak hasła lub ścieżki serwera w parametrach połączenia.
>
> Jeśli skorzystasz z ciągu połączenia ze źródła zewnętrznego, takich jak użytkownika, podając identyfikator użytkownika i hasło, należy zachować ostrożność do upewnij się, że wartości, które można użyć do utworzenia połączenia ciąg zawiera dodatkowych ciąg parametrów połączenia Spowoduje to zachowanie połączenia.
>
> Rozważ użycie funkcji chronione konfiguracji do szyfrowania poufnych informacji w pliku konfiguracji. Zobacz [ochrony informacji o połączeniu](/dotnet/framework/data/adonet/protecting-connection-information) Aby uzyskać więcej informacji.

> [!NOTE]
> Ponieważ nie istnieje żaden model pliku konfiguracji dla bibliotek klas, ustawienia aplikacji nie są stosowane dla projektów biblioteki klas. Wyjątek stanowi Visual Studio Tools dla pakietu Office DLL projektu, który może mieć plik konfiguracji.

## <a name="using-customized-settings-files"></a>Za pomocą ustawień niestandardowych, pliki

Możesz dodać pliki dostosowanych ustawień do projektu wygodny zarządzania grupami ustawień. Ustawienia, które znajdują się w jednym pliku są ładowane i zapisywane jako jednostki. W związku z tym możliwość ustawienia są przechowywane w oddzielnych plików dla często używanych i rzadko używane grup, można zaoszczędzić czas podczas ładowania i zapisywania ustawień.

Na przykład można dodać pliku, takie jak SpecialSettings.settings do projektu. Podczas Twojego `SpecialSettings` klasy nie jest widoczna w `My` przestrzeni nazw, **kod widoku** można odczytać pliku ustawień niestandardowych, który zawiera `Partial Class SpecialSettings`.

Ustawienia projektanta najpierw szuka pliku Settings.settings, który tworzy system projektu; jest to domyślny plik wyświetlany w Projektancie projektu w **ustawienia** kartę. Settings.Settings znajduje się w folderze Moje projektu dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty w folderze właściwości [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów. Projektant projektu wyszukuje inne ustawienia plików w folderze głównym projektu. W związku z tym należy umieścić plik ustawień niestandardowych. Po dodaniu pliku .settings w innym miejscu w projekcie w Projektancie projektu nie będzie mógł go zlokalizować.

## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Uzyskiwanie dostępu lub zmienianie ustawień aplikacji w czasie wykonywania w języku Visual Basic

W projektach Visual Basic, mogą korzystać ustawienia aplikacji w czasie wykonywania za pomocą `My.Settings` obiektu. Na **ustawienia** kliknij przycisk **wyświetlić kod** przycisk, aby wyświetlić plik Settings.vb. Definiuje Settings.VB `Settings` klasy, która pozwala na obsługę tych zdarzeń w klasie ustawień: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, i <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Zwróć uwagę, że `Settings` klasy w Settings.vb jest częściowej klasy, która wyświetla tylko użytkowników kod, nie całego wygenerowanej klasy. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do ustawień aplikacji przy użyciu `My.Settings` obiektów, zobacz [podczas uzyskiwania dostępu do ustawień aplikacji (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Wartości ustawienia zakresu użytkownika, które użytkownik zmieni się w czasie wykonywania (na przykład pozycję formularza od razu) są przechowywane w pliku user.config. Należy zauważyć, że wartości domyślne nadal są zapisywane w pliku app.config.

Jeśli zmieniono ustawienia zakresu użytkownika w czasie wykonywania, na przykład w przypadku testowania aplikacji i chcesz zresetować te ustawienia do wartości domyślnych, kliknij przycisk **Synchronizuj** przycisku.

Zdecydowanie zaleca się używanie `My.Settings` obiekt i domyślnego pliku .settings ustawień dostępu. To dlatego projektanta ustawień można użyć do przypisania właściwości do ustawienia, a ponadto ustawienia użytkownika są automatycznie zapisywane przed zamykania aplikacji. Jednak aplikacji Visual Basic można uzyskać dostępu do ustawień bezpośrednio. W takim przypadku należy uzyskać dostęp `MySettings` klasy i przy użyciu pliku .settings niestandardowe w katalogu głównym projektu. Należy również Zapisz ustawienia użytkownika przed zakończeniem aplikacji, jak C# aplikacji; jest to opisane w poniższej sekcji.

## <a name="accessing-or-changing-application-settings-at-run-time-in-c"></a>Uzyskiwanie dostępu lub zmienianie ustawień aplikacji w czasie wykonywania w języku C# #

W językach innych niż Visual Basic, takich jak C#, muszą uzyskać dostęp do `Settings` klasy bezpośrednio, jak pokazano w następującym [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] przykład.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Należy również jawnie wywołać `Save` metody tej klasy otoki w celu utrzymania ustawień użytkownika. Zwykle to zrobić w `Closing` obsługi zdarzeń formularza głównego. W poniższym przykładzie C# przedstawiono sposób wywołania `Save` metody.

```csharp
Properties.Settings.Default.Save();
```

Aby uzyskać ogólne informacje o uzyskiwaniu dostępu do ustawień aplikacji `Settings` , zobacz [Przegląd ustawień aplikacji (.NET Frameword)](/dotnet/framework/winforms/advanced/application-settings-overview). Informacje o iteracji w ustawieniach, zobacz ten [wpis na forum](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Zobacz także

[Uzyskiwanie dostępu do ustawień aplikacji (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)