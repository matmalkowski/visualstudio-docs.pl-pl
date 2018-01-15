---
title: "Zarządzanie odwołaniami w projekcie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c941b196897b7d3f7a815c50fc1e0a4817d3ed74
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2018
---
# <a name="managing-references-in-a-project"></a>Zarządzanie odwołaniami w projekcie

Aby pisać kod dla składników zewnętrznych lub połączone usługi, projektu najpierw musi zawierać odwołanie do niej. Odwołanie jest zasadniczo wpis w pliku projektu, który zawiera informacje, że program Visual Studio musi zlokalizować składnik lub usługa.

Aby dodać odwołanie, węzła odwołań w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj odwołanie**. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Dodaj odwołanie w Visual C &43; &#43; ] (../ide/media/vs2015_cpp_add_reference.png "vs2015_cpp_add_reference")

Można wprowadzić odwołania do następujących typów składników i usług:

- Biblioteki klas .NET framework lub zestawów

- Aplikacji platformy uniwersalnej systemu Windows

- COM — Składniki

- Inne zestawy oraz bibliotek klas projektów w tym samym rozwiązaniu

- Usługi sieci Web XML

## <a name="uwp-app-references"></a>Odwołania do aplikacji platformy uniwersalnej systemu Windows

### <a name="project-references"></a>Odwołania do projektu

Uniwersalne projekty platformy systemu Windows (UWP) można utworzyć odwołania do innych projektów uniwersalnych systemu Windows w rozwiązaniu lub Windows 8.1 projektów lub plików binarnych, pod warunkiem, że te projekty nie należy używać interfejsów API, które są przestarzałe w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [przenieść z systemem Windows 8 środowiska wykonawczego platformy uniwersalnej systemu Windows](/windows/uwp/porting/w8x-to-uwp-root).

Jeśli wybierzesz przekierować projekty Windows 8.1 do systemu Windows 10, zobacz [portu, migracji i uaktualniania projektów programu Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Odwołania do zestawu SDK rozszerzenia

Visual Basic, C#, C++ i JavaScript Windows platformy Uniwersalnej aplikacji może się odwoływać rozszerzenia SDK przeznaczonych Windows 8.1, tak długo, jak te rozszerzenia SDK nie należy używać interfejsów API, które są przestarzałe w systemie Windows 10. Sprawdź, czy w witrynie dostawcy zestawu SDK rozszerzenia, aby dowiedzieć się, czy można się odwoływać za aplikacji platformy uniwersalnej systemu Windows.

Jeśli okaże się, że zestawu SDK rozszerzenia przywoływane przez aplikację nie jest obsługiwany, a następnie należy wykonać następujące czynności:

1. Sprawdź nazwę projektu, który powoduje błąd. Platformy, którą Twój projekt jest docelowo jest podana w nawiasach obok nazwy projektu. Na przykład **MyProjectName (Windows 8.1)** oznacza, że projekt **MyProjectName** jest przeznaczonych dla wersji platformy Windows 8.1.

1. Przejdź do witryny dostawcy, który jest właścicielem nieobsługiwany zestawu SDK rozszerzenia, a następnie zainstalować wersję zestawu SDK rozszerzenia z zależnościami, które są zgodne z wersją platformy, którą Twój projekt jest docelowo.

    > [!NOTE]
    > Jednym ze sposobów dowiedzieć się, czy zestawu SDK rozszerzenia ma zależności od innych zestawów SDK rozszerzenia jest przeszukując **Menedżera odwołań**. Uruchom ponownie program Visual Studio, Utwórz nowy projekt aplikacji platformy uniwersalnej systemu Windows C#, a następnie kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj odwołanie**. Przejdź do **Windows** kartę, a następnie **rozszerzenia** karty podrzędnej, a następnie wybierz zestawu SDK rozszerzenia. Szukaj w okienku po prawej stronie w **Menedżera odwołań**. Jeśli zawiera on zależności, zostaną one dostępne.

    > [!IMPORTANT]
    > Jeśli projekt jest docelowo systemu Windows 10 i zestawu SDK rozszerzenia zainstalowane w poprzednim kroku ma zależność na pakietu Microsoft Visual C++ środowiska wykonawczego, wersji programu Microsoft Visual C++ Runtime Package zgodnego z systemem Windows 10 jest 14.0 i jest zainstalowany Program Visual Studio.

1. Jeśli zainstalowany w poprzednim kroku zestawu SDK rozszerzenia ma zależności od innych zestawów SDK rozszerzenia, przejdź do witryny dostawców, którzy należą zależności i zainstalować wersje te zależności, które są zgodne z wersją platformy, którą Twój projekt jest Określanie wartości docelowej.

1. Uruchom ponownie program Visual Studio, a następnie otwórz aplikację.

1. Kliknij prawym przyciskiem myszy **odwołania** węzła w projekcie, który spowodował błąd i wybierz polecenie **Dodaj odwołanie**.

1. Kliknij przycisk **Windows** kartę, a następnie **rozszerzenia** podrzędna, następnie usuń zaznaczenie pól wyboru dla starego rozszerzenia SDK, a następnie sprawdź, czy pola wyboru nowego rozszerzenia SDK. Kliknij przycisk **OK**.

## <a name="adding-a-reference-at-design-time"></a>Dodawanie odwołania w czasie projektowania

Po wprowadzeniu odwołania do zestawu w projekcie programu Visual Studio wyszukuje zestawu w następujących lokalizacjach:

- Bieżący katalog projektu. (Te zestawy można znaleźć przy użyciu **Przeglądaj** kartę.)

- Innych katalogów projektu w tym samym rozwiązaniu. (Te zestawy można znaleźć na **projekty** kartę.)

> [!NOTE]
> Wszystkie projekty zawierają domniemanych odwołanie do biblioteki mscorlib. Projekty Visual Basic zawierają domniemanych odwołanie do `Microsoft.VisualBasic`. Wszystkie projekty zawierają domniemanych odwołanie do `System.Core`, nawet jeśli `System.Core` zostanie usunięty z listy odwołania.

## <a name="references-to-shared-components-at-run-time"></a>Odwołania do składników współużytkowanych w czasie wykonywania

W czasie wykonywania składniki musi być w ścieżce danych wyjściowych projektu lub w globalnej pamięci podręcznej zestawów (GAC). Jeśli projekt zawiera odwołanie do obiektu, który nie znajduje się w jednej z tych lokalizacji, należy skopiować odwołanie do ścieżka danych wyjściowych projektu podczas kompilowania projektu. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> Właściwość wskazuje, czy ta kopia ma zostać wykonane. Jeśli wartość jest **True**, odwołanie jest kopiowany do katalogu projektu podczas kompilowania projektu. Jeśli wartość jest **False**, odwołanie nie zostanie skopiowany.

W przypadku wdrożenia aplikacji, która zawiera odwołanie do niestandardowych składników, która jest zarejestrowana w pamięci GAC, składnik nie zostanie wdrożony z aplikacją, niezależnie od tego <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> ustawienie. We wcześniejszych wersjach programu Visual Studio, można ustawić <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> właściwości odwołania, aby upewnić się, że zestaw został wdrożony. Teraz musisz ręcznie dodać zestaw w folderze \Bin. Spowoduje to umieszczenie wszystkich kodu niestandardowego, w obszarze kontroli, co zmniejsza ryzyko publikowania kodu niestandardowego, z którą nie znasz.

Domyślnie <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> właściwość jest ustawiona na **False** zestawem lub składnikiem znajduje się w globalnej pamięci podręcznej zestawów lub jest on składnikiem framework. W przeciwnym razie wartość jest równa **True**. Odwołania projektu do projektu jest zawsze ustawiona **True**.

## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Odwołanie do projektu lub zestawu, którego celem jest inna wersja programu .NET Framework

Można tworzyć aplikacje, które odwołują się do projektów lub zestawów, które odnoszą się do innej wersji programu .NET Framework. Na przykład można utworzyć aplikacji, którego element docelowy [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)], który odwołuje się do zestawu, którego celem jest [!INCLUDE[dnprdnext](../ide/includes/dnprdnext_md.md)]. Jeśli tworzenie projektu, który jest przeznaczony dla starszej wersji programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], nie można ustawić odwołanie projektu do projektu lub zestawu, którego celem jest nowsza wersja.

