---
title: Strony właściwości, JavaScript
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5690abe8e155c33d8e998ea0a18749e172da7e34
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949504"
---
# <a name="property-pages-javascript"></a>Strony właściwości, JavaScript
**Strony właściwości**zapewnia dostęp do ustawień projektu. Można użyć stron, które są widoczne w **strony właściwości** można zmienić właściwości projektu.

Aby uzyskać dostęp do właściwości projektu, wybierz węzeł projektu w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Następujące strony i opcje są wyświetlane w **strony właściwości**.

## <a name="configuration-and-platform-page"></a>Strona platformy i konfiguracji
 Użyj poniższych opcji, aby wybrać configuration i platform, aby wyświetlić lub zmodyfikować.

 **Konfiguracja**

 Określa ustawienia konfiguracji, aby wyświetlić lub zmodyfikować. Ustawienia są **debugowania** (ustawienie domyślne), **wersji**, **wszystkie konfiguracje**, lub konfiguracji zdefiniowanej przez użytkownika. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie debugowania i wydania konfiguracji w programie Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

 **Platformy**

 Określa ustawienia platformy, aby wyświetlić lub zmodyfikować. Ustawienia są **Any CPU** (domyślne dla [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikacji), **x64**, **ARM**, **x86**, lub platformę zdefiniowane przez użytkownika. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie debugowania i wydania konfiguracji w programie Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

## <a name="general-page"></a>Strona Ogólne
 Użyj poniższych opcji można ustawić właściwości ogólne projektu.

> [!NOTE]
> Niektóre opcje są dostępne tylko w aplikacjach platformy uniwersalnej systemu Windows.


 **Ścieżka danych wyjściowych**

 Określa lokalizację plików wyjściowych dla konfiguracji projektu. Ścieżka jest względna; Po wprowadzeniu ścieżką bezwzględną ścieżkę bezwzględną jest zapisywany w projekcie. Domyślna ścieżka to bin\Debug.

 Korzystając z konfiguracji kompilacji uproszczony, system projektu określa, czy do kompilacji debugowania lub wersji. Po kliknięciu **debugowania**, **Rozpocznij debugowanie** (lub naciśnij klawisz F5) kompilacji jest umieszczany w lokalizacji debugowania, niezależnie od tego **ścieżka wyjściowa** określisz. Jednak **Kompiluj rozwiązanie** na **kompilacji** menu umieszcza je w lokalizacji użytkownika. Aby włączyć zaawansowane konfiguracje kompilacji, na pasku menu wybierz **narzędzia**, **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, wybierz pozycję **ogólne**, a następnie wyczyść **Pokaż zaawansowane konfiguracjekompilacji**pole wyboru. Umożliwia ręcznej kontroli nad wszystkie wartości konfiguracji i czy jest zbudowany wersji debugowanie czy wydanie.

 **Język domyślny**

 Określa język domyślny dla projektu. Opcji języka w **zegar, język i Region** Określa preferowany język użytkownika, w Panelu sterowania. Określając język domyślny dla projektu, należy upewnić się, wykorzystanie zasobów języka określoną wartość domyślną preferowany język użytkownika jest niezgodna z zasobów językowych dostępnych w aplikacji.

## <a name="debug-page"></a>Strona debugowania
 Użyj poniższych opcji, aby ustawić właściwości do debugowania zachowanie w projekcie.

> [!NOTE]
> Niektóre opcje są dostępne tylko w aplikacjach platformy uniwersalnej systemu Windows.


 **Debuger do uruchomienia**

 Określa domyślnego hosta dla debugera.

-   Wybierz **komputera lokalnego** do uruchomienia aplikacji na komputerze hosta programu Visual Studio. Aby uzyskać więcej informacji, zobacz [uruchamianie aplikacji na komputerze lokalnym](../../debugger/run-windows-store-apps-on-the-local-machine.md).

-   Wybierz **symulatora** uruchomić aplikację w symulatorze. Aby uzyskać więcej informacji, zobacz [uruchamianie aplikacji w symulatorze](../../debugger/run-windows-store-apps-in-the-simulator.md).

-   Wybierz **maszyny zdalnej** do uruchomienia aplikacji na komputerze zdalnym. Aby uzyskać więcej informacji na temat debugowania zdalnego, zobacz [uruchamianie aplikacji na komputerze zdalnym](../../debugger/run-windows-store-apps-on-a-remote-machine.md).

**Uruchamianie aplikacji**

Określa, czy można uruchomić aplikacji, naciśnij klawisz F5 lub kliknij przycisk **debugowania**, **Rozpocznij debugowanie**. Wybierz **tak** do uruchamiania aplikacji; w przeciwnym razie wybierz **nr**. W przypadku wybrania **nr**, nadal można debugowania aplikacji, jeśli używasz innej metody ją uruchomić.

**Typ debugera**

Określa typy kodu do debugowania. Wybierz **tylko skrypt** do debugowania kodu JavaScript. Wybierz **zarządzane tylko** do debugowania kodu, który jest zarządzany przez środowisko uruchomieniowe języka wspólnego. Wybierz **tylko kod natywny** do debugowania kodu C++. Wybierz **natywny ze skryptem** do debugowania z C++ i JavaScript. Wybierz **Mixed (zarządzanego i natywnego)** do debugowania zarządzanego i kodu C++.

**Zezwalaj na sprzężenie zwrotne sieci lokalnej**

Określa, czy do testowania aplikacji jest dozwolony dostęp do adresu IP sprzężenia zwrotnego. Wybierz **tak** aby umożliwić użycie adres sprzężenia zwrotnego w przypadku aplikacji klienckiej na tym samym komputerze, gdzie aplikacja serwera jest uruchomiona, a w przeciwnym, zaznacz **nr**. Ta właściwość jest dostępna tylko wtedy, gdy **debugera do uruchamiania** właściwość jest ustawiona na **maszyny zdalnej**.

**Nazwa komputera**

Określa nazwę komputera zdalnego, host debugera. Ta właściwość jest dostępna tylko wtedy, gdy **debugera do uruchamiania** ustawiono **maszyny zdalnej**.

**Wymagaj uwierzytelniania**

Określa, czy komputer zdalny wymaga uwierzytelniania. Ta właściwość jest dostępna tylko wtedy, gdy **debugera do uruchamiania** ustawiono **maszyny zdalnej**.
