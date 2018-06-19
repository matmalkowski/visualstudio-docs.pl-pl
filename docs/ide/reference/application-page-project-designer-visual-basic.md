---
title: Strona aplikacji, Projektant projektu (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62cbae6115b8268adbb1e2f9d6c27df8bf94a28b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31954572"
---
# <a name="application-page-project-designer-visual-basic"></a>Strona aplikacji, Projektant projektu (Visual Basic)

Użyj **aplikacji** strony projektanta projektu, aby określić ustawienia aplikacji i właściwości projektu.

Aby uzyskać dostęp do **aplikacji** wybierz węzeł projektu (nie **rozwiązania** węzła) w **Eksploratora rozwiązań**. Następnie wybierz pozycję **projektu** > **właściwości** na pasku menu. Gdy pojawi się w Projektancie projektu, zaznacz **aplikacji** kartę.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Ustawienia ogólne aplikacji

Następujące opcje umożliwiają konfigurowanie ogólnych ustawień dla aplikacji.

### <a name="assembly-name"></a>Nazwa zestawu

Określa nazwę pliku wyjściowego, który będzie zawierał manifest zestawu. Jeśli zmienisz tę właściwość, **nazwy wyjściowego** również zmiany właściwości. Można również określić nazwę pliku wyjściowego z wiersza polecenia, używając [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) przełącznika kompilatora. Aby uzyskać informacje o sposobie programowy dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

### <a name="root-namespace"></a>Główna przestrzeń nazw

Określa podstawowej przestrzeni nazw dla wszystkich plików w projekcie. Na przykład jeśli ustawisz **Namespace głównego** do `Project1` i masz `Class1` poza przestrzeni nazw w kodzie, będzie jego przestrzeni nazw `Project1.Class1`. Jeśli masz `Class2` w przestrzeni nazw `Order` w kodzie, będzie jego przestrzeni nazw `Project1.Order.Class2`.

Jeśli wyczyścisz **Namespace głównego**, można określić strukturę przestrzeń nazw projektu w kodzie.

> [!NOTE]
> Jeśli używasz Global — słowo kluczowe w [instrukcji Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement), można zdefiniować przestrzeni nazw poza głównej przestrzeni nazw projektu. Jeśli wyczyścisz **Namespace głównego**, `Global` staje się najwyższego poziomu przestrzeni nazw, co eliminuje potrzebę `Global` — słowo kluczowe w `Namespace` instrukcji. Aby uzyskać więcej informacji, zobacz "Globalne — słowo kluczowe w Namespace instrukcje" w [przestrzeni nazw w Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Aby uzyskać informacje o sposobie tworzenia przestrzeni nazw w kodzie, zobacz [instrukcji Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Aby uzyskać więcej informacji o katalogu głównego przestrzeni nazw właściwości, zobacz [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Aby uzyskać informacje o sposobie programowy dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

### <a name="target-framework-all-configurations"></a>Platforma docelowa (wszystkie konfiguracje)

Określa wersję systemu .NET Framework który celów aplikacji. Ta opcja może mieć różne wartości w zależności od wersji programu .NET Framework są zainstalowane na tym komputerze.

Wartością domyślną jest zgodna platformie docelowej określonej w **nowy projekt** okno dialogowe.

> [!NOTE]
> Wstępnie wymagane pakiety, które są wymienione w [wstępnie wymagane składniki — okno dialogowe](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie po otwarciu okna dialogowego po raz pierwszy. Jeśli użytkownik zmieni platformy docelowej projektu, należy określić wymagania wstępne ręcznie, aby dopasować nowej platformy docelowej.

Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) i [programu Visual Studio omówienie Wielowersyjności](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Typ aplikacji

Określa typ aplikacji do skompilowania. Można określić dla aplikacji Windows 8.x, **aplikacji ze Sklepu Windows**, **biblioteki klas**, lub **pliku WinMD**. W przypadku większości innych typów aplikacji, można określić **aplikacji systemu Windows**, **aplikacji konsoli**, **biblioteki klas**, **usługi systemu Windows**, lub **sieci Web biblioteki formantu**.

Dla projektu aplikacji sieci web, należy określić **biblioteki klas**.

Jeśli określisz **pliku WinMD** opcji typów może zostać przedstawione w dowolnym języku programowania środowiska wykonawczego systemu Windows. Przez opakowanie wyjściowy projektu jako plik WinMD, kod aplikacji w wielu językach i kod współdziałać tak, jakby zostało napisane w języku. Można użyć **pliku WinMD** opcji rozwiązania, które odnoszą się do bibliotek środowiska uruchomieniowego systemu Windows, w tym [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

> [!NOTE]
> Środowisko wykonawcze systemu Windows można typy projektów, aby były wyświetlane jako obiektów macierzystych w niezależnie od języka używa ich. Na przykład aplikacji JavaScript, które współdziałają z środowiska wykonawczego systemu Windows używać go jako zestaw obiektów JavaScript i korzystanie z aplikacji C# biblioteki jako kolekcję obiektów platformy .NET. Przez tworzenie pakietów wyjściowych projektu jako plik WinMD, można skorzystać z tej samej technologii, która używa środowiska wykonawczego systemu Windows.

Aby uzyskać więcej informacji na temat **typu aplikacji** właściwości, zobacz [/TARGET (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Aby uzyskać informacje o sposobie programowy dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.OutputType%2A>.

### <a name="icon"></a>Ikona

Ustawia plik ICO jako ikonę programu. Wybierz  **\<Przeglądaj >** aby wyszukać istniejącej grafiki. Zobacz [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (lub [/win32icon (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)) Aby uzyskać więcej informacji. Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

### <a name="startup-form--startup-object--startup-uri"></a>Formularz startowy / obiekt uruchomieniowy / URI uruchamiania

Określa punkt formularza lub wpis uruchomienia aplikacji.

Jeśli **struktury aplikacji Włącz** wybrano (ustawienie domyślne), ta lista jest zatytułowany **formularz startowy** i pokazuje tylko formularze ponieważ struktury aplikacji obsługuje tylko uruchamiania formularzy nie obiektów.

Jeśli projekt jest aplikacją przeglądarki WPF, ta lista jest zatytułowany **URI uruchamiania**, a wartość domyślna to **Page1.xaml**. **URI uruchamiania** listy umożliwia określenie zasobu interfejsu użytkownika (a XAML element) aplikacji jest wyświetlany podczas uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Application.StartupUri%2A>.

Jeśli **struktury aplikacji Włącz** jest wyczyszczone, ta lista staje się **obiekt uruchomieniowy** i przedstawia formularzy i klasy lub moduły z `Sub Main`.

**Obiekt uruchomieniowy** określa punkt wejścia ma być wywoływana podczas ładowania aplikacji. Ogólnie rzecz biorąc to jest ustawiona jako główne formularza w aplikacji lub do `Sub Main` procedury, która powinna być uruchamiana podczas uruchamiania aplikacji. Ponieważ nie ma punktu wejścia biblioteki klas, ich jedyną opcją dla tej właściwości jest **(Brak)**. Aby uzyskać więcej informacji, zobacz [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

### <a name="assembly-information"></a>Informacje o zestawie

Kliknij ten przycisk, aby wyświetlić [informacji o zestawie — okno dialogowe](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Włącz platformę aplikacji

Określa, czy projekt będzie używać struktury aplikacji. Ustawienie tej opcji ma wpływ na opcje dostępne w **formularz startowy**/**obiekt uruchomieniowy**.

Jeśli to pole wyboru jest zaznaczone, aplikacja korzysta ze standardu `Sub Main`. Po zaznaczeniu tego pola wyboru włącza funkcje **właściwości platformy aplikacji systemu Windows** sekcji, a także wymaga wybrania formularz startowy.

Jeśli to pole wyboru jest wyczyszczone, aplikacja używa niestandardowego `Sub Main` określonej w **formularz startowy**. W takim przypadku można określić obiektu uruchamiania (niestandardowego `Sub Main` w metodzie lub klasie) lub formularz. Ponadto opcje w **właściwości platformy aplikacji systemu Windows** sekcji staną się niedostępne.

### <a name="view-windows-settings"></a>Wyświetl ustawienia systemu Windows

Kliknij ten przycisk, aby wygenerować i otworzyć pliku app.manifest. Visual Studio wykorzystuje ten plik do generowania manifestu danych aplikacji. A następnie ustaw kontroli konta użytkownika żądany poziom wykonywania, modyfikując `<requestedExecutionLevel>` tagów w app.manifest w następujący sposób:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce współpracuje z poziomu `asInvoker` lub w trybie zwirtualizowanych (nie manifestu Generowanie). Aby określić zwirtualizowanych tryb, usuń cały tag z app.manifest.

Aby uzyskać więcej informacji o tworzeniu manifestu, zobacz [wdrażania ClickOnce w systemie Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Właściwości platformy aplikacji systemu Windows

Następujące ustawienia są dostępne w **właściwości platformy aplikacji systemu Windows** sekcji. Te opcje są dostępne tylko wtedy, gdy **struktury aplikacji Włącz** pole wyboru jest zaznaczone. Po tej sekcji opisano **właściwości platformy aplikacji systemu Windows** ustawienia dla aplikacji Windows Presentation Foundation (WPF).

### <a name="enable-xp-visual-styles"></a>Włącz style wizualne XP

Włącza lub wyłącza style wizualne systemu Windows XP, znanej także jako *kompozycji systemu Windows XP*. Style wizualne Windows XP włączyć, na przykład formantów dynamicznych kolorów i zaokrąglone narożniki. Domyślnie włączone.

### <a name="make-single-instance-application"></a>Aplikacja pojedynczego wystąpienia

Zaznacz to pole wyboru, aby uniemożliwić użytkownikom uruchamianie wielu wystąpień aplikacji. Domyślnym ustawieniem jest to pole wyboru *wyczyszczone*, dzięki czemu wiele wystąpień aplikacji do uruchomienia. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> zdarzeń.

### <a name="save-mysettings-on-shutdown"></a>Zapisz My.Settings przy zamknięciu

Zaznacz to pole wyboru, aby określić, że aplikacja `My.Settings` ustawienia są zapisywane, gdy użytkownicy wyłączają komputery. Ustawieniem domyślnym jest włączone. Jeśli ta opcja jest wyłączona, możesz zapisać ustawienia aplikacji ręcznie przez wywołanie metody `My.Settings.Save`.

### <a name="authentication-mode"></a>Tryb uwierzytelniania

Wybierz **Windows** (ustawienie domyślne) aby określić używanie uwierzytelniania systemu Windows, aby zidentyfikować aktualnie zalogowanego użytkownika. Te informacje w czasie wykonywania można pobrać za pomocą `My.User` obiektu. Wybierz **zdefiniowanym przez aplikację** Jeśli należy udostępnić własny kod do uwierzytelniania użytkowników zamiast domyślnych metod uwierzytelniania systemu Windows.

### <a name="shutdown-mode"></a>Tryb zamykania

Wybierz **gdy zamknie się formularz startowy** (ustawienie domyślne), aby określić, że zamyka aplikację, gdy formularz jest ustawiona jako formularz startowy, nawet jeśli inne formy są otwarte. Wybierz **podczas ostatniego formularz zostanie zamknięty** do określenia, gdy zostanie zamknięty ostatni formularz lub zakończyć działanie aplikacji `My.Application.Exit` lub `End` jest nazwana jawnie.

Wybierz **podczas zamykania jawne** do określenia, że aplikacja wyjść, gdy jawnie wywołać `Shutdown`.

Wybierz **na ostatnie okno Zamknij** do określenia, czy po zamknięciu ostatniego okna lub gdy jawnie wywołać zakończyć działanie aplikacji `Shutdown`. To jest ustawienie domyślne.

Wybierz **w głównym oknie, zamknąć** do określenia, czy aplikacja zakończyć po zamknięciu okna głównego lub gdy jawnie wywołać `Shutdown`.

### <a name="splash-screen"></a>Ekran powitalny

Wybierz formularz, który ma być używany jako ekran powitalny. Należy wcześniej utworzono ekran powitalny za pomocą formularza lub szablonu. Wartość domyślna to **(Brak)**.

### <a name="view-application-events"></a>Wyświetl zdarzenia aplikacji

Kliknij ten przycisk, aby wyświetlić pliku kodu zdarzeń, w którym można zapisać zdarzeń dla zdarzeń aplikacji w ramach `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` i `NetworkAvailabilityChanged`. Możesz też przesłonić metody framework niektórych aplikacji. Na przykład, aby zmienić zachowanie wyświetlania ekranu powitalnego przez zastąpienie `OnInitialize`.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Właściwości platformy aplikacji systemu Windows dla systemu Windows Presentation Foundation (WPF) aplikacji

Następujące ustawienia są dostępne w **właściwości platformy aplikacji systemu Windows** sekcji, gdy projekt jest aplikacją Windows Presentation Foundation. Te opcje są dostępne tylko wtedy, gdy **struktury aplikacji Włącz** pole wyboru jest zaznaczone. Opcje wymienione w poniższej tabeli są dostępne tylko w przypadku aplikacji WPF lub aplikacji w przeglądarce WPF. Nie są one dostępne dla bibliotek formanty użytkownika WPF lub formant niestandardowy.

### <a name="shutdown-mode"></a>Tryb zamykania

Ta właściwość ma zastosowanie tylko do aplikacji Windows Presentation Foundation.

Wybierz **podczas zamykania jawne** do określenia, że aplikacja wyjść, gdy jawnie wywołać <xref:System.Windows.Application.Shutdown%2A>.

Wybierz **na ostatnie okno Zamknij** do określenia, czy po zamknięciu ostatniego okna lub gdy jawnie wywołać zakończyć działanie aplikacji <xref:System.Windows.Application.Shutdown%2A>. To jest ustawienie domyślne.

Wybierz **w głównym oknie, zamknąć** do określenia, czy aplikacja zakończyć po zamknięciu okna głównego lub gdy jawnie wywołać <xref:System.Windows.Application.Shutdown%2A>.

Aby uzyskać więcej informacji na temat używania tego ustawienia Zobacz <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>Edytowanie języka XAML

Kliknij ten przycisk, aby otworzyć i modyfikowania pliku definicji aplikacji (Application.xaml) w edytorze XAML. Po kliknięciu tego przycisku Application.xaml otwiera się w węźle definicji aplikacji. Należy edytować ten plik do wykonywania określonych zadań, takich jak definiowanie zasobów. Jeśli plik definicji aplikacji nie istnieje, Projektant projektu tworzy jeden.

### <a name="view-application-events"></a>Wyświetl zdarzenia aplikacji

Kliknij ten przycisk, aby wyświetlić `Application` pliku klasy częściowe (Application.xaml.vb) w edytorze kodu. Jeśli plik nie istnieje, Projektant projektu tworzy z odpowiednią nazwę klasy i przestrzeni nazw.

<xref:System.Windows.Application> Obiektu informuje o zdarzeniach, gdy występują pewne zmiany stanu aplikacji (na przykład do uruchamiania aplikacji lub zamknięcie). Aby uzyskać pełną listę zdarzeń, które udostępnia tę klasę, zobacz <xref:System.Windows.Application>. Zdarzenia te są obsługiwane w sekcji kodu użytkownika `Application` klasy częściowej.