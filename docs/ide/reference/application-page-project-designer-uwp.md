---
title: "Strona właściwości aplikacji dla aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft"
ms.date: 01/23/2018
ms.technology: vs-ide-general
ms.topic: article
f1_keywords: AppPackage.Properties.Application"
helpviewer_keywords: Application page [UWP project]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 34cb125c33ab36a89601c2492d27841bb2ce49d5
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="application-property-page-uwp-projects"></a>Strona właściwości aplikacji (projekty platformy UWP)

Użyj **aplikacji** stronę właściwości, aby określić zestaw projektu Windows platformy Uniwersalnej i informacji pakietu i wersję docelową systemu Windows 10.

![Strona właściwości aplikacji](media/application-page-uwp.png)

Aby uzyskać dostęp do **aplikacji** wybierz węzeł projektu w **Eksploratora rozwiązań**. Następnie wybierz pozycję **projektu** > **właściwości** na pasku menu. Strony właściwości, Otwórz na **aplikacji** kartę.

## <a name="general-section"></a>Sekcja Ogólne

**Nazwa zestawu**&mdash;Określa nazwę pliku wyjściowego, który będzie zawierał manifest zestawu.

Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Domyślny obszar nazw**&mdash;określa podstawowej przestrzeni nazw dla plików dodane do projektu. Aby uzyskać więcej informacji na temat obszarów nazw, zobacz [przestrzenie nazw (C# Podręcznik programowania)](/dotnet/csharp/programming-guide/namespaces/), [przestrzenie nazw (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces), lub [przestrzenie nazw (C++)](/cpp/cpp/namespaces-cpp).

Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Informacje o zestawie**&mdash;wybór ten przycisk otwiera [okno dialogowe Informacje o zestawie](../../ide/reference/assembly-information-dialog-box.md).

**Manifest pakietu**&mdash;wybór ten przycisk otwiera projektanta manifestu. Projektant manifestu możliwy, wybierając _Package.appxmanifest_ w pliku **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [konfiguracji pakietu przy użyciu projektanta manifestu](/windows/uwp/packaging/packaging-uwp-apps#configure-an-app-package).

## <a name="targeting-section"></a>Przeznaczonych dla sekcji

Należy określić wersję docelową i minimalną wersję systemu Windows 10 dla aplikacji, przy użyciu list rozwijanych w tej sekcji. Zaleca się docelowych najnowszej wersji systemu Windows 10 i jeśli tworzysz aplikację przedsiębiorstwa, zbyt obsługuje starsza wersja minimalna. Aby uzyskać więcej informacji o wersji systemu Windows 10 do wyboru, zobacz [wybierz wersję platformy uniwersalnej systemu Windows](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Informacje o platformie elementów docelowych w programie Visual Studio 2017 r, zobacz [obsługiwane platformy](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs#a-iddevelopwindows-avisual-studio-2017-support-for-windows-development).

## <a name="see-also"></a>Zobacz także

[Tworzenie pierwszej aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/get-started/your-first-app)  
[Wybierz wersję platformy uniwersalnej systemu Windows](/windows/uwp/updates-and-versions/choose-a-uwp-version)