Aby uzyskać więcej informacji, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="project-to-project-references"></a>Odwołania do projektu do projektu

Odwołania projektu do projektu są odwołania do projektów, które zawierają zestawy; można je utworzyć za pomocą **projektu** kartę. Program Visual Studio można znaleźć zestawu, w przypadku podania ścieżki do projektu.

Jeśli masz projektu, który spowoduje utworzenie zestawu należy odwołania do projektu i nie używać odwołanie pliku (patrz poniżej). Zaletą odwołanie projektu do projektu jest tworzy zależność między projektami w systemie kompilacji. Zależne projekt zostanie skompilowany, jeśli została zmieniona od czasu ostatniego konstruowania odwołaniem do projektu. Odwołanie pliku nie tworzy zależność kompilacji, dzięki czemu można Skompiluj projekt odwołujący się bez tworzenia projektu zależne i odwołania może stać się nieaktualne. (To znaczy projektu można odwoływać się wcześniej skompilowany wersja projektu.) Może to spowodować różne wersje pojedynczego pliku DLL jest wymagany w katalogu bin, który nie jest możliwe. Gdy wystąpi konflikt, zostanie wyświetlony komunikat o takich jak "Ostrzeżenie: nie można skopiować zależności 'Plik' w projekcie 'projekt' do katalogu uruchomienia, ponieważ zastąpiłaby ona odwołanie 'Plik'.". Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami uszkodzony](../ide/troubleshooting-broken-references.md) i [porady: tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Zamiast odwołania projektu do projektu odwołanie pliku jest tworzony, jeśli wersja docelowej platformy .NET Framework jeden projekt jest wersji 4.5 i wersję docelową innych projektów jest w wersji 2, 3, 3.5 lub 4.0.

## <a name="file-references"></a>Odwołania do pliku

Odwołania do pliku są bezpośrednie odwołania do zestawów poza kontekstem projektu programu Visual Studio. Można je utworzyć za pomocą **Przeglądaj** karcie **Menedżera odwołań**. Użyj odwołania pliku, jeśli masz tylko zestaw lub składnik i nie tworzy go jako dane wyjściowe projektu.

## <a name="see-also"></a>Zobacz także

[Rozwiązywanie problemów z przerwanymi odwołaniami](../ide/troubleshooting-broken-references.md)  
[Instrukcje: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
