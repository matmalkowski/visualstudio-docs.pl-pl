---
title: Strona aplikacji, Projektant projektu (C#) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4ea0e0f38b96f7ba48a8a88ebf41986350fe73f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="application-page-project-designer-c"></a>Strona aplikacji, Projektant projektu (C#)

Użyj **aplikacji** strony **projektanta projektu** Aby określić ustawienia aplikacji i właściwości projektu.  
  
Aby uzyskać dostęp do **aplikacji** wybierz węzeł projektu (nie **rozwiązania** węzła) w **Eksploratora rozwiązań**. Następnie wybierz pozycję **projektu**, **właściwości** na pasku menu. Gdy pojawi się w Projektancie projektu, kliknij przycisk **aplikacji** kartę.  
  
[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="general-application-settings"></a>Ustawienia ogólne aplikacji  
 Następujące opcje umożliwiają konfigurowanie ogólnych ustawień dla aplikacji.  
  
 **Nazwa zestawu**  
 Określa nazwę pliku wyjściowego, który będzie zawierał manifest zestawu. Zmienianie tej właściwości spowoduje również zmianę **nazwy wyjściowego** właściwości. Można wprowadzić tej zmiany z poziomu wiersza polecenia przy użyciu [/out (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **Domyślna przestrzeń nazw**  
 Określa podstawowej przestrzeni nazw dla plików dodane do projektu.  
  
 Zobacz [przestrzeni nazw](/dotnet/csharp/language-reference/keywords/namespace) Aby uzyskać więcej informacji o tworzeniu przestrzeni nazw w kodzie.  
  
 Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Struktura docelowa**  
 Określa wersję systemu .NET Framework który celów aplikacji. Ta opcja może mieć różne wartości w zależności od wersji programu .NET Framework są zainstalowane na tym komputerze.  
  
 Domyślnie wartość jest taka sama jak docelowe środowisko, które wybrano w **nowy projekt** okno dialogowe.  
  
> [!NOTE]
>  Wstępnie wymagane pakiety wymienione w [wstępnie wymagane składniki — okno dialogowe](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli użytkownik zmieni platformy docelowej projektu, konieczne będzie wybierz warunki wstępne ręcznie, aby dopasować nowej platformy docelowej.  
  
 Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) i [programu Visual Studio omówienie Wielowersyjności](../../ide/visual-studio-multi-targeting-overview.md).  
  
 **Typ aplikacji**  
 Określa typ aplikacji do skompilowania. Można określić dla aplikacji Windows 8.x, **aplikacji ze Sklepu Windows**, **biblioteki klas**, lub **pliku WinMD**. W przypadku większości innych typów aplikacji, można określić **aplikacji systemu Windows**, **aplikacji konsoli**, **biblioteki klas**, **usługi systemu Windows**, lub **sieci Web biblioteki formantu**.  
  
 Dla projektu aplikacji sieci web, należy określić **biblioteki klas**.  
  
 Jeśli określisz **pliku WinMD** opcji typów może zostać przedstawione w dowolnym języku programowania środowiska wykonawczego systemu Windows. Przez opakowanie wyjściowy projektu jako plik WinMD, kod aplikacji w wielu językach i kod współdziałać tak, jakby zostało napisane w języku. Można określić tę opcję dla rozwiązania, które odnoszą się do bibliotek środowiska uruchomieniowego systemu Windows, w tym [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
> [!NOTE]
>  Środowisko wykonawcze systemu Windows można typy projektów, aby były wyświetlane jako obiektów macierzystych w niezależnie od języka używa ich. Na przykład aplikacji JavaScript, które współdziałają z środowiska wykonawczego systemu Windows używać go jako zestaw obiektów JavaScript i korzystanie z aplikacji C# biblioteki jako kolekcję obiektów platformy .NET. Przez tworzenie pakietów wyjściowych projektu jako plik WinMD, można skorzystać z tej samej technologii, która używa środowiska wykonawczego systemu Windows.  
  
 Aby uzyskać więcej informacji na temat **typu aplikacji** właściwości, zobacz [/TARGET (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). Aby uzyskać informacje o sposobie programowy dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Informacje o zestawie**  
 Kliknięcie tego przycisku powoduje wyświetlenie [informacji o zestawie — okno dialogowe](../../ide/reference/assembly-information-dialog-box.md).  
  
 **Obiekt początkowy**  
 Określa punkt wejścia ma być wywoływana podczas ładowania aplikacji. Zwykle ta opcja jest ustawiona na formularzu głównym aplikacji lub do `Main` procedury, która powinna być uruchamiana podczas uruchamiania aplikacji. Ponieważ nie ma punktu wejścia biblioteki klas, ich jedyną opcją dla tej właściwości jest **(nie ustawiono)**.  
  
 Domyślnie w projekcie aplikacji przeglądarki WPF, ta opcja jest **(nie ustawiono)**. Druga opcja to *Projectname*. App. Dla tego typu projektu należy ustawić początkową identyfikator URI do ładowania zasobów interfejsu użytkownika podczas uruchamiania aplikacji. Aby to zrobić, otwórz plik Application.xaml projektu i ustawić `StartupUri` właściwość w pliku .xaml w projekcie, takie jak Window1.xaml. Listę elementów głównych dopuszczalne, zobacz <xref:System.Windows.Application.StartupUri%2A>. Należy również zdefiniować `public static void Main()` metodę w klasie w projekcie. Ta klasa będą wyświetlane w **obiekt uruchomieniowy** listy jako *ProjectName.ClassName*. Następnie możesz wybrać klasę jako obiekt początkowy.  
  
 Zobacz [/main (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) Aby uzyskać więcej informacji. Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
## <a name="resources"></a>Zasoby  
 Następujące opcje umożliwiają konfigurowanie ogólnych ustawień dla aplikacji.  
  
 **Ikony, jak i manifestu**  
 Domyślnie ten przycisk radiowy zostanie wybrany i **ikona** i **manifestu** opcje są włączone. Dzięki temu możesz wybrać własne ikonę lub wybrać opcje inne generowanie manifestu. Pozostaw ten przycisk radiowy zaznaczone, chyba że udostępniasz plik zasobów dla projektu.  
  
 **Ikona**  
 Ustawia plik ICO jako ikonę programu. Kliknij przycisk wielokropka, aby wyszukać istniejącej grafiki, lub wpisz nazwę pliku, który ma. Zobacz [/win32icon (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) Aby uzyskać więcej informacji. Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Manifest**  
 Wybiera opcję generowania manifestu, po uruchomieniu aplikacji w systemie Windows Vista w ramach kontroli konta użytkownika (UAC). Ta opcja może mieć następujące wartości:  
  
-   **Osadź manifest z ustawieniami domyślnymi**. Obsługuje typowy sposób, w którym działa program Visual Studio w systemie Windows Vista, która jest osadzanie informacji o zabezpieczeniach w pliku wykonywalnego aplikacji, określając, że `requestedExecutionLevel` można `AsInvoker`. Jest to opcja domyślna.  
  
-   **Utwórz aplikację bez manifestu**. Ta metoda jest znany jako *wirtualizacji*. Użyj tej opcji, zgodność ze starszymi aplikacjami.  
  
-   **Properties\app.manifest**. Ta opcja jest wymagana w przypadku aplikacji wdrażanych przez ClickOnce lub bez rejestracji modelu COM. Jeśli spróbujesz opublikować aplikację przy użyciu wdrażania ClickOnce **manifestu** jest automatycznie ustawiana opcja.  
  
**Plik zasobów**  
Wybierz ten przycisk radiowy, jeśli udostępniasz plik zasobów dla projektu. Wybranie tej opcji wyłącza **ikona** i **manifestu** opcje.  
  
Wprowadź nazwę ścieżki lub użyj przycisku Przeglądaj (**...** ) można dodać plik zasobów Win32 do projektu